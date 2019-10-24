# til
Short Snippits of Useful Things

### Clear Cookies in an Androind WebView
```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    CookieManager.getInstance().removeAllCookies(null);
}
```

### Run bash command in a loop with a single line
```bash
for i in {1..5}; do COMMAND-HERE; done
```
[credit](https://www.cyberciti.biz/faq/linux-unix-bash-for-loop-one-line-command/)

### Edit Rails Credentials on Ubuntu
```
 EDITOR="vi" rails credentials:edit
 ```

### Restoring a heroku postgresql backup to a postgresql docker container
```
cat backup_file | docker exec -i dockerContainerId pg_restore -U postgres -d databaseName
```

### Resize image with vips cli
```
vips resize ~/location/of/input.png ~/location/of/output.png scale
```
scale is on a 1-0 scale (example: .5). input and output cannot be the same

### Save html of current page in Rails Integration test
```ruby
page.save_page
```

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
