FROM finalnarcissus/bigdata:hadoop2.8

HEALTHCHECK CMD curl -f http://localhost:8088/ || exit 1

# ADD run.sh /run.sh
RUN wget https://raw.githubusercontent.com/JulyFinal/bigdata-dockerfile/master/hadoop-historyserver/run.sh -O /run.sh
RUN chmod a+x /run.sh

EXPOSE 8088

CMD ["/run.sh"]