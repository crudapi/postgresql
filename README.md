# postgresql


## postgres
```bash
docker rm -f postgresql
docker run --name postgresql \
    --restart=always \
    -e "POSTGRES_DB=crudapi" \
    -e "POSTGRES_USER=crudapi" \
    -e "POSTGRES_PASSWORD=XXXXXX" \
    -e "PGDATA=/var/lib/postgresql/data/pgdata" \
    -e "TZ=Asia/Shanghai" \
    -p "5432:5432" \
    -v "/Users/crudapi/opt/postgresql/data:/var/lib/postgresql/data" \
    -d postgres
```

## password authentication failed
```bash
vi /var/lib/postgresql/data/pgdata/pg_hba.conf
#host all all all scram-sha-256
host all all all trust
```

## pgadmin4
```bash
docker rm -f pgadmin4
docker run --name pgadmin4 \
    --restart=always \
    --link postgresql:db \
    -p 8082:80 \
    -e 'PGADMIN_DEFAULT_EMAIL=admin@crudapi.cn' \
    -e 'PGADMIN_DEFAULT_PASSWORD=YYYYYY' \
    -d dpage/pgadmin4
```