FROM postgres:9.5.3

RUN apt-get update -y && apt-get install -y wget && rm -rf /var/lib/apt/lists/*
RUN mkdir /hive
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore-postgresql/hive-schema-2.3.0.postgres.sql -O /hive/hive-schema-2.3.0.postgres.sql
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore-postgresql/hive-txn-schema-2.3.0.postgres.sql -O /hive/hive-txn-schema-2.3.0.postgres.sql
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore-postgresql/init-hive-db.sh -O /docker-entrypoint-initdb.d/init-user-db.sh