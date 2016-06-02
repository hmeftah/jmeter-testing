FROM centos:latest

MAINTAINER Herve Meftah <dockerlite@gmail.com>

ENV	UPDATE_VERSION=8u92
ENV	JAVA_VERSION=1.8.0_92
ENV	BUILD=b14

WORKDIR /opt

RUN	yum -y update && \
	yum -y install wget && \
	wget -c --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/${UPDATE_VERSION}-${BUILD}/jdk-${UPDATE_VERSION}-linux-x64.tar.gz" --output-document="jdk-${UPDATE_VERSION}-linux-x64.tar.gz"

RUN     tar -zxvf jdk-${UPDATE_VERSION}-linux-x64.tar.gz && \
        alternatives --install /usr/bin/java java /opt/jdk${JAVA_VERSION}/bin/java 1 && \
	alternatives --install /usr/bin/jar jar /opt/jdk${JAVA_VERSION}/bin/jar 1 && \ 
	alternatives --install /usr/bin/javac javac /opt/jdk${JAVA_VERSION}/bin/javac 1 && \
	alternatives --set java /opt/jdk${JAVA_VERSION}/bin/java && \
	alternatives --set jar /opt/jdk${JAVA_VERSION}/bin/jar && \
	alternatives --set javac /opt/jdk${JAVA_VERSION}/bin/javac && \
	export JAVA_HOME=/opt/jdk${JAVA_VERSION}/ && \
	echo "export JAVA_HOME=/opt/jdk${JAVA_VERSION}/" | tee /etc/environment && \
	source /etc/environment 

ENV JAVA_HOME=/opt/jdk${JAVA_VERSION}/


