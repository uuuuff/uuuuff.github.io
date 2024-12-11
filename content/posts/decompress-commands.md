+++
date = '2024-12-11T20:51:15+09:00'
draft = false
title = 'Linuxコマンドで tar, xz, zip, gzip, bzip2 形式のファイルの展開する方法'
+++
## はじめに
どれもよくつかうファイル形式ですが、展開方法をよく忘れてしまうのでこの機会にまとめました。  
展開方法のみ書きましたので詳細なつかい方はmanをみてください。
## 目次
- [tar](#tar)
- [xz](#xz)
- [zip](#zip)
- [gzip](#gzip)
- [bzip2](#bzip2)
---

## tar
```
$ tar -xf archive.tar # -f でファイル名 archive.tar を指定し、 -x で展開をする
```

## xz
```
$ xz -d archive.xz  # -d はdecompress(展開の意味)の頭文字
または
$ unxz archive.xz
```
## zip
```
$ unzip archive.zip
```
## gzip
```
$ gzip -d archive.gzip
または
$ gunzip archive.gzip
```
## bzip2
```
$ bzip2 -d archive.bz2
```
