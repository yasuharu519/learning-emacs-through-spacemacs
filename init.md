
# init.el

[spacemacs/init.el](https://github.com/syl20bnr/spacemacs/blob/master/init.el)

## 関数

- [defconst](https://github.com/yasuharu519/learning-emacs-through-spacemacs/blob/master/functions.md#defconst)
- [defun](https://github.com/yasuharu519/learning-emacs-through-spacemacs/blob/master/functions.md#defun)
- [version](https://github.com/yasuharu519/learning-emacs-through-spacemacs/blob/master/functions.md#version)
- [require](https://github.com/yasuharu519/learning-emacs-through-spacemacs/blob/master/functions.md#require)

## 変数

- [emacs-version](https://github.com/yasuharu519/learning-emacs-through-spacemacs/blob/master/variables.md#emacs-version)

## 処理の流れ

```elisp
(defconst spacemacs-version          "0.102.2" "Spacemacs version.")
(defconst spacemacs-emacs-min-version   "24.3" "Minimal version of Emacs.")
```

- spacemacsのバージョン定義
- emacsの最低動作バージョンを定義

```elisp
(defun spacemacs/emacs-version-ok ()
  (version<= spacemacs-emacs-min-version emacs-version))
```

- 実行しているEmacsが最低動作バージョンを満たしているか確認


```elisp
(when (spacemacs/emacs-version-ok)
  (load-file (concat user-emacs-directory "core/core-load-paths.el"))
  (require 'core-spacemacs)
  (require 'core-configuration-layer)
  (spacemacs/init)
  (configuration-layer/sync)
  (spacemacs/setup-after-init-hook)
  (spacemacs/maybe-install-dotfile)
  (require 'server)
  (unless (server-running-p) (server-start)))
```

- emacsのバージョンをチェック、条件を満たしていれば `core/core-load-paths.el` をロードパスに追加
- 各種ロード
