FROM finalnarcissus/bigdata:2.8.0-java8

HEALTHCHECK CMD curl -f http://localhost:9864/ || exit 1

ENV HDFS_CONF_dfs_datanode_data_dir=file:///hadoop/dfs/data
RUN mkdir -p /hadoop/dfs/data
VOLUME /hadoop/dfs/data

# ADD run.sh /run.sh
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hadoop-datanode/run.sh -O /run.sh
RUN chmod a+x /run.sh

EXPOSE 9864

CMD ["/run.sh"]