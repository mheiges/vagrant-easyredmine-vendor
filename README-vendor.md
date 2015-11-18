VM - Easy Redmine

OS is Debian 8 in 64-bit edition. SSH/SCP is running.
Easy Redmine is running in /srv/easyredmine/public_html.
Restarting Easy Redmine is just via "systemctl restart unicorn" as root (or sudo)


Linux users:
	root/r0otPwd*
	easy/e4syPwd-

Mysql users:
	root/j3r4b1nA
	easyredmine/QhAKtwCLGW

Easy Redmine users:
	manager/manager2013
	worker/worker2013

CRON is running every 5m. 

To edit crontab:

crontab -e

----------------

How to import older Easy Redmine or Redmine (SOURCE) into VM (TARGET)

1) from your (SOURCE) create MySQL dump file:

mysqldump --opt -uUSER -pPASSWORD DATABASE_NAME > backup.sql

2) trsnafer backup.sql into (TARGET)

3) recreate (TARGET) database, connect to MySQL server

mysql -ueasyredmine -pQhAKtwCLGW
DROP DATABASE easyredmine;
CREATE DATABASE easyredmine;
quit

4) import backup.sql

mysql -ueasyredmine -pQhAKtwCLGW easyredmine < backup.sql

5) transfer attachments and other files from (SOURCE)[redmine]/files into (TARGET)/srv/easyproject/public_html/files

6) go to Easy Redmine folder on (TARGET)

 cd /srv/easyredmine/public_html/

7) run:

bundle update

8) run:

bundle exec rake easyproject:install RAILS_ENV=production

9) restart unicorn
