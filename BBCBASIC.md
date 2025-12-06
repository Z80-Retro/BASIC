# Building BBC BASIC for the Retro/Nouveau

One way to build BBC BASIC on the Retro (or Nouveau) is to use the SLR Z80ASM compiler on CP/M 
(not the Linux package of the same name, not the one that comes with z88dk) using the following commands:

Assuming you have the SLR assembler & linker on drive a:

```
a:z80asm dist/rmf,main/rmf,exec/rmf,eval/rmf,asmb/rmf,cmos/rmf,math/rmf,hook/rmf,data/rmf
a:slrnk /V,BBC/N,/A:0100,dist,/P:0200,main,exec,eval,asmb,math,hook,cmos,/P:4B00,data,/E
```

This will create a BBC.COM file as well as various listings and object files.  
For example, I compiled it on drive G and the directory noe looks like this: 

```
g>dir
G: MAIN     Z80 : DIST     Z80 : ACORN    Z80 : HOOK     Z80
G: EXEC     Z80 : CMOS     Z80 : ASMB     Z80 : EVAL     Z80
G: MATH     Z80 : DATA     Z80 : AMOS     Z80 : DUMP     Z80
G: DIST     REL : DIST     LST : MAIN     REL : MAIN     LST
G: EXEC     REL : EXEC     LST : EVAL     REL : EVAL     LST
G: ASMB     REL : ASMB     LST : CMOS     REL : CMOS     LST
G: MATH     REL : MATH     LST : HOOK     REL : HOOK     LST
G: DATA     REL : DATA     LST : BBC      COM
g>
```

Now run it by typing `bbc` like this:

```
g>bbc
BBC BASIC (Z80) Version 5.00  
(C) Copyright R.T.Russell 2025
>      
```

Note that BBC BASIC wants allthe commands and keywords entered in upper case.  
You will need to type in code like this partially working game I was working on:

```
  300 REM shut off the cursor
  310 PRINT CHR$(27);"[?25l";
  320 REM clear the screen
  330 PRINT CHR$(12);
  340 LMAX%=2
  350 RMAX%=76
  360 REM initialize the position queue
  370 ROWS%=24
  380 DIM PFIFO%(ROWS%)
  390 FOR I=0 TO ROWS%-1: PFIFO%(I)=0: NEXT
  400 REM goto line 1 in position of the player
  410 PLAYER%=39
  420 SHIP$="-V-"
  430 SCORE%=0
  440 IF PFIFO%(1)<>0 AND PLAYER%-1 <= PFIFO%(1) AND PLAYER%+1 >= PFIFO%(1) THEN 650
  450 PRINT : REM scroll the display
  460 I$=INKEY$(1)
  470 IF I$="," AND PLAYER%>LMAX% THEN PLAYER%=PLAYER%-1
  480 IF I$="." AND PLAYER%<RMAX% THEN PLAYER%=PLAYER%+1
  490 IF I$="q" THEN 690
  500 GOSUB 610
  510 REM add a new asteroid to the screen
  520 SCORE%=SCORE%+1
  530 FOR I%=1 TO ROWS%-1: PFIFO%(I%-1) = PFIFO%(I%): NEXT
  540 PFIFO%(ROWS%-1) = INT(RND(RMAX%+1))
  550 X$=STR$(PFIFO%(ROWS%-1))
  560 PRINT CHR$(&1B);"[24;";MID$(X$,2,LEN(X$)-1);"H";"*";
  570 REM uncomment the following line to slow down the game
  580 FOR I%=0 TO 1000 : NEXT
  590 GOTO 440
  600 REM print the player's ship
  610 X$=STR$(PLAYER%-1)
  620 PRINT CHR$(&1B);"[1;";MID$(X$,2,LEN(X$)-1);"H";SHIP$
  630 RETURN
  640 REM turn cursor back on
  650 PRINT CHR$(&1B);"[4;1H";"BOOM!"
  660 PRINT "Your score is: ";SCORE%
  670 PRINT CHR$(&1B);"[?25h";
  680 END
  690 PRINT CHR$(&1B);"[4;1H";"quitting..."
  700 GOTO 660
```

Then run it by typing `RUN` (not `run`) and list it using `LIST` and so on.

Note that the above game will only work on a VT100/ANSI terminal and expect the screen to be 25x80.
