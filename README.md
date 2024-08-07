[The project I forked this from has integrated my changes, credited me (thanks!), and provided a compiled binary here.](https://github.com/t0mtee/FromStutterFixUpdated)

# FromStutterFixUpdated

This tool will apply a fix for a certain type of stutter in FromSoft games. It can also disable achievements in Elden Ring, to work around a bug where achievements can freeze the game when Steam is offline.

Supported patches:
* DS3 1.15.2
* Sekiro 1.06
* Elden Ring 1.10.1

## What's new?

* I have updated the Dark Souls 3 pointers so it supports the latest patch (1.15.2) and plan on keeping them updated into the future (at least until my friend stops playing Dark Souls III)

* I added a debug console, so I don't have to deal with messy message boxes
## Usage

There is a standalone .exe version which doesn't touch the game files, but needs to be run manually each time and there is also a .dll version which loads automatically. Both do the same thing.

Note: EAC needs to be disabled for Elden Ring.

### EXE Version

Run the game, then run the program. It will say "flag set" if it worked. Close the program. The fix will last until you restart the game.

**ONLY NEEDS TO BE DONE FOR ELDEN RING:** To enable the achievement fix, create a file with no extension in the same folder as the StutterFix EXE called "achievement".

### DLL Version

* If using dinput8 mods: You'll need to chainload this using:
	* **Elden Ring:** I recommend Elden Mod Loader as Mod Engine 2 seems to have some issues chainloading multiple mods.
	* **Dark Souls 3:** Use DS3 Mod Engine.
	* **Sekiro:** Use Sekrio Mod Engine.
* If not using any dinput8 mods: Rename StutterFixDLL.dll to dinput8.dll and place it in the same folder as the Elden Ring EXE file.

**ONLY NEEDS TO BE DONE FOR ELDEN RING:** In both cases, to the enable the achievement fix, create a file with no extension in the mods folder (create the folder if not using Elden Mod Loader) called "achievement".

## How does it work?

The game does...something, relating to Steam Input, which scans over all devices (basically everything listed in Device Manager). This happens any time any device changes, like a microphone being plugged in, a bluetooth headset pairing, or a driver update happening in the background. The game stops rendering frames until this is done, and it can take up to a second on some PCs.

The game has a flag which turns this off. This program sets the flag.

## Okay, but how do I know it's working?

Run the game without the fix, and try plugging/unplugging a USB dongle. If windowed, make sure the game window is focused (the stutter won't happen otherwise). You should see a noticeable stutter. Now apply the fix, then repeat the test. It should no longer occur.

On the DLL version, a sound will play at boot if the achievment fix is enabled.

## Does it break anything?

I don't know. I haven't noticed any problems. If you actually use Steam Input, it might stop working. Replugging a controller still works for me.

The achievement-disabling freeze fix will prevent you from getting any achievements, but you probably have them all by now anyway.

## This fixed my unplayable stutters that happened every 10 seconds!

Cool, but something is probably still wrong with your PC. Check if anything looks weird in Device Manager, eg. if it's constantly refreshing, or any warning symbols.

## I still get stutters at certain points in the game

Stutters at loading triggers probably can't be fixed, except by From, or a miracle patch to the rendering pipeline. There may be other sources of stutter also.

## Credit

* Original program is by kh0nsu and in turn I forked this off OsoaGH, I have not done much beside adding a debug console, added typing and changing the offset values for Dark Souls III.
* I forked this off OsoaGH
* OsoaGH found the new pointers by debugging ERTool and just adding those to this program.
* I found the pointers by getting referred to the problematic code by a friend (Ike) who wanted me to make a patch for him, I don't play Dark Souls or any Souls-like game.
  It involved doing some minor pointer chasing using Cheat Engine.  
