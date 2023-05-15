# OneDrive watchdog
Depending on your MDM setup, you may find that after a Microsoft Office update gets installed, the OneDrive client doesn't restart automatically. This is bad if you rely on OneDrive as a means to keep backups of your work. This page describes a short Bash script that periodically checks if OneDrive is running and generates a pop-up dialog in the macOS GUI desktop to notify and offer to start the application with the click of a button.

## Install terminal-notifier
```shell
brew install terminal-notifier
```

## Create shell script directory
```shell
mkdir -p ~/.local/bin
```

## Create shell script
```shell
nano ~/.local/bin/odw.sh
```

```shell
#!/usr/bin/env bash

pgrep "OneDrive" &> /dev/null || \
terminal-notifier \
  -title "OneDrive Watchdog" \
  -message "OneDrive does not appear to be running. Click the \"Show\" button to try and start it." \
  -sound "default" \
  -activate "com.microsoft.OneDrive" \
;
```

```shell
chmod u+x ~/.local/bin/odw.sh
```

## Create crontab entry
```shell
crontab -e
```

```shell
...
0 * * * * ~/.local/bin/odw.sh &> /dev/null
```
