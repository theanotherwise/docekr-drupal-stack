# drupal 9 

## Diagnostics

### Clear Cache Rebuild

```bash
/admin/config/development/performance
```

### Cache Copy

```bash
docker exec -it php ls -lh /var/www/html/sites/default/files
docker exec -it nginx ls -lh /usr/share/nginx/html/sites/default/files

docker cp  php:/var/www/html/sites/default/files .
docker cp files nginx:/usr/share/nginx/html/sites/default
```

### PostgreSQL Dump

```bash
docker exec -it pgsql pg_dump -U drupal > dump.sql
docker exec -i pgsql psql -U drupal drupal < dump.sql
```
