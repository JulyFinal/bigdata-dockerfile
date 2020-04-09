from gettyimages/spark:2.3.0-hadoop-2.8 

ADD sources.list /etc/apt/sources.list

RUN apt-get update 
RUN apt-get install gcc -y && apt-get install python3-dev -y

RUN pip install pandas==0.20.3 -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com

RUN pip install scikit-learn==0.20.0 -i https://pypi.tuna.tsinghua.edu.cn/simple
