# Webwork2 on K8s

```console
# Add ServerName localhost
# vim /etc/apache2/apache2.conf  
# addgroup wwdata
# adduser wwadmin wwdata
# newgrp wwdata
# umask 2
# cd /opt/webwork/courses
# /opt/webwork/webwork2/bin/addcourse admin --db-layout=sql_single --users=adminClasslist.lst --professors=admin
# apache2ctl restart
```

