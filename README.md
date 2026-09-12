# Bitcoinminer

3074
-
-The everything port.
-Blocks world updates, damage and buffs mostly.
-Flush Buffer will instantly re-sync you (without unticking).
-you can use flush buffer instead unticking to update your world.

27K
-
- Player connection port.
- stop player position updates.
-Prevent matchmaking players.
-Keep revive tokens.

7500
-
-API updates and items switches.
-Auto disable allows you to set a timer for which this module will automatically disable itself after the timer is up unless you’ve unticked already.

30K
- 
-Blocks joining, objectives, world connection.
-Auto disable allows you to set a timer for which this module will automatically disable itself after the timer is up unless you’ve unticked already.
use this to hold auto revives from objective updates.

30K slow
- 
-Blocks joining, objectives, world connection.
-Delays all inbound 30K packets by a fixed amount of time.
-Use this for holding a reconnect.
-Auto disable allows you to set a timer for which this module will automatically disable itself after the timer is up unless you’ve unticked already.

30K super
- 
-Blocks joining, objectives, world connection.
-Changes the window size of all outbound 30K packets.
-Can reliably be held for a minute and a half, longer is not always guaranteed.
-Resync is bad.
-Use this for holding joining and for holding objective updates when you don’t need an auto revive from them.
-Auto disable allows you to set a timer for which this module will automatically disable itself after the timer is up unless you’ve unticked already.

Reconnect
- 
-Forces a new 30K connection.
-Forces an anteater error code.
-Will resync on fireteam leader.

Gamepause
-
-Suspends the d2 to process.

Weasel
-
-Forces a new 7500 connection.

Load manipulation
-
-Blocks inbounds 30K traffic for a set static amount of time before an instance starts. This allows you to get a better load .
-23 seconds of blocking should guarantee a perfect load.

75 Damage Module. 
-
-Automatically block 7500 packets when it detects a swap between two specific guns.
-This should only trigger when switching between the two weapons which you specify.
-A click while blocking will stop blocking so that when you shoot, it will immediately resync without any other inputs.
-To find the trigger length you need to download WIRESHARK and apply the filter TCP.SRCPORT == 7500 to your active network interface. With WIRESHARK open, switch between the two guns of your choice (likely Lorentz Driver and Duality) somewhat frequently, about twice a second is nice. When swapping guns there should be a burst of 3 to 4 packets on WIRESHARK one of the packets Len (far right) will probably be 87, one of the other ones will probably be 43, one around 150, and the last about 190 - 230. You’ll use the biggest one. For me it’s 198, I’ve seen as high as 230 and as low as 170. Put your packet length in the trigger length text box and then enable the module, turn it on, and try switching guns and you’ll see how it works.

UL Slow Damage Module.
-
-This also has a trigger based on when you switch between two specific weapons. Find the trigger length the same way.
-When you turn this on, it will tick UL slow. When you switch between the designated weapons it will wait for the delay and then it will flush buffer.

3074 2
-
-Added for compatibility with K3's macros.
-I suggest using different binds for this module and leaving buffering off.

27K 2
-
-Added for compatibility with K3's macros.
-I suggest using different binds for this module and leaving buffering off.

Dialogue Skip
-
-Will automatically swap loadouts to skip dialogue in loads.
-Search time is the amount of time after an instant starts that it will search for.
-Duration is the amount of time to swap for.
-Delay is the amount of time between clicks.
-Swap order and the associated grid or text box controls which loadouts to swap between.
-In normal mode the order is descending from 1 to 20.
-Ending loadout optionally select ending loadout (0 for no ending loadout).
-Close inventory forcibly closes the inventory screen after the swap sequence (Note that loading in will also do this for you).
-By default this module is network based and looks for a certain packet to use this.
-Visual based trigger, is a pixel color based version where it will look for certain black pixels on your screen.
-Force focus allows the module to force focus destiny when it should if you are tabbed out. This works with both the normal network based and the visual based triggers.

Freeze Hotkeys
-
-There’s a new keybind in the service window that allows you to bind a 'freeze hotkeys' keybind.
-When this is enabled it will prevent any other hotkeys from triggering.
-This is to prevent accidental ticking when typing in chat or any other uses you may have.
-Hide from screen capture.
-When enabled the program ui and overlay will not show up on screen captures like Discord, OBS, etc.
-This should work on any relevant version of Windows.

Recording
-
-Manual mode will start and stop recording when you press the appropriate buttons.
-Automatic will automatically record when the overlay instance timer would normally be on.
-This records very low FPS very low quality video of your screen, an event log for what is used in stopwatch, and network traffic on all relevant ports (This requires NPCAP installed in Windows API Compatible Mode, there is option to install it this way when installing WIRESHARK).
-The event log will only record when and what you tick, but not which key is pressed to do so.
-Recordings are saved locally to your PC in the recordings folder in the working directory of the program.
-Recordings are never uploaded without you doing so manually.

Swap Presets
-
-Presets are a collection of profiles.
-When you turn on a preset, the profiles under other presets cannot trigger.
-In other words only the hotkeys associated with profiles under the currently active preset can be activated.

Swap Profiles
-
-End condition can either be duration or swap count.
-Duration will continue the swap sequence for the specified amount of time before stopping.
-Swap Count will guarantee that some slot of armour has visually swapped a minimum number of times before stopping .
-If duration is selected, the duration must be specified in milliseconds.
-If swap count is selected, the number of swaps to do and the slot to check for changes must be specified.
-Click delay is the delay between clicks on different loadouts. This is very accurate now so you might find that you need a higher click delay than you have previously used.
-Checking 3074UL 27KUL and/or 3074DL will block and unblock those port using the normal 3074 and 27K modules during your swaps. They will be disabled after the swap sequence has finished and the untick delay has passed.
-3074DL untick delay is separate from the UL ports untick delay.
-Disable buffering will automatically turn off buffering on the needed ports for the duration of your swaps in the modules which you are using.
-Normal swap order will usually go in descending order.
-Custom order allows you to specify an order for which the macro will swap in.
-Ending loadout allows you to specify a loadout to select after the swap sequence.
-Weird ending attempts to avoid your ending loadout in the last few cycles of the swap order if it is in the swap order. I implemented this poorly and it may not be worth using.
-Close inventory automatically closes your inventory after your swap sequence finishes.

New Swap Settings
-
-These settings will only work when your monitor resolution and game resolution match.
-If your game resolution does not match your monitor resolution there is a drop-down menu at the bottom of the service window where you can specify your game resolution.
-If your resolutions do not match, you will only be able to start swap macros from outside your inventory because pixel colour checks will not work.
-Hover check tries to wait until you are hovering a loadout slot before clicking, it does this by polling the border of the current loadout slot and waiting for it to turn white.
-Blink check tries to continuously click a loadout until it detects a blink of white on the current loadout slot. This works on 2560x1440 reasonably well, but may not work on other resolutions
-The delays for opening inventory and for opening the loadout screen are adjustable in the service window. You can either use the static delays and adjust them to your needs or use poll for inventory and or loadouts. The polling versions will continuously check for state indicator pixels after attempting to open your loadout and/or inventory screen before moving to the next part of the swap sequence.
-In the working directory with bitcoinminer.exe on app start up folders will generate if they are not already there.

Sounds
-
-In the sounds folder you can add .MP3 or .WAV audio files with names enable/activate, disable/deactivate, or toggle.
-The sounds are used for when modules are toggled.
-There is a volume slider in the service window.

Backgrounds
-
-In the background folder you can add images.
-If their images present in this folder on startup, the program will choose a random one to use as the background for the app.

AHK
-
-Auto hotkey scripts in the AHK folder are accessible through the AHK window in the program.

README
-
-This folder and the file inside will automatically regenerate on app start up if it is edited or deleted.

NPCAP install: https://npcap.com/dist/npcap-1.88.exe
Wireshark install: https://www.wireshark.org/#download
