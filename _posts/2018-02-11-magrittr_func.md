の代替---
layout: post
title: magrittrの関数たち
tags:
  - R
  - magrittr
---

```magrittr```パイプ演算子以外にも、パイプをつなぐために便利な関数が用意されてます。
それらを調べてみました。

[vignette](https://cran.r-project.org/web/packages/magrittr/magrittr.pdf)をみてみると、以下の関数が用意されています。それぞれの変数は、‘‘で囲まれた演算の代用をすることができます。

| コマンド | 対応する演算子 |
|-----|-----|
| ```extract``` | ‘[‘ |
| ```extract2``` | ‘[[‘ |
| ```inset``` | ‘[<&#8211;‘ |
| ```inset2``` | ‘[[<&#8211;‘ |
| ```use_series``` | ‘$‘ |
| ```add``` | ‘+‘ |
| ```subtract``` | ‘-‘ |
| ```multiply_by``` | ‘*‘ |
| ```raise_to_power``` | ‘^‘ |
| ```multiply_by_matrix``` | ‘%*%‘ |
| ```divide_by``` | ‘/‘ |
| ```divide_by_int``` | ‘%/%‘ |
| ```mod``` | ‘%%‘ |
| ```is_in``` | ‘%in%‘ |
| ```and``` | ‘&‘ |
| ```or``` | ‘&#124;‘ |
| ```equals``` | ‘==‘ |
| ```is_greater_than``` | ‘>‘ |
| ```is_weakly_greater_than``` | ‘>=‘ |
| ```is_less_than``` | ‘<‘ |
| ```is_weakly_less_than``` | ‘<=‘ |
| ```not (‘n’est pas‘)``` | ‘!‘ |
| ```set_colnames``` | ‘colnames<&#8211;‘ |
| ```set_rownames``` | ‘rownames<&#8211;‘ |
| ```set_names``` | ‘names<&#8211;‘ |


<br />
<br />


## 各関数のメモ


***

### データの抽出、代入

 ```extract``` ```extract2```

リストやデータフレームの要素を抽出する。

 ```inset``` ```inset2```

 リストやデータフレームに要素を代入する。

 ```use_series```

 リストやデータフレームから要素をベクトル抽出する。



### 算術演算子

 ```add```

 加算。

 ```subtract```

 減算。

 ```multiply_by```  ```multiply_by_matrix```

 乗算。後者は行列積の演算をする。

 ```raise_to_power```

 べき乗。

 ```divide_by``` ```divide_by_int```

 除算。後者は整数商を返す。

 ```mod```

 剰余演算。


### 比較演算子、論理演算子

 ```is_in```

 要素が含まれるかどうかを判定。

 ```and```　　

 演算子```&```の代替。

 ```or```

 演算子```|```の代替。

 ```equals```

 演算子```=```の代替。

 ```is_greater_than```

 演算子```>```の代替。

 ```is_weakly_greater_than```

 演算子```>=```の代替。

 ```is_less_than```

 演算子```<```の代替。

 ```is_weakly_less_than```

 演算子```<=```の代替。

 ```not```

 演算子```!```の代替。


### 名前の変更

 ```set_colnames```

 列の名前を変更する。

     # データセットの作成
     > df = data.frame(matrix(rnorm(10), nrow=5))
     > df
                X1         X2
     1 -0.45881978  0.1070585
     2  0.17728293 -0.2522486
     3  0.02923236  0.4124346
     4  0.32051567  0.6691685
     5  1.20671981  0.4406586

     > df %>% set_colnames(c('A','B'))
                 A          B
     1 -0.45881978  0.1070585
     2  0.17728293 -0.2522486
     3  0.02923236  0.4124346
     4  0.32051567  0.6691685
     5  1.20671981  0.4406586


 ```set_rownames```

 行の名前を変更する。

     > df %>% set_rownames(c('a','b','c','d','e'))
                X1         X2
     a -0.45881978  0.1070585
     b  0.17728293 -0.2522486
     c  0.02923236  0.4124346
     d  0.32051567  0.6691685
     e  1.20671981  0.4406586

 ```set_names```

 ベクトルの要素名を変更する。

     > df %$% set_names(X1,letters[1:5])
                a          b          c          d          e
      -0.45881978 0.17728293 0.02923236 0.32051567 1.20671981
