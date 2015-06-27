
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
