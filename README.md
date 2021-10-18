Tabs and ribbons for the mode line
==================================

This package provides utilities for displaying elements of the
mode line as tabs and ribbons.  It also provides replacements
for a few built-in elements.

![screenshot](http://readme.emacsair.me/moody.png)

* Make sure that the face `mode-line` does not set `:box` and
  that `:underline` and `:overline` are the same color or are
  both `undefined`.  If defined, then the line color should be
  different from the `:background` colors of both `mode-line`
  and `default`.  The same rules apply to `mode-line-inactive`.
  The line colors of `mode-line` and `mode-line-inactive` do
  not necessarily have to be identical.  For example:

  ```lisp
  (use-package solarized-theme
    :config
    (load-theme 'solarized-light t)
    (let ((line (face-attribute 'mode-line :underline)))
      (set-face-attribute 'mode-line          nil :overline   line)
      (set-face-attribute 'mode-line-inactive nil :overline   line)
      (set-face-attribute 'mode-line-inactive nil :underline  line)
      (set-face-attribute 'mode-line          nil :box        nil)
      (set-face-attribute 'mode-line-inactive nil :box        nil)
      (set-face-attribute 'mode-line-inactive nil :background "#f9f2d9")))
  ```

* Add something like this to your init file:

  ```lisp
  (use-package moody
    :config
    (setq x-underline-at-descent-line t)
    (moody-replace-mode-line-buffer-identification)
    (moody-replace-vc-mode)
    (moody-replace-eldoc-minibuffer-message-function))
  ```

* Such replacement functions are defined as commands, making it
  quicker to try them out without having to add anything to your
  init file.

* To undo the call to a `moody-replace-*` function, call the same
  function with `t` as the value of the optional REVERSE argument.
  You can accomplish the same by interactively calling such a
  function with a prefix argument to do so.
