# BASIC
Yet another BASIC implementation

See the discord [Z80-Retro! BASIC thread](https://discord.com/channels/1010951092277874791/1427916714548527176)

# Minimal must-have list for an proof of concept/alpha release (very likely to change)

- support line-number style (unstructured)
- list files and save and load files
- peek / poke
- ability to delete multiple lines
- support for variables with longer names. Up to 8 chars?
- values in decimal and hex with ability to print in hex too. 
- DATA and READ (uses an auto increment pointer good for loading graphics etc)
- save in text/untokenised format
- IN and OUT for IO access
- Page at a time listing

Nice to have:

- support structured style BASIC
- save in tokenized and untokenised formats. 
- ideally some form of inline editor.  Shouldn't have to retype the whole line every time I want to make an edit 
- graphics primitives and MODE to set the graphics mode
- some form of editor. Especially if doing structured basic
- baked in xmodem or other for pulling files over serial (maybe add `xload` and `xsave` commands that can do this?)

# Other Implementations For Inspiration

- https://jorgicor.niobe.org/bas55/ (This includes a note: The ECMA-55 standard was chosen over the "ANSI X3.60-1978 minimal BASIC" standard since it is free.)
  - https://github.com/jorgicor/bas55 (ECMA 55 minimal BASIC, implemented using yacc)
  - https://buraphakit.sourceforge.io/BASIC.shtml
- https://github.com/nanochess/CVBasic
- https://www.bbcbasic.co.uk/bbcbasic/z80basic.html
- https://github.com/paulscottrobson/neo6502-firmware
- bbcbasic.  It supports inline assembly.
- cvbasic.  Not native. It compiles down to assembly and is meant for cross compiling.the neo6502 platform has a version of basic that runs natively but and has structured programming.

After apple basic on the apple 3 I used qbasic on my dos PC.  It had a cursed type interface and supported functions and sub / end sub routines.  Structured.  The thing had a full blown manual inside it making it easy to learn.
I love the idea of a retro-basic.  If it's in the other rom bank,  The only hard to replicate thing is the filesystem. Serial is easy.  The graphics features are already something that we do without ROM or CPM support.

# Links to Useful DOCs

- https://en.wikipedia.org/wiki/Full_BASIC
  - [ECMA 116: Full BASIC](https://web.archive.org/web/20111014140105/http://www.ecma-international.org/publications/files/ECMA-ST-WITHDRAWN/ECMA-116,%201st%20edition,%20June%201986.pdf) (withdrawn?)
  - [ANSI X3.113-1987: Full BASIC](https://archive.org/details/federalinformat6821nati_0)
  - [ANSI X3.124-1985: Graphical Kernel System (GKS) functional description](https://nvlpubs.nist.gov/nistpubs/Legacy/FIPS/fipspub120-1.pdf)
- https://en.wikipedia.org/wiki/Minimal_BASIC
  - [ECMA 55: Minimal BASIC](https://www.ecma-international.org/wp-content/uploads/ECMA-55_1st_edition_january_1978.pdf)
  - [An ASCII version of ECMA 55](https://buraphakit.sourceforge.io/ECMA-55.TXT)
 
# Manuals

- [BASIC-80_Reference_Manual_VT180_V5.21_1981](http://www.bitsavers.org/pdf/dec/terminal/vt180/AA-P226A-TV_BASIC-80_Reference_Manual_VT180_V5.21_1981.pdf)
- [Getting_Started_With_MBASIC_VT180_V5.21_1981](http://www.bitsavers.org/pdf/dec/terminal/vt180/AA-P225A-TV_Getting_Started_With_MBASIC_VT180_V5.21_1981.pdf)
