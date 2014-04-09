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

However, I immediately ran into a bug on OS X, which I fixed by editing wgr.f90.
```
The file output routines do not distinguish between non-capitalised and
capitalised letters. 
The code then crashes at line 600 in wgr.f90, upon trying to open
'Gr-neutrons.dat' which overlaps with 'gr-neutrons.dat'.

A fix is to rename the files in lines 582, 583, 591, 592 of wgr.f90.
```

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

I'm trying to get this working with a 2x2x2 supercell of MAPI perovskite. See
here: https://github.com/WMD-Bath/Perovskites

GOOD LUCK!
