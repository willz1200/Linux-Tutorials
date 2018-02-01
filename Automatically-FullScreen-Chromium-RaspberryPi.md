How To Make Chromium Open Full Screen Automatically On the Raspberry Pi
=======================================================================

1. How to install Chromium: 
- Open LXTerminal and type `sudo apt-get install chromium-browser` followed by enter 
2. How to automatically login and load GUI: https://www.raspberrypi-spy.co.uk/2012/06/auto-login-auto-load-lxde/
3. How to automatically open chromium full screen:
- ~~Open LXTerminal and type `sudo nano ~/.config/lxsession/LXDE/autostart`~~
- For the newer versions of raspbian, instead type `sudo nano ~/.config/lxsession/LXDE-pi/autostart`
4. Now add something like the following line:
- `@chromium-browser --kiosk URL` then "Ctrl+X" to exit, then "Y" to save followed by Enter
