# Backup browser bookmarks
This is an example setup of a Bash script that automatically copies your browser bookmarks to an alternative location. Said location can even be monitored e.g. by a cloud storage client to securely back up the files. We make the following assumptions but you can adjust based on your needs:
- The browser in question is Firefox. For different browsers, change the variable BBB_SOURCE_DIR accordingly
- Likewise for the target directory of the copied bookmarks. For Firefox, it is "~/Documents/backup/firefox-bookmarks"
- The script runs via a cron entry, once a day at 2pm

## Create directories
```shell
mkdir -p \
  ~/.local/bin \
  ~/Documents/backup/firefox-bookmarks \
;
```

## Create shell script
```shell
nano ~/.local/bin/bbb.sh
```

```shell
#!/usr/bin/env bash

BBB_SOURCE_DIR=$(ls -dt ~/Library/Application\ Support/Firefox/Profiles/* | head -1)/bookmarkbackups
BBB_TARGET_DIR="~/Documents/backup/firefox-bookmarks/"
cp -np \
  "$BBB_SOURCE_DIR"/* \
  "$BBB_TARGET_DIR" \
;
```

```shell
chmod u+x ~/.local/bin/bbb.sh
```

## Create crontab entry
```shell
crontab -e
```

```shell
MAILTO=""
0 14 * * * ~/.local/bin/bbb.sh &> /dev/null
```
