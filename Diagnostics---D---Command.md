##Diagnostics < D > Command##

Since its not uncommon for user to have initial problems with configuring the Base Station, I added a new diagnostics **< D >** command to the Base Station code that will help in debugging issues. Here's the steps I would recommend:



1. Remove the Motor Shield ---we are going to test just the Arduino first.  
2. Download and install the most current version of [DCC++ Base Station](https://github.com/DccPlusPlus/BaseStation) (not the latest named release, which is about a week old, but rather the latest version with the new commit Date).  
3.  Open the Serial Monitor Window in the Arduino IDE and establish communication with the Arduino. You will need to set the serial data rate to 115200 baud. If you see gibberish instead of English, this is probably set  incorrectly.  

###Testing the Arduino and Base Station code###

Next, we are going to utilize the built-in on-board LED attached to pin 13 to test the Arduino and Base Station code. This series of tests only works if you are NOT using pin 13 for any sort of output (using it as an input is okay).  

1. Connect a jumper from pin 13 to whatever pin you have defined (or was already defined in the software) for SIGNAL_ENABLE_PIN_MAIN  
2. The LED next to pin 13 should go off (or remain off, if it was already off)  
3. Send a **< 1 >** command to turn on track power --- the LED should go on.  
4. Send a **< 0 >** (that's a zero) command to turn off track power --- the LED should go off.  
5. Repeat this a few times to check for robustness.  
6. Assuming this works, now perform the same test for the the programming track by connecting the jumper from pin 13 to whatever pin is defined for SIGNAL_ENABLE_PIN_PROG.  

If either of these tests fail, first review the DCCpp_Uno.h file to make sure you are indeed testing the right pins and matching SIGNAL_ENABLE_PIN_MAIN and SIGNAL_ENABLE_PIN_PROG. If one or both of these pins is not able to control the LED attached to pin 13, there is likely something amiss with the Arduino itself.  

If both tests pass, it means the Arduino should be able to correctly enable/disable track power, at least from its perspective.  


###Testing the DCC signal###

Now the fun part -- we are going to test the generation of the DCC signal itself.  

1. Move the jumper once again so you are now connecting pin 13 to whatever pin is defined as DCC_SIGNAL_PIN_MAIN.  
2. The LED next to pin 13 should go on, regardless of whether track power is set on (**<1>**) or off (**<0>**). Track power control does not alter the actual DCC signal generation on the Arduino.  
3. Now send a **< D >** command to the Arduino --- this SLOWS DOWN the entire system clock by a factor of 256, and also slows down the speed of the timers generating the DCC signal.  
4. The LED next to pin 13 should now be blinking - mostly fast, but sometimes a little slower for just one or a handful of blinks. This is the actual DCC signal. Fast blinks represent a one-bit, slow blinks represent a zero-bit.  
5. You'll note that once you send the **< D >** command, the Arduino will respond with a message indicating "Entering diagnostic mode..." This is the last communication you will be able to send or receive while the window is open. To re-establish communication and reset the clock speed you will need to close and re-open the serial monitor window, or cycle power on the Arduino, or hit the reset button on the Arduino. But don't do that just yet.  
6. Repeat the test for for programming track DCC signal by moving the jumper to connect pin 13 to whatever pin is defined as DCC_SIGNAL_PIN_PROG.  
7. You do not (actually cannot) need to send the **< D >** command again - the Arduino will still be in diagnostic mode unless you've close and re-opened the serial monitor window.  
8. As before, the pin-13 LED should now be blinking. The program-track DCC signal defaults to the same as the main-track DCC signal when the system first starts so the blinking pattern of ones and zeros should be the same. However on the UNO (but not the MEGA), the entire pattern will be twice as fast for the programming track than for the main track DCC signal. This is not normally the case, but the diagnostic mode can't slow the two signals down to the same rates on the UNO.  

If either of these tests fail, first review the DCCpp_Uno.h file to make sure you are indeed testing the right pins and matching DCC_SIGNAL_PIN_MAIN and DCC_SIGNAL_PIN_PROG. If you are and one or both of these pins is not causing the pin-13 LED to blink, then that suggests there is something wrong with the Arduino timers or interrupts. But before drawing that conclusion, run the entire test a few more times to double-check, since the new diagnostic command is...well, new.  


###Testing the Motor Shield###

If first two tests pass, then the Arduino is functioning correctly and it's time to test the Motor Shield.  

1. Power down the Arudino  
2. Install the Motor Shield, and make sure it has power, though do not connect to the tracks  
3. Verify that all of the mappings are correct, and that the signals on the Motor Shield are properly being mapped to the enable and signals pins you identified above.  
4. Open (or re-open) the Arduino Serial window  
5. Send a **< 1 >** command.  
6. All 4 lights next to the outputs of the Motor Shield should be on  
7. Send a **< D >** command to enter diagnostic mode  
8. All 4 lights should now be blinking - the two attached to one output channel should blink in alternation, and the two attached to the other output channel should also blink in alternation.  

If neither of the LEDs attached to one of the output channels comes on when you send a **< 1 >** command, this indicates you are not correctly mapping either the SIGNAL_ENABLE_PIN_MAIN or SIGNAL_ENABLE_PIN_PROG pins from the Arduino (depending on which output channel does not appear to be working). From the above tests, we know those pins on the Arduino are working, so it must be in the wiring or jumpers between that Arduino pin and the pin used to enable to the Motor Shield for that channel (if indeed a wire or jumper was needed at all).  

If only one of the LEDs attached to the one of the output channels comes on when you send a **< 1 >** command, but the other does not, this suggests that either the DCC signal is not getting through to the Motor Shield, in which case it is a mapping/wiring/jumper problem, OR that the signal is getting through but the H-bridge on the Motor Shield itself is not functioning (and the Motor Shield may need to be replaced). To see which is the case, check whether the lone-LED begins to blink once you send the **< D >** command. If it does not, that indicates that problem is in mapping the DCC signal generation pin (which we know is working from the above tests), to the Direction pin on the Motor Shield. If the lone-LED does start to blink after sending a **< D >** command, but the opposing LED does not blink in alternation, then something is wrong with the Motor Shield and it likely needs to be replaced.  

I hope this helps with your diagnosis - please let us know what you find.  
[DCC++ Discussion on Trainboard](http://www.trainboard.com/highball/index.php?threads/introducing-dcc-a-complete-open-source-dcc-station-and-interface.84800/)    

-Gregg