# Roam Notes

[Zettelkasten](https://en.wikipedia.org/wiki/Zettelkasten) style notes written in Russian language with [org-roam](https://www.orgroam.com/) mode in [GNU Emacs](https://www.gnu.org/software/emacs/).

License: [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

## How to prepare for working with these notes

* Firstly, you will need **GNU Emacs**. Install it in any way accepted by the operating system you are using.
* Install Emacs packages `org-roam` and `org-roam-ui` using the built-in package manager or the package manager of your operating system.
* Then open the file `~/.emacs.d/init.el` and insert into it the following lines:
``` elisp
(use-package org-roam
  :init
  (setq org-roam-v2-ack t)
  :custom
  (org-roam-directory "~/RoamNotes")
  (org-roam-completion-everywhere t)
  (org-roam-capture-templates
   '(("d" "default" plain
      "%?"
      :if-new (file+head
               "%<%Y%m%d%H%M%S>-${slug}.org"
               "#+TITLE: ${title}\n#+AUTHOR: YOUR NAME\n#+LANGUAGE: Russian\n#+LICENSE: CC BY-SA 4.0\n#+DATE: %<%Y-%m-%d>\n#+FILETAGS:\n")
      :unnarrowed t)))
  :bind (("C-c n l" . org-roam-buffer-toggle)
         ("C-c n f" . org-roam-node-find)
         ("C-c n i" . org-roam-node-insert)
         :map org-mode-map
         ("C-M-i" . completion-at-point))
  :config
  (org-roam-setup)
  (org-roam-db-autosync-mode))

(use-package org-roam-ui
  :disabled
  :after org-roam
  :config
  (setq org-roam-ui-sync-theme t
        org-roam-ui-follow t
        org-roam-ui-update-on-save t
        org-roam-ui-open-on-start t))
```
* Replace of `YOUR NAME` with your name. You can also replace the language. But you can't change the license!
* Restart Emacs.

## How to work with these notes

* **Finding** or **creating** of note: press Ctrl-c then n then f, and then type note title. If the note is not found, then you can press Enter and then a new note will be created according to the template.
* **Linking** with other note: type note title and choose of appropriate note by pressing Enter. Other way: select text fragment, then press Ctrl-c then n then i, and then type note title. If the note is not found, then you can press Enter and then a new note will be created according to the template.

(c) Evgeny Simonenko, 2022-2025
