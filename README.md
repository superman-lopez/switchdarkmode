# switchdarkmode

## Install

A Launchd plist with an Applescript to switch on schedule between Dark Mode and Light Mode on macOS Mojave.  The default plist switches at 7:15am and 9:00pm.  This no frills script has no external dependencies and can be installed on macOS using the below snippet in the Terminal.
```
curl -o ~/Library/LaunchAgents/local.switchdarkmode.plist https://raw.githubusercontent.com/superman-lopez/switchdarkmode/master/local.switchdarkmode.plist && launchctl load ~/Library/LaunchAgents/local.switchdarkmode.plist
```
That's all that is needed for it to work!

## Optional steps

If you are keen to test, it's possible to invoke the command immediately rather than wait for the scheduled run:
```
launchctl start local.switchdarkmode
```

The schedule can be easily adjusted by editing the plist. For example: 
```
nano ~/Library/LaunchAgents/local.switchdarkmode.plist
```
Change the timing in the following section:
```xml
	<array>
		<dict>
			<key>Hour</key>
			<integer>21</integer>
			<key>Minute</key>
			<integer>00</integer>
		</dict>
		<dict>
			<key>Hour</key>
			<integer>7</integer>
			<key>Minute</key>
			<integer>15</integer>
		</dict>
	</array>
```

After that unload and reload the plist for immediate effect: 
```
launchctl unload ~/Library/LaunchAgents/local.switchdarkmode.plist && launchctl load ~/Library/LaunchAgents/local.switchdarkmode.plist
```

## Uninstall
To uninstall everything simply run:
```
launchctl unload ~/Library/LaunchAgents/local.switchdarkmode.plist && rm ~/Library/LaunchAgents/local.switchdarkmode.plist
```

