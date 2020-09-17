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

# How to give SBCL a nice REPL with linedit

At the SBCL command prompt evaluate:

```
(ql:quickload :linedit)
```

Add the following lines to the end of your .sbclrc

```
;;; Check for --no-linedit command-line option.
(if (member "--no-linedit" sb-ext:*posix-argv* :test 'equal)
    (setf sb-ext:*posix-argv* 
	  (remove "--no-linedit" sb-ext:*posix-argv* :test 'equal))
    (when (interactive-stream-p *terminal-io*)
      (require :sb-aclrepl)
      (require :linedit)
      (funcall (intern "INSTALL-REPL" :linedit) :wrap-current t)))
      
```
