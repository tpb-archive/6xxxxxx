Hold+ v4.0
Author: Torch

Tested on 5.50GEN-B

Hold+ is the ultimate companion to the PSP's music player. It adds useful features and gives you TWICE the battery life when used properly.

It does the following when the Hold switch is enabled:
* Switches off the LCD screen and backlight.
* Underclocks the CPU to 60MHz
* Fixes malfunctioning Hold switch
* The original screen brightness and clock speed are restored only when the Hold switch is released fully to the power off position
* Prevents the PSP from going into suspend mode if you accidently push the power switch too far when turning off Hold mode.
* Turns off LEDs in hold mode.
* While in hold mode, allows the use of Left, Right, LTrigger, RTrigger, Volume and Start buttons, if you hold the Select button first. Useful to skip songs, pause etc.

Additional Features:
* Enables the 5th brightness level on PSP Slim.
* Increases the vertical scrolling speed of Music player by around 50% (scroll 300 songs in 10 seconds).

Usage:
Turn on the Hold switch to automatically disable the display and underclock the CPU. Release the Hold switch fully to the power off position to return the CPU to normal speed and enable the display.

If you push the ANALOG UP button when turning on the Hold switch, it will only lock the keypad like normal hold mode. The display and CPU speed will not be changed, so that you can watch videos etc. with the keypad locked. Release the Hold switch fully to the power off position to unlock the keypad.

While the PSP is in hold mode, if you first hold down the Select button, you can use the following buttons: Left, Right, LTrigger, RTrigger, Vol+, Vol-, Start.

Installation:
You can install it in the seplugins folder, and make an entry in VSH.txt. Thus it will be active in the XMB. Its also possible to use it in games by adding it to GAME.txt, but some games may crash etc., if the CPU is underclocked to such a low value.

Optionally, its also possible to install it in your PSP's flash0 so that it will work without a Memory Stick. For this you can use FreePlay's "NewBTCFNedit" and enable it for VSH mode in the all the PSPBT?NF.bin files. Add it before vshmain.prx.

Advanced:
If you want to change the clock speed to your own values, you can use a hex editor to change them. The offsets in the file for v4.0 are
0x1154 - CPU
0x1158 - Bus (Should be half the CPU speed or less)

The values should be entered in hexadecimal. The default value for CPU is 3C (60 MHz in decimal) and the default value for Bus is 1E (30 MHz in decimal).

Note that simply using any arbitrary value will not work. You will have to test and see which values for CPU and Bus speed work.

Credits:
Thanks to adrahil for helping with preventing the suspend mode.

Thanks to Booster for the SysCon Hook sample, based on which Hold+ v3.0 was updated.

Changelog v4.0
----------------------------------
Now when the Hold switch is enabled, the PSP remains in hold mode permanently until the switch is fully pushed to the power off position. This will prevent a malfunctioning Hold switch from randomly interfering.

Removed Display Off mode (hold ANALOG UP while releasing Hold) since holding Select is sufficient for most users.

Changelog v3.8
----------------------------------
5th brightness level now works correctly on PSP-3000.

Changelog v3.7
----------------------------------
Optimized Code.
Proper fixed to prevent any chance of accidental suspend when coming out of hold mode due to pushing switch too far.
LEDs do not blink every 30 seconds anymore.

Changelog v3.6
----------------------------------
Incorporated Fast Scroll Music functionality into Hold+. Increases the vertical scrolling speed of Music player by around 50% (scroll 300 songs in 10 seconds).

Changelog v3.51
----------------------------------
5th brightness level is now restricted to PSP Slim, because its ineffective on Phat.

Changelog v3.5
----------------------------------
Enabled 5th brightness level. (If the screen dims due to being idle, it returns to the 4th brightness level. You'll need to press the Display button again to go back to the 5th level.)

Proper fix for faulty Hold switch.

Changelog v3.42
----------------------------------
Fixed a bug in the faulty Hold switch detection method. It should now be very resistant to problems such as CPU remaining underclocked due to faulty Hold switch.

Changelog v3.41
----------------------------------
Improved faulty Hold switch protection, as there were still some chances of a faulty Hold switch causing problems.

Changelog v3.4
----------------------------------
Fixed a problem caused by a faulty Hold switch in some PSPs. This made the CPU remain underclocked even after turning off the Hold switch.

The problem is the Hold switch doesn't consistently return a pressed state. It sometimes rapidly fluctuates between an Off and On signal. If this fluctuation occurs within one iteration of the main program loop, it causes problems. Its not humanly possible to toggle the Hold switch so fast, but a loose connection can :P

Changelog v3.3
----------------------------------
Fixed a bug where if the battery was low, and the Power LED was blinking, and you turned off the Hold switch exactly at the moment before the Power LED blinked, the problem of the dissappearing battery icon would occur.

The method of prevent accidental suspend has been changed back to adrahil's SysEvent method, instead of Booster's method which was used from v3.0, which was causing various problems as it worked by corrupting SysCon packets that contained the Power Switch On signal.

Changelog v3.2
----------------------------------
Fixed a bug where after you exit a Photo or the Browser, the battery icon would keep disappearing and reappearing.

Fixed a bug where each time you exit a Photo or the Browser, the first time you turn on Hold after that it would only go to Normal Hold mode.

Changelog v3.1
----------------------------------
Reduced CPU usage by delaying longer in main loop. Since v3.0 the main loop doesn't do much so it needn't run as fast as before. This *should* alleviate problems with the battery icon.

Now its not possible to accidently press 'other' buttons in hold mode while holding Select button. Ex: If you are holding Select + VolUp to increase volume, and you accidently press X, the X button will not have effect.

Changelog v3.0
----------------------------------
Completely overhauled the plugin to work using only the SysCon functions based on Booster's example.

The prevention of accidental suspend was changed to Booster's method as that is more efficient.

In Display Off mode, pressing the Screen button to return to normal no longer causes the firmware's internal brightness variable to become one step higher than the original screen brightness.

Added the ability to use some of the buttons while in hold mode, by holding the Select button first.

Changelog v2.71
----------------------------------
Fixed a bug where after the first time you resume from suspend the Analog Up + Hold Switch Off would not work.

Changelog v2.7
----------------------------------
LEDs are turned off when in Hold mode or Display Off mode, but they are flashed every 30 seconds so that the PSP is not mistaken to be powered off.

Fixed a bug introduced in v2.64 where the PSP wouldn't automatically suspend after being idle while in Hold mode or Display Off mode.

Changelog v2.64
----------------------------------
While in Display Off mode, you can now also turn on the display by pushing the power switch to the suspend position.

Pressing the Screen button also works but I recommend using the power switch instead, because when you press the Screen button, the firmware sets its internal brightness variable to the next level, even though the screen is functioning at the original brightness. Thus if you leave it idle after turning on the display using the Screen button, and the screen dims due to the PSP being idle, when you press a button it will jump to the next brightness level.

Changelog v2.63
----------------------------------
Fixed a bug where turning off the Hold switch very fast (less than 100ms) to the Power position would cause the PSP to enter standby.

Changelog v2.62
----------------------------------
Fixed a bug where the Analog Up features would not respond after opening the Photo menu in the XMB. After you exit the Photo menu, just toggle the Hold switch once and the Analog Up features should work after that.

Changelog v2.61
----------------------------------
Fixed a bug that was introduced in v2.6 that caused the control input buffer to completely fill up, hence causing the Analog Up features not to work in Hold mode, when the plugin was used for an extended period of time.

Changelog v2.6
----------------------------------
Modified the code a bit so that it should work better in GAME mode, although I don't really support using it in GAME mode.

Changelog v2.5
----------------------------------
Added feature to allow normal Hold mode where only the keypad will be locked without changing the display or CPU speed. Hold ANALOG UP when turning on Hold to do this.
The button for operating in Display Off mode has also been changed to ANALOG UP while turning off Hold.

Changelog v2.4
----------------------------------
Bugfix: When the PSP was left in Hold mode for longer than the idle timeout, and then you hold UP and turn off Hold, the screen used to turn on even though you were holding UP.

Changelog v2.3
----------------------------------
Bugfix: When the PSP was operated in display off mode (after holding UP and turning off Hold), if left idle for the duration of the LCD idle timeout, then after that pressing any key would enable the display. It was supposed to enable the display only on pressing the Screen key.

Changelog v2.2
----------------------------------
Added feature to allow operation of PSP with display turned off.

Changelog v2.1
----------------------------------
Fixed a bug where if the Hold switch was turned off and quickly turned on again, the PSP would not suspend after being left idle for a few minutes (the idle timeout didn't work).

Changelog v2.0
----------------------------------
Added feature to prevent PSP from going into suspend mode if the power button is pushed too far when turning off Hold mode.
