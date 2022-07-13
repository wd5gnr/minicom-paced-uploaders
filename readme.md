Paced Uploaders
===============

These are two programs I wrote a long time ago to solve specific problems uploading
to the COSMAC ELF2K and AmForth. 

The idea is to send a character and wait for an echo and/or some special characters.
They plug into minicom.

Compile
=======
To compile this file:

```
gcc -o am4up am4up.c 
```

Then copy the am4up executable to your path somewhere 

Or use elf2k-xfrv2.c if you are using that version

Install
=======
Minicom uploader has stdin connected to serial input,
stdout connected to serial output
stderr connects back to minicom
exit code 0 for success or non zero for fail
 
To set this up, use Control+AO and configure file transfer 
protcols. Set a name and the program file name 
Set Name=Y, U/D to U, FullScrn to N, IO-Red to Y, and Multi to N

OR you can put this in /etc/minicom/minirc.amforth

```
# Machine-generated file - use setup menu in minicom to change parameters.
pu pname10          YUNYNamforth
pu pprog10          am4up
pu baudrate         9600
pu bits             8
pu parity           N
pu stopbits         1
pu minit            
pu mreset           
pu backspace        BS
pu rtscts           No

 ```

 Obviously, change am4up if you are using elf2k...

 Then start minicom like this:
```
minicom -w -D /dev/ttyUSB1 amforth
```

This presumes you have am4up (this file compiled with gcc) on your path
and you are using /dev/ttyUSB1.
 
 