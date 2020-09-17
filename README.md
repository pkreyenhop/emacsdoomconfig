# How to install Emacs Doom with a nice config for Common Lisp

```
git clone --depth 1 https://github.com/hlissner/doom-emacs ~/.emacs.d
git clone https://github.com/pkreyenhop/emacsdoomconfig.git ~/.doom.d
~/.emacs.d/bin/doom install
```
# How to make SBCL load libraries with Quicklisp

```
curl -O https://beta.quicklisp.org/quicklisp.lisp
sbcl --load quicklisp.lisp
```
At the SBCL command prompt evaluate:

```
(quicklisp-quickstart:install)
(ql:add-to-init-file)
```
To test evaluate `(ql:quickload :asdf)`

