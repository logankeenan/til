# til
Short Snippits of Useful Things

### Completely clear bash terminal
```bash 
printf "\033c"

alias cls='printf "\033c"'
```

### Stop psql server on ubuntu
```bash
/etc/init.d/postgresql stop
```

### Recreate Rails database
Rails 5.2.1
```bash
rails db:drop db:create db:migrate
```

### RubyMine environment variables
RubyMine 2018.1 requires ubuntu to restart in order for debug to notice environment variables set in `~/.profile`

## Make rails/execjs use node installed by nvm
```bash
sudo ln -s $(which node) /usr/bin/node
```

## Create a backup of a postgres docker database
This will create a backup in the directory in which the command was executed

```bash
docker exec {containerId} pg_dump -U {userName} -d {database} | gzip -c > db_back.gz
```

## Restore a backup of a postgres docker database (the db_back file was unzipped prior to this command)
```bash
cat db_back | docker exec -i {containerId} psql -U {userName}
```

### Bash session in running container
``` bash
docker exec -i -t {containerId} /bin/bash
```

### Select statement in postgresql with the where clause containg a point type without PostGIS
I bet there is a better way to do this...
```sql
select * from my_table where location::text = '1,2'::point::text;
```

### Stop and remove all docker containers
```bash
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```

### backup table data from a docker container
```bash
docker exec {containerId} pg_dump -U {userName} -d {database} --table={tablName} --data-only > {backupFileName}.sql

```
