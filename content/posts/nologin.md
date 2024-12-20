+++
date = '2024-12-20T18:50:02+09:00'
draft = false
title = 'Linuxでroot以外のログインを禁止する'
+++
## nologin(5)とは
Linuxでは`/etc/nologin`というファイルを作成することで特権ユーザー以外のログインを禁止することができます。  
nologin(5)のmanページには次のようなことが書かれています。  
> If  the  file  /etc/nologin  exists and is readable, login(1) will allow access only to
> root.  Other users will be shown the contents of this file and their logins will be re‐
> fused.  This provides a simple way of temporarily disabling all unprivileged logins.

要約すると
- `/etc/nologin`が存在し読み取り可能な場合、login(1)はrootのみにアクセスを許可する。
- 他のユーザーは`/etc/nologin`の内容を見ることができ、ログインは拒否される。

つまり、`/etc/nologin`を作成し読み取り権限を付与すればroot以外のログインを禁止できるということです。  

## 実際にやってみた
`/etc/nologin` を作って試してみました。  
以下、やってわかったことのまとめです。  

- 非特権ユーザーを入力するとパスワードプロンプトが表示されるまもなくログイン拒否される。
- `agetty`などで非特権ユーザーの自動ログインを設定しているとログインできてしまう。
- `/etc/nologin`に記述した内容は下のように表示される。  
```
login: user	# ユーザー名入力後、エンター
only root can access this system.	# `/etc/nologin`の内容が出力される
```
- root以外のログインも許可したくなったら`/etc/nologin`を消すだけでOK

## まとめ
ファイルの作成・削除だけで機能するので簡単で良いですね。  
ちなみに、rootのパスワードを設定していない/忘れている 人は本当にログインできなくなってしまうので注意してください。(^_-)
