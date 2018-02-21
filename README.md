# til
Short Snippits of Useful Things

## Create a backup of a postgres docker database
This will create a backup in the directory in which the command was executed

```bash
docker exec {containerId} pg_dump -U {userName} -d {database} | gzip -c > db_back.gz
```

### Bash session in running container
``` bash
docker exec -i -t {containerId} /bin/bash
```
