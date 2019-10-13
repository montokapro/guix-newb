## Background

The Contributing section of the guix documentation suggests you build for systems other than your own, including mips. It is my belief that the documentation is not aligned with community practices.

I encountered this issue when building the `emacs-dimmer` package, which I was attempting to contribute:
```
$ ./pre-inst-env guix build --system=mips64el-linux -K --rounds=2 emacs-dimmer
building /gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv...
@ unsupported-platform /gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv mips64el-linux
while setting up the build environment: a `mips64el-linux' is required to build `/gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv', but I am a `x86_64-linux'
note: keeping build directory `/tmp/guix-build-guile-bootstrap-2.0.drv-0'
builder for `/gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv' failed with exit code 1
build of /gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv failed
View build log at '/var/log/guix/drvs/ks/rb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv.bz2'.
cannot build derivation `/gnu/store/ka1hnnirxk9jlwwqsl36cvl2l6l8ilmw-bash-minimal-5.0.7.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/ccw7xl9s779f1fz3bk2wh2zd3ifllm1r-binutils-2.32.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/ijxi3ldhyapfshxg08xrpwb43zhpcxcj-binutils-cross-boot0-2.32.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/bdgipvg8fdzs75lpx4dn4vxzm213y495-bootstrap-binaries-0.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/m33ryw4mjmq3hq9qwqsy1lmmn3l2f7qj-diffutils-boot0-3.7.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/avrnh1rz1p3lcdl2rq1n45ljs0vghsda-file-5.33.tar.xz.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/dfi41q6sk6ss5ip9dcgm8qpjmki43z4d-file-boot0-5.33.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/84kjzlympmbb1ibji8yghlh3xhqcf4aq-findutils-4.6.0.tar.xz.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/d9ya452rhn3fp58srs7h3vdby0fx772b-findutils-boot0-4.6.0.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/g5gr1flg0x7mdnzzw7j5yycm372abdwv-gcc-7.4.0.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/a6damla1zy4c26h6cq2474viybg0y9rj-glibc-2.29.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/zq0xddk9qax0jlcgzclrvf9q4mc2r8wk-gmp-6.1.2.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/nra1gnggph0mkm8dkw0c11v5d08a5gwl-gmp-6.1.2.tar.xz.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/f8kbra1nvpshx2kwgyj9b0js8ssrk5l9-grep-3.3.tar.xz.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/ryjrpmhh55k6qaajqihzbk5jpd066cfm-guile-2.2.6.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/mjgjaaym2i50bsccz3cv3s6fh9bgdmfp-gzip-1.10.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/gjc650favfc9yf1rfv1viv5gm72dcv7n-ld-wrapper-boot0-0.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/llzxa2sz7ymk9nzriwli9kyn9xsfc7z1-ld-wrapper-boot3-0.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/0s2r5pb5dr7f608zwbslvj82xcfhi66n-libgc-7.6.12.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/w6k1awds5ygfynab77rjpvw9x4v1vj7k-libltdl-2.4.6.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/p95kmdvk5n8dkvrwjwyn1vy20xc99ncd-libunistring-0.9.10.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/3h99sly7c57byh0mb05nhg9sdcmyyf0s-linux-libre-headers-4.19.56.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/lrzi2bwl4lq2a3lnhs1r22xmrw0mg57c-m4-1.4.18.tar.xz.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/s02vfvjvwgi35810sy4p1ij9r3z03ddc-make-4.2.1.tar.xz.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/x6wy7zyn995s5wv71yn2603r9qbqd5qf-make-boot0-4.2.1.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/afkhcd78k38arz89py8s2lqafiisz4xx-patch-2.7.6.tar.xz.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/6zyhx2nvqi43fxph3yha7605hj1z8vn6-perl-5.30.0.tar.xz.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/lnrf9crd8rcwxc3bid4simlmskm216hg-perl-boot0-5.30.0.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/ysyrgcj9mabqb9w5p8scilmc9kqfvmz7-tar-1.32.tar.xz.drv': 1 dependencies couldn't be built
cannot build derivation `/gnu/store/dhw93qckc2y2pqq5j0x67kvv1mykw3j3-ghostscript-9.27.drv': 1 dependencies couldn't be built
guix build: error: build of `/gnu/store/dhw93qckc2y2pqq5j0x67kvv1mykw3j3-ghostscript-9.27.drv' failed
```

A succinct recreation of the error can be found by building guile-bootstrap:
```
$ guix build --system=mips64el-linux -K --rounds=2 guile-bootstrap
The following derivation will be built:
   /gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv
building /gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv...
@ unsupported-platform /gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv mips64el-linux
while setting up the build environment: a `mips64el-linux' is required to build `/gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv', but I am a `x86_64-linux'
note: keeping build directory `/tmp/guix-build-guile-bootstrap-2.0.drv-2'
builder for `/gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv' failed with exit code 1
build of /gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv failed
View build log at '/var/log/guix/drvs/ks/rb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv.bz2'.
guix build: error: build of `/gnu/store/ksrb1jlhj7ks893k53akyjizg6rrrhpy-guile-bootstrap-2.0.drv' failed

```

## Resolution

I ignored mips build errors and contributed the package as is. It would seem that the mips build process is a low priority as of now.
