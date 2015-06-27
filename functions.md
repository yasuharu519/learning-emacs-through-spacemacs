
# Functions

elispでの関数について

## defconst

```elisp
(defconst SYMBOL INITVALUE [DOCSTRING])
```

`SYMBOL`を`INITVALUE`で定義

## defun

```elisp
(defun NAME ARGLIST &optional DOCSTRING DECL &rest BODY)
```

`NAME` は関数名。
`(lambda ARGLIST [DOCSTRING] BODY...)` が定義となる。

## version<=

```elisp
(version<= V1 V2)
```

`V1`のほうが`V2`よりもバージョンが小さければ`t`を返す

## require

```elisp
(require FEATURE &optional FILENAME NOERROR)
```

`FEATURE`がまだロードされていなければ`FILENAME`から読み出す。
`FILENAME`が`nil`であれば、`FEATURE`に`.elc`、`.el`を追加したファイルから読み出しを行う。
これについては、`get-load-suffixes`を参照。
`NOERROR`が`nil`でなければ、ファイルが見つからなかったとしても、エラーを出さない。

## add-to-list
```elisp
(add-to-list LIST-VAR ELEMENT &optional APPEND COMPARE-FN)
```

`ELEMENT`が`LIST_VAR`に含まれていない場合追加。
`ELEMENT`が含まれているかどうかのテストは`equal`関数で行われる。
もしくは`COMPARE-FN`が`nil`でない場合はそちらが使用される。
`APPEND`が`nil`でない場合は、末尾に追加、そうでない場合は先頭に追加する。

## expand-file-name

```elisp
(expand-file-name NAME &optional DEFAULT-DIRECTORY)
```

`NAME`で指定されたファイルパスを絶対パスに展開

## concat

```elisp
(concat &rest SEQUENCES)
```

`SEQUENCES`を連結してstringを返す

## unless

```elisp
(unless COND BODY...)
```

`COND`が`nil`であれば、`BODY`を実行し、そうでなければ`nil`を返す。
`BODY`を実行した際は、順に実行され、最後の値が返される。

## file-exists-p

```elisp
(file-exists-p FILENAME)
```

`FILENAME`が存在すれば`t`を返す。
存在しないファイルへのシムリンクであれば`nil`を返す。


## make-directory

```elisp
(make-directory DIR &optional PARENTS)
```

`DIR`のディレクトリを作成。

## mapc

```elisp
(mapc FUNCTION SEQUENCE)
```

`SEQUENCE`の要素に`FUNCTION`を適用させる。
結果の値を返さず、`SEQUENCE`が返される。

