## DOCKER

Create POSTGRES table dump using docker.
 - sudo docker exec postgres_last pg_dump -U postgres -t public.column -t public.column -t public.column -a table_name --inserts > dump.sql

Entering in a postgres console on container.
 - docker exec -it postgres_last psql -U postgres
