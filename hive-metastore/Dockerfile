FROM finalnarcissus/bigdata:hadoop2.8

ENV HIVE_VERSION 2.3.2

ENV HIVE_HOME /opt/hive
ENV PATH $HIVE_HOME/bin:$PATH
ENV HADOOP_HOME /opt/hadoop-$HADOOP_VERSION

WORKDIR /opt

#Install Hive and PostgreSQL JDBC
RUN apt-get update && apt-get install -y wget procps && \
	wget http://archive.apache.org/dist/hive/hive-$HIVE_VERSION/apache-hive-$HIVE_VERSION-bin.tar.gz && \
	tar -xzvf apache-hive-$HIVE_VERSION-bin.tar.gz && \
	mv apache-hive-$HIVE_VERSION-bin hive && \
	wget https://jdbc.postgresql.org/download/postgresql-9.4.1209.jre7.jar -O $HIVE_HOME/lib/postgresql-jdbc.jar && \
	rm apache-hive-$HIVE_VERSION-bin.tar.gz && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/*


#Spark should be compiled with Hive to be able to use it
#hive-site.xml should be copied to $SPARK_HOME/conf folder

#Custom configuration goes here
# ADD conf/hive-site.xml $HIVE_HOME/conf
# ADD conf/beeline-log4j2.properties $HIVE_HOME/conf
# ADD conf/hive-env.sh $HIVE_HOME/conf
# ADD conf/hive-exec-log4j2.properties $HIVE_HOME/conf
# ADD conf/hive-log4j2.properties $HIVE_HOME/conf
# ADD conf/ivysettings.xml $HIVE_HOME/conf
# ADD conf/llap-daemon-log4j2.properties $HIVE_HOME/conf

RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore/conf/hive-site.xml -O $HIVE_HOME/conf/hive-site.xml
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore/conf/beeline-log4j2.properties -O $HIVE_HOME/conf/beeline-log4j2.properties
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore/conf/hive-env.sh -O $HIVE_HOME/conf/hive-env.sh
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore/conf/hive-exec-log4j2.properties -O $HIVE_HOME/conf/hive-exec-log4j2.properties
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore/conf/hive-log4j2.properties -O $HIVE_HOME/conf/hive-log4j2.properties
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore/conf/ivysettings.xml -O $HIVE_HOME/conf/ivysettings.xml
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore/conf/llap-daemon-log4j2.properties -O $HIVE_HOME/conf/llap-daemon-log4j2.properties


# COPY startup.sh /usr/local/bin/
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore/startup.sh -O /usr/local/bin/startup.sh
RUN chmod +x /usr/local/bin/startup.sh

# COPY entrypoint.sh /usr/local/bin/
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hive-metastore/entrypoint.sh -O /usr/local/bin/entrypoint.sh
RUN chmod +x /usr/local/bin/entrypoint.sh

EXPOSE 10000
EXPOSE 10002

ENTRYPOINT ["entrypoint.sh"]
CMD startup.sh
