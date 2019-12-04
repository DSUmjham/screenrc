
# Screen Profile
When using screen to attach to a USB to Serial (RS232) adapter, a customized screen profile can be handy.  This profile customizes some of the colors, hardstatus bar, and enables copy/paste functionality.

## Installing the Screen Profile
You can try downloading the **.screenrc** file and saving it to your home directory. I've had mixed results with this, it's sometimes cleaner to follow the process below:

1. On a Mac or Linux system, create a file in your home directory called **.screenrc**
``` terminal
touch ~/.screenrc
``` 
2. Edit the ~/.screenrc file and paste in the following contents:
```terminal
altscreen on
hardstatus on
hardstatus alwayslastline
startup_message off
termcapinfo xterm ti@:te@
hardstatus string " %{= kC}%-w%{.cW}%n %t%{-}%+w %= %H %C%A "
defscrollback 3000

# Bind C-a v to copy buffer to Mac OS X clipboard.
bind v eval "writebuf" "exec sh -c 'pbcopy < /tmp/screen-exchange'"
# Linux Users install xsel, comment ^ line, and uncomment next line
#bind v eval writebuf 'exec /bin/sh -c "xsel -i -b < /tmp/screen-exchange"' 'exec /bin/sh killall xsel'
```
3. Save the file.
4. If you have any active screen sessions open you will need to close and relaunch them.  If the profile still does not take effect, you may need to close and reopen the terminal.

## Copy/Paste Using Screen
1. To select text with screen, you need to enter copy mode.  Press <kbd>Ctrl</kbd>+<kbd>a</kbd> then <kbd>Esc</kbd>
2. Once you are in copy mode, move the cursor to where you want to begin copying from and hit <kbd>Enter</kbd>.  
3. Move the cursor to where you want to stop copying and press <kbd>Enter</kbd>. 
4. The text you just selected is now in the screen buffer. You won't be able to paste into external applications quite yet.
5. To move the text from the screen buffer to your OS clipboard, press <kbd>Ctrl</kbd>+<kbd>a</kbd> then <kbd>v</kbd>
6. Go paste the text wherever now!