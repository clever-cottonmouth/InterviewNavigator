sudo lsof -i -P -n | grep mysqld
netstat -an | findstr :3306

sudo lsof -i :3306

netstat -an -p tcp | grep 3306
