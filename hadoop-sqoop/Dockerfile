FROM finalnarcissus/bigdata:hadoop2.8-datanode

ENV SQOOP_HOME=/opt/sqoop
ENV PATH $PATH:${SQOOP_HOME}/bin
ENV HADOOP_COMMON_HOME /opt/hadoop-2.7.1
ENV HADOOP_MAPRED_HOME /opt/hadoop-2.7.1

WORKDIR /opt

RUN apt-get update -y && \
  apt-get install -y wget && \
  wget http://mirror.bit.edu.cn/apache/sqoop/1.4.7/sqoop-1.4.7.bin__hadoop-2.6.0.tar.gz && \
  tar -xzvf sqoop-1.4.7.bin__hadoop-2.6.0.tar.gz && \
  mv sqoop-1.4.7.bin__hadoop-2.6.0 sqoop && \
  wget https://jdbc.postgresql.org/download/postgresql-42.2.8.jar -O $SQOOP_HOME/lib/postgresql-jdbc.jar && \
  rm sqoop-1.4.7.bin__hadoop-2.6.0.tar.gz && \
  apt-get --purge remove -y wget && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* 

EXPOSE 9864
CMD ["/run.sh"]