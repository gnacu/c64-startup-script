# c64-startup-script
A startup script for the C64

This is a text dump of a BASIC program (s.bsc). The text is in PETSCII not ASCII. Sorry if that makes you unhappy because you can't read the file on a PC properly without converting it first. But, it's for the Commodore 64, and the Commodore 64's native text encoding is PETSCII. (I caved an added an ASCII translation, s.txt)

The C64 doesn't (in stock configuration) have the ability to run a script at startup automatically. If you only have a floppy drive, this is not going to serve you unless you put a copy of this on every single disk. But, if you have a hard drive or equivalent mass storage device, then you can just stick it in the root directory of the default partition. It's named "s" to be minimally short and easy to run.

If you have JiffyDOS, you can run it after a fresh bootup with 3 keystrokes (2 characters plus RETURN.)

^s

If you don't have JiffyDOS and you don't have a hard drive, then, just don't worry about this script at all. It's designed to work with JiffyDOS. 

It's divided into a few main parts:

# Screen Colors

Clears the screen, switches character set to upper/lower, sets the border, background and foreground colors to those of the SX-64's default KERNAL ROM. These are obviously customizable to the colors you prefer.

# Define Function Keys

This is meant to work with JiffyDOS's function key definition overrides. The way this script is setup is custom to what I want, but you can follow the template and customize these to however you want them.

F1: List current directory
F3: Load and run Turbo Macro Pro from the root directory of partition 1.
F5: Load and run NovaText from the root directory of partition 1.
F7: Load and run a Machine Language Monitor from the root directory of partition 1.

F2: Load and run the C64 OS booter from the root directory of partition 1.
F4: Prep a file in a directory listing to be read with JiffyDOS's @t command.
F6: Load and run this startup script again, from the root directory of partition 1.
F8: Prep a file in a directory listing to be scratched with JiffyDOS's @s command.

# Configure Drives

Set the default device number to 8. Set the JiffyDOS copier's target device to 10.

Change the default device to partition 1. Changing to the root directory has been commented out. You can use this if you want, but I found that it was more convenient for it to leave me in the current directory.

Lastly, it closes any and all open files on device 8.

# Ready Message

Sets a workspace memory variable to enable auto-repeat of all keys.

Outputs an inspirational message. Then outputs the current date and time, which is read from the RTC of the default device. 

It then gosubs to the Help Display section. This can be commented out if you don't need the help text.

Issues a NEW, which removes this startup script from memory.

# Help Display

Prints a simple table on the screen with an explanation of all the function keys. If you customize the function keys you can customize this help display. 

If you make multiple versions of this start up script, the help display can help remind you of which version of it you just loaded in. For instance, you might have one for getting quick access to a some games you're currently playing. Or another one to get access to a different set of tools or utilities.

# Quick Save

I often finish my BASIC programs with a section at the end, typically at line 5000, for saving any changes made to this program. 

line 4999 starts with an END, so that if the program goes rogue and keeps running, it'll end before reaching the 5000 quick save. After making any modifications to this program, you can just type 

run5000 

to save this program, with overwrite option, to the current device.


