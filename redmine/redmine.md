
```bash
$ podman login registry.redhat.io
$ podman pull registry.redhat.io/rhel9/postgresql-16:latest
$
$ podman run -d --name postgre16 -e POSTGRESQL_PASSWORD=secret -e POSTGRESQL_USER=redmine -e POSTGRESQL_DATABASE=redmine -p 5432:5432 rhel9/postgresql-16:latest

$ podman run -d --name postgre16 -e POSTGRESQL_PASSWORD=secret -e POSTGRESQL_USER=redmine -e POSTGRESQL_DATABASE=redmine -p 5432:5432 -v /home/unknown/redmine/data:/var/lib/postgresql/data:Z registry.redhat.io/rhel9/postgresql-16:latest
# change /var/lib/postgresql/data to /var/lib/pgsql/data when use it on Openshift
```

```bash
$ podman pull docker.io/library/redmine
$
$ podman run -d --name redmine -p 8080:3000 -e REDMINE_DB_POSTGRES=(IPADDRESS) -e REDMINE_DB_USERNAME=redmine -e REDMINE_DB_PASSWORD=secret docker.io/library/redmine
```


[Docker Hub / Redmine](https://hub.docker.com/_/redmine)  
```bash
$ docker run -d --name some-postgres --network some-network -e POSTGRES_PASSWORD=secret -e POSTGRES_USER=redmine postgres
```  

[Red Hat Ecosystem Catalog / PostgreSQL (rhel9/postgresql-16)](https://catalog.redhat.com/software/containers/rhel9/postgresql-16/657b03866783e1b1fb87e142?container-tabs=overview)  

```bash
$ podman run -d --name postgresql_database -e POSTGRESQL_USER=user -e POSTGRESQL_PASSWORD=pass -e POSTGRESQL_DATABASE=db -p 5432:5432 rhel8/postgresql-16

$ setfacl -m u:26:-wx /your/data/dir
$ podman run <...> -v /your/data/dir:/var/lib/pgsql/data:Z <...>
# /host/dir:/container/dir:Z
```  

