---
layout: post
title: UNIX入門
tags:
  - UNIX
  -
---
*****
[ここ](https://www.codereading.com/unix-tutorial/)

####UNIXの構成要素
  * カーネル
    * プログラムの時間とメモリを割り当てて、システムコールに応答してファイルストアとの通信を処理する。
  * シェル
    * ユーザーとカーネル間を取り持つインターフェース
    * コマンドインタプリタ
  * ファイルとプロセス
    * ディレクトリ構造の一番上はrootと呼ぶ

*****

####ディレクトリの移動、作成
作業中のディレクトリにある内容を表示
```sh
% ls
```
隠しファイルを表示
```sh
% ls -a
```

ディレクトリの作成
```sh
% mkdir
```

ディレクトリの移動
```sh
% cd
```

カレントディレクトリ(.)
親ディレクトリ(..)

*****
####ホームディレクトリとパス名
パス名を理解する
```sh
% ls unixstuff
```

```sh
% ls unixstuff/backups
```
ホームディレクトリはチルダ(~)で参照可能

*****
####ファイルのコピー、移動、表示、検索
#####file1をfile2にコピー
```sh
% cp file1 file2
% cp /vol/examples/tutorial/science.txt .
```

#####file1をfile2に移動
```sh
% mv file1 file2
```

#####ファイルの内容を表示
```sh
% cat file
```

#####ファイルの内容を１ページずつ表示(qで削除)
```sh
% less file
```

#####ファイルの先頭の１０行を表示
```sh
% head file
% head -5 file
```

#####ファイルの最後の１０行を表示
```sh
% tail file
% tail -15 file
```

#####science.txtから'science'を探す
```sh
% less science.txt
% /science
```

#####grepは、特定の単語、パターンをファイル内から検索
デフォルトは大文字小文字を区別。
  * -i:大文字小文字の区別無し
  * -v:検索に、マッチしない行を表示
  * -n:行番号を表示
  * -c:マッチした行の総数だけを表示
一度に複数のオプションを使える -ivc

```sh
% grep science science.txt
% grep Science science.txt
% grep -i science science.txt
% grep -i 'spining top' science.txt
```

#####文字数を数える
  * -w: 単語数を数える
  * -l: 行数を数える
```sh
% wc file
```

 *****
####標準入出力とリダイレクション、パイプライン
#####リダイレクション
UNIXでは、コマンドの入力と出力をリダイレクト（変える）ことができる
```sh
% cat
apple
banana
[^D]
```

#####標準出力のリダイレクト
```sh
% cat > list1
pear
banana
apple
^D

% cat list1
```

#####ファイルへの追記
```sh
cat >> list1
peach
grape
orange
^D
% cat list1
```

#####list1とlist2を読み取って、biglistにテキストを書き出す。
```sh
% cat list1 list2 > biglist
% cat biglist
```

#####標準入力のリダイレクト

<で、コマンドの入力をリダイレクトできる
sortは一覧をアルファベット順に並べ替える
```sh
% sort
% sort < biglist
% sort < biglist > slist
```

#####パイプライン
このシステムに誰がいる？
```sh
% who
```

#####名前の分類されたリストを得る方法
```sh
% who > names.txt
% sort < names.txt
```

#####whoコマンドの出力をsortコマンドの入力にする方法(|)
```sh
% who | sort
```


####ワイルドカード、ファイル名の規則、マニュアル
＊ワイルドカードは、0個以上の文字列と照合
```sh
% ls list*
% ls *list
```

？ワイルドカードは、１文字だけを照合
```sh
% ls ?list
```

#####ファイル名の規則
特別な記号、スペースを避ける。拡張子を入れる。

#####助けを求める
```sh
% man wc
% whatis wc
```
コマンドを忘れたとき
```sh
% apropos keyword
% apropos copy
```
