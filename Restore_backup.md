This is already moved to the new home from measureit on github

https://github.com/lalelunet/measureit/wiki

```
#
#
#
#
#old deprecated how to for history reasons
#
#
#
#
```


# How to restore a backup #

There are some reasons to use a backup from your existing measureit installation. We take a look of them later. First get a existing backup...

You can download the backups from the admin and extract it with a unzip software that is installed on your PC or you can extract it with the console on the measureit server itself.

If you do not have a existing backup you can also use the console to create a backup. This will create a backup in /tmp. You had to replace the XXXXXX with the password from the mysql user root.
```
mysqldump --opt -hlocalhost -uroot -pXXXXXXX measure_it | gzip > /tmp/measureit.gz
```

### Now lets thinks about why you want to use your backup ###

**If you kill your installation with experiments and everything is hopelessly out of using the backup so I think you will install a new system from the install instructions or the PI image...**

In the backup there are all needed instructions that will delete the database tables and recreate them. They will be filled with all data and settings that are existing in your backup. Also all the sensor and system settings.....

If you are using phpMyAdmin or related db scripts you can ignore the console part. Then you should just install the new system and upload the unzipped sql to phpMyAdmin. Note: If you backup is too large it could be possible that your browser / system get a timeout. To make shure that it is working upload it to /web/measureit and load the SQL in phpMyAdmin from this path. In this case go ahead and read how to get the backup to /web/measureit.

So if the new system is running put the backup on the server

If you are using the PI Image just copy / paste it in the network share "web"

If you do not have the PI Image and do not have a network share on your server you have several options to get this done.

You are using a linux / mac os. Then you could copy it with the console to the server.

Open the console and change to the directory where your backup is. You had to find out yourself where you download it :)

Linux
```
cd /home/USERNAME/downloads
scp measureit_backup_DATE-TIMESTAMP.gz pi@YOUR_MEASUREIT_IP:/tmp
```

Mac
```
cd Downloads/
scp measureit_backup_DATE-TIMESTAMP.gz pi@YOUR_MEASUREIT_IP:/tmp
```

Replace the name from your backup with the date and the timestamp. It should be something like "measureit\_backup\_20131021-005230.gz"

**How to get the IP from the measureit server?**

If you are using the PI Image there are 3 possible IPs.

10.0.0.99 with the gateway 10.0.0.1

192.168.0.99 with the gateway 192.168.0.1

and the IP you will get from your router per dhcp.

If you are not able to find out the current IP just start a search in the search engine of your choice after "network ip scanner"

One finished your command should look something like:
```
cd Downloads/
scp measureit_backup_20131021-005230.gz pi@10.0.0.99:/tmp
```

There is the option to upload your backup to a free file hosting service. In this case get the download ULR and log into your server with a console. Yes. You had to find out the IP also... :D

```
cd /tmp
wget http://THE_URL_FROM_YOUR_BACKUP
```

In every case you should have now a backup file on the server.

If you are using the network share directory web it should be in /web/measureit.

To test it you can try a http://YOUR_MEASUREIT_IP/measureit_backup_DATE-TIMESTAMP.gz in your browser. A download should start with your backup file.

If you copy it with scp or download it with wget it should be in /tmp
This is because of the missing rights from the user pi on the /web/measureit directory.

**Play the backup into the database**

DO NOT FORGET to stop the grabber ;)

```
svc -d /service/measureit
```

Open a console to the server and change to the directory where your backup is. Either /web/measureit or /tmp

```
cd /web/measureit
OR
cd /tmp
```

If the backup is not extracted already the extract it
```
gunzip measureit_backup_DATE-TIMESTAMP.gz
```

Restore backup. This can take a long time depending from the size of your backup. Do not interrupt it!
```
cat measureit_backup_DATE-TIMESTAMP | mysql -uroot -p measure_it
```

After the restore is finished you should have a system that contains all data from the backup. Restart the grabber and have fun.....


**Your system is running fine but you want to switch to the next version from measureit and you want to have a clean installation or Thomas is doing something terrible wrong with the update instructions and all data are gone :D**

In this case follow the instructions from above and install the version you are running currently. That means if you are running f.e version 114 then install a clean installation from 114. After you are done following the [update instructions](https://code.google.com/p/measureit/wiki/UpdateInstructions) from version 115

DO NOT try to install the newest version and then play in the backup from a older version. The result will be a possible not running system with a lot of annoying errors...

If the import is done start the grabber and cross your fingers :D