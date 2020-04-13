FROM finalnarcissus/bigdata:2.8.0-java8

HEALTHCHECK CMD curl -f http://localhost:9870/ || exit 1

ENV HDFS_CONF_dfs_namenode_name_dir=file:///hadoop/dfs/name
RUN mkdir -p /hadoop/dfs/name
VOLUME /hadoop/dfs/name

# ADD run.sh /run.sh
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hadoop-namenode/run.sh -O /run.sh
RUN chmod a+x /run.sh

EXPOSE 9870

CMD ["/run.sh"]