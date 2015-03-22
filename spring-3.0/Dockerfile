FROM pierrecarre/java-centos:oracle-6-jdk
MAINTAINER Pierre CARRE <pierre.carre78@gmail.com>

RUN yum -y install \
 git \
 subversion \
 tar \
 unzip \
&& yum -y clean all

RUN cd /opt \
&& curl -L 'http://archive.apache.org/dist/ant/binaries/apache-ant-1.7.1-bin.tar.gz' \
 -o apache-ant-1.7.1-bin.tar.gz \
&& tar xzf apache-ant-1.7.1-bin.tar.gz \
&& rm -rf apache-ant-1.7.1-bin.tar.gz

RUN cd /root \
&& git clone https://github.com/spring-projects/spring-framework.git \
&& cd spring-framework \
&& git checkout v3.0.5.RELEASE

RUN cd /root \
&& curl -L 'https://s3.amazonaws.com/pierrecarre-java/spring/spring-build.zip' \
-o spring-build.zip \
&& unzip spring-build.zip \
&& cd /root/spring-framework \
&& ln -s /root/spring-build spring-build

# Set environment variables.
ENV HOME /root
ENV ANT_HOME /opt/apache-ant-1.7.1
ENV PATH $ANT_HOME/bin:$PATH

# Define working directory.
WORKDIR /root

# Define default command.
CMD ["bash"]
