
# core-load-paths.el

[spacemacs/core/core-load-paths.el](https://github.com/syl20bnr/spacemacs/blob/master/core/core-load-paths.el)

## 関数
- [add-to-list](https://github.com/yasuharu519/learning-emacs-through-spacemacs/blob/master/functions.md#add-to-list)
- [expand-file-name](https://github.com/yasuharu519/learning-emacs-through-spacemacs/blob/master/functions.md#expand-file-name)
- [unless](https://github.com/yasuharu519/learning-emacs-through-spacemacs/blob/master/functions.md#unless)
- [file-exists-p](https://github.com/yasuharu519/learning-emacs-through-spacemacs/blob/master/functions.md#file-exists-p)
    

## 変数
- [load-path](https://github.com/yasuharu519/learning-emacs-through-spacemacs/blob/master/variables.md#load-path)
- [user-emacs-directory](https://github.com/yasuharu519/learning-emacs-through-spacemacs/blob/master/variables.md#user-emacs-directory)

## 処理

```elisp
(defun add-to-load-path (dir) (add-to-list 'load-path dir))
```

- `load-path`に追加したディレクトリを追加する関数の定義

```elisp
;; paths
(defconst spacemacs-core-directory
  (expand-file-name (concat user-emacs-directory "core/"))
  "Spacemacs core directory.")
(defconst spacemacs-info-directory
  (expand-file-name (concat spacemacs-core-directory "info/"))
  "Spacemacs info files directory")
(defconst spacemacs-release-notes-directory
  (expand-file-name (concat spacemacs-info-directory "release-notes/"))
  "Spacemacs release notes directory")
(defconst spacemacs-banner-directory
  (expand-file-name (concat spacemacs-core-directory "banners/"))
  "Spacemacs banners directory.")
(defconst spacemacs-banner-official-png
  (expand-file-name (concat spacemacs-banner-directory "img/spacemacs.png"))
  "Spacemacs official banner image.")
(defconst spacemacs-directory
  (expand-file-name (concat user-emacs-directory "spacemacs/"))
  "Spacemacs base directory.")
(defconst spacemacs-cache-directory
  (expand-file-name (concat user-emacs-directory ".cache/"))
  "Spacemacs storage area for persistent files")
(defconst user-home-directory
  (expand-file-name "~/")
  "User home directory (~/).")
(defconst pcache-directory
  (concat spacemacs-cache-directory "pcache"))
(unless (file-exists-p spacemacs-cache-directory)
    (make-directory spacemacs-cache-directory))
(defconst user-dropbox-directory
  (expand-file-name (concat user-home-directory "Dropbox/"))
  "Dropbox directory.")

```

- パス等の定義
- キャッシュディレクトリが存在しなければディレクトリを作成

```
;; load paths
(mapc 'add-to-load-path
      `(
        ,(concat user-emacs-directory "core/")
        ,(concat user-emacs-directory "core/libs/")
        ,(concat user-dropbox-directory "emacs/")
        ))
```

- `~/.emacs.d/core/`, `~/.emacs.d/core/libs/`, `~/Dropbox/emacs/`がロードパスに追加される。

