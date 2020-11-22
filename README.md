# DFIR ORC Configuration

New version the memory could just be used with x64 arch.

This configuration include memory dump with _winpmem.exe_
and GetMemFiles (pagefile,swapfile,hiberfil).

If you don't want then you need to put the optional parameter at "yes"
in the __DFIR-ORC_config.xml__ part "ORCMEM" (or comment/uncomment conf).

It's possible to not execute Memory dump with an explicite `/-key=Memory` when
you launch the DFIR-ORC.

```
DFIR-ORC.exe /-key=Memory
```

To configure DFIR ORC, you need:
* configuration files in XML format, located in the "config" directory
* items to embed (especially DFIR-Orc binaries in 32 and 64 bits),
stored in the "tools" directory
* check "output" directory is __empty__ (no DFIR-Orc.exe)

The configurations given as example here use Sysinternals "Autoruns"
tools. You have to download and put it in the "tools" directory.

The "tools" directory must therefore contain the following files:
* DFIR-Orc_x64.exe
* DFIR-Orc_x86.exe
* autorunsc.exe
* winpmem.exe
* tcpvcon.exe

Include here.

Finally, to generate a configured DFIR-Orc executable, you have to run
the "Configure.cmd" script (on a Windows system).

The generated binary is created in the __"output"__ directory.

# Use

From our Windows workstation

```
git clone https://github.com/DvAu26/dfir-orc-config.git
```

In a administrator CMD windows :

For an x64 build (you need a x64 Windows of course):

```
> cd dfir-orc-config
> Configure.cmd
```

For an x86 build :

```
> Configure_x86.cmd
```

Wait seconds... check the output directory (cut and paste out of the output directory)

You can test __DFIR-Orc.exe__ ;)

- Good reading ;)
```
DFIR-Orc.exe /?
```

- To know archives and commands set
```
DFIR-Orc.exe /keys
```

You can add or del commands or archives with `+key=` or `-key=`.

_Get SWAP Files is optional now_
For example you can just do memory with this command :

```
# Just winpmem for x64 arch
DFIR-Orc.exe /key=Memory

# Just Swapfiles
DFIR-Orc.exe /key=GetMemFiles
```

Or just the main part with :

```
# Just the Main
DFIR-Orc.exe /key=Main
```

You can add NTFSInfoHashPE and FatInfoHashPE with this command :

```
DFIR-Orc.exe /+key=NTFSInfoHashPE,FatInfoHashPE
```

PE Hashes
> MD5 from all PEs will take time... you can update __command_timeout__ and __ElapsedTimeLimit__.

## Authors and contributors

Authors and contributors are the same as listed in the
[AUTHORS file of GitHub repository of the source code](https://github.com/dfir-orc/dfir-orc/blob/master/AUTHORS.txt).
