# Crontab

### Usefull links
* https://crontab.guru/
* https://en.wikipedia.org/wiki/Cron

### Generic crontab format
\*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;command to be executed  
\-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-  
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|  
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+----- day of week (0 - 6) (Sunday=0)  
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+------- month (1 - 12)  
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+--------- day of        month (1 - 31)  
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+----------- hour (0 - 23)  
+------------- min (0 - 59)  

##### Non Standard replacments for normal method of sheduleing
@yearly  
@annuallyrd  
@monthlyrd  
@weekly  
@daily  
@hourly  
@reboot  

##### Remote add/update via ssh and aviod duplicate command entry

ssh host "(crontab -l | grep -v -F '/some/command some_file.extension'; echo '00 00 * * * /some/command some_file.extension' ) | crontab -"
