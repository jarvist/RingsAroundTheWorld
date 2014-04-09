First we've got to compile Rings! 

On OS X, I had to reconf with this magic:
```
automake --add-missing
autoreconf
./configure
make -j8
./src/rings
```
Hurrah it compiles! I also recommend opening ./src/input.f90 to understood
where it's chocking on your input / options files.

Files care about line numbers / blank lines at top.

The VASP input routines choke on the new human readable atom-list (so delete
that line from your XDATCAR).

Rings generates XMGRACE output files.

My PWD looks like this. ./data and ./options are hardcoded to rings.
```
> ls -R
README.md             data/                 gr/                   options
rings_input_MAPI.dat
./data:
POSCAR   XDATCAR
```

GOOD LUCK!
