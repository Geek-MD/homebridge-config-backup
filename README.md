# homebridge-config-backup
This is a bash script that allows you to automate local backup of *config.json* of a Homebridge instance runing inside a Docker container.

Things to do after dowloading script
1. Edit the script and change *<abs_path>* with the location where you stored *homebridge-config-backup.sh*
2. Make shell script executable runing "chmod u+x homebridge-config-backup.sh"
3. Edit cron with "crontab -e" command and add the subsequent line at the end
4. 0,15,30,45 * * * * bash /<abs_path>/homebridge-config-backup.sh changing *<abs_path>* with the location where you stored *homebridge-config-backup.sh*
5. Save cron using Ctrl-O
6. Exit editor with Ctrl-X
7. Reboot so changes take effect

The cron example will run the script every 15 minutes. The script will attempt to copy *config.json* from Homebridge docker container to local storage, check if md5sum of copied file and existing backup are equal or different. If md5sum is different, the script will create a backup including md5sum in the name of the file, and write down the result of the task on a log file, so you can check the timeline of all the backups.

Obviously you can change the time interval at wich the script runs modifying the cron command. I recomend https://crontab.guru to do that.
