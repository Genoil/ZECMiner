# Genoil's ZEC miner

This is an early (binary) release of my ZCash (ZEC) miner. I know better 
alternatives are already available or maybe even out as we speak, but this one is 
for the Windows crowd out there that want to mine on ZEC stratum pools from day one.

## Options
Command line options are very limited:

- help, h: show this help message
- conn, c: set host
- user, u: set user
- pass, p: set password
- gpus, g: set gpu(s)
- ints, i: set intensity (defaults to 13)
- plat, P: set OpenCL platform id

Example:
```
genoil.exe -c zec.suprnova.cc:2142 -u Genoil.Tromp -p z -P 0 -g 0 1 -i 13
```
Have fun! 

## Credits

Based on an early release of [John Tromp's Equihash solvers](https://github.com/tromp/equihash). Thanks John, your rock!
Thanks to ocminer from suprnova and feeleep from coinmine.pl for debugging assistance!

Tips & donations are very much appreciated on:
BTC: 1Nu2fMCEBjmnLzqb8qUJpKgq5RoEWFhNcW  
ETH: 0xeb9310b185455f863f526dab3d245809f6854b4d
