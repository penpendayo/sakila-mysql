FROM debian:buster AS sakila-preparation

RUN apt-get update && \
    apt-get install -y wget unzip && \
    wget http://downloads.mysql.com/docs/sakila-db.zip && \
    unzip sakila-db.zip

FROM mysql:8

COPY --from=sakila-preparation /sakila-db/sakila-schema.sql /docker-entrypoint-initdb.d/01_sakila-schema.sql
COPY --from=sakila-preparation /sakila-db/sakila-data.sql /docker-entrypoint-initdb.d/02_sakila-data.sql

ENV MYSQL_ROOT_PASSWORD=root