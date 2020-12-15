I've found a workflow that works for me to generate new packages. This lets me stage new packages for introduction into the main guix repository, or add local packages. This is important to me, because the main guix repository has become too big to be effectively hacked on - it exhausts all the memory available in emacs and causes crashing.

My local `~/.config/guix/channels.scm` looks like this:
```
(cons*
 (channel
  (name 'free)
  (url "file:///home/steve/code/guix/free/.git")
  (branch "master"))
 ;; (channel
 ;;  (name 'montokapro-free)
 ;;  (url "https://github.com/montokapro/guix-free.git"))
 %default-channels)
```

When I add a new package, I first add a commit to my master branch in guix with the new package, without pushing it. In the future, I'd like to restrict this to my "development" channel.
```
guix pull --allow-downgrades
```

I then build my package using:
```
guix build example-package --check
```

If I am building a particular version of that package and I want to see all of the versions, I run:
```
guix search example-package
guix build example-package@example-0.123456 --check
```

Whenever I encounter a problem, I use a variant of the below command to debug:
```
bzcat /var/log/guix/drvs/ex/example-path.drv.bz2 | less
```

Committing to the official guix project is a bit more complicated (lots of conventions to get right_, so I find this to be a lower barrier of entry to getting things accomplished.
