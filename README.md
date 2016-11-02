# Genoil's ZEC miner

A basic AMD OpenCL Zcash GPU miner. 

## Features
- AMD GCN architecture GPUs
- multi GPU
- stratum pool connection
- fast SilentArmy kernels
 

## Options
Command line options:

```
Command line param        Description              Example
--help,-h                 show help message        
--krnl,-k kernelname  	  set kernel(s)            -k zec
--conn,-c hostname:port   set host                 -c zec.suprnova.cc:2142
--user,-u username.worker set user                 -u Genoil.SilentArmy
--pass,-p workerpass      set password             -p z
--gpus,-g <x y z ...>	    set gpu(s)               -g 0 1 2 3 ...
--work,-w <n> 			      set work size(s)         -w 64
--ints,-i <n> 			      set intensity(ies)       -i 20
--plat,-P <n> 			      set OpenCL platform id   -P 0
--fail,f <n>              set gpu fail mode        -f 0
--zero,z <n>              set zero sols watch      -z 1
```

Notes:
- --krnl/-k parameter can have multiple parameters. This will launch more CPU threads, each running a miner with the specified kernel. For now, only dual (or more) zec is supported, i.e. '-k zec zec'
- --ints/-i parameter sets 2-log of equihash bucket size & OpenCL global work size. Only the following values are supported: 20, 19, 18, 16. Lower values will usually lower performance, but free up GPU resources for desktop work or dual mining.
- --work/-w parameter prefers powers of to between 64 and 256. You may experiment with other values.
- --plat--P paramter is useful for systems with iGPU enabled or mixed AMD/Nvidia GPUs.
- --fail/-f 0: attempt gpu restart 1: exit gpu thread 2: exit application (default: 0)
- --zero/-z 0: disable 0 sol/s watchdog 1: enable 0 sols/s watcdog (default: 1)

Example:
```
genoil.exe -c zec.suprnova.cc:2142 -u Genoil.SilentArmy -p z -P 0 -g 0 1 -i 20 -w 64
```

## Known issues

Current release may have problems compiling kernels on first use. It can help to launch the miner for a single gpu first, before trying to run with multiple GPUs. This is especially the case when you have differetn models of GPUs in your rig.


## Changelog

### 0.5
- show help message
- reduce number of '21' errors
- reconnect on 21 error
- reintroduce -w and -i switches

### 0.4.2
- GCN 1.0 support (SilentArmy v2)
- reconnect on 24 error

### 0.4.1
- does not require AVX2 CPU any longer

### 0.4
- SilentArmy v1 kernels

### 0.3 
- Trial & error release

### 0.2
- some bug fixes

### 0.1 
- initial release 

## Credits

Up until version and including version 0.3 I could use OpenCL ported versions of [John Tromp's Equihash solver](https://github.com/tromp/equihash). Thanks John, your rock!
From version 0.4 onwards I'm using [Marc Bevand's SilentArmy solver](https://github.com/mbevand/silentarmy). Thanks Marc, you march, silently!

Also thanks to ocminer from suprnova and feeleep from coinmine.pl for debugging assistance! And to my donators who provided me with shiny new GPUs!

Tips & donations are very much appreciated on:
- BTC: 1Nu2fMCEBjmnLzqb8qUJpKgq5RoEWFhNcW
- ETH: 0xeb9310b185455f863f526dab3d245809f6854b4d
