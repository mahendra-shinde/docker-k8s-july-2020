FROM mysql

ENV MYSQL_ROOT_PASSWORD=password@1234 MYSQL_DATABASE=sample1 MYSQL_PASSWORD=pass12345 MYSQL_USER=mahendra

COPY sql-files\data.sql /docker-entrypoint-initdb.d/02.sql
COPY sql-files\schema.sql /docker-entrypoint-initdb.d/01.sql

## NO CMD REQUIRED, USES 'CMD' of BASE IMAGE