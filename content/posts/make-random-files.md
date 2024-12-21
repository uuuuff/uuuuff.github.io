+++
date = '2024-12-21T14:22:33+09:00'
draft = false
title = 'headでランダムな大きさのファイルを作る(linux)'
+++
`head`コマンドでランダムな大きさのファイルを作ってみます。  
`/dev/random`を`head`してその出力をリダイレクトします。  
```
$ head /dev/random > test
```
`ls -l`でファイルサイズを見てみます。  
```
$ ls -l test

-rw-r--r-- 1 user user 1920 Dec 21 14:58 test
```

しかし、大きさは本当にランダムになっているのでしょうか。  
以下のワンライナーを使ってファイルを5つ作ります。  
```
$ for i in {0..4}; do touch test$i && head /dev/random > $_; done
$ ls
test0  test1  test2  test3  test4
```

`ls -l`でファイルサイズを見てみます。  
```
$ ls -l
total 20
-rw-r--r-- 1 user user 2146 Dec 21 14:53 test0
-rw-r--r-- 1 user user 2647 Dec 21 14:53 test1
-rw-r--r-- 1 user user 3757 Dec 21 14:53 test2
-rw-r--r-- 1 user user 2578 Dec 21 14:53 test3
-rw-r--r-- 1 user user 2388 Dec 21 14:53 test4
```
おおよそ、2000~4000バイトくらいのファイルが作らるようですね。  
完全なランダムではありませんが、手頃なサイズのファイルを作ることができそうです。  
