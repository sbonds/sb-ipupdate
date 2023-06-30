# sb-ipupdate

A fork of the abandoned but still widely used ez-ipupdate from SourceForge.

## Update Autoconf to work on a Rocky 8 host

* `git mv configure.in configure.ac`
* `aclocal`
* `automake`

```text
configure.ac:5: warning: AM_INIT_AUTOMAKE: two- and three-arguments forms are deprecated.  For more info, see:
configure.ac:5: https://www.gnu.org/software/automake/manual/automake.html#Modernize-AM_005fINIT_005fAUTOMAKE-invocation
configure.ac:11: error: required file './compile' not found
configure.ac:11:   'automake --add-missing' can install 'compile'
Makefile.am:3: error: 'ez_ipupdate_SOURCES' includes configure substitution '@EXTRASRC@';
Makefile.am:3: configure substitutions are not allowed in _SOURCES variables
Makefile.am: error: required file './depcomp' not found
Makefile.am:   'automake --add-missing' can install 'depcomp'
```

* `automake --add-missing`

```text
Makefile.am:3: error: 'ez_ipupdate_SOURCES' includes configure substitution '@EXTRASRC@';
Makefile.am:3: configure substitutions are not allowed in _SOURCES variables
```

Remove @EXTRASRC@ and @EXTRAOBJ@ from Makefile.am

* `automake`
* `autoconf`
* `./configure`

```text
...
checking build system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized
configure: error: /bin/sh ./config.sub x86_64-unknown-linux-gnu failed
```
