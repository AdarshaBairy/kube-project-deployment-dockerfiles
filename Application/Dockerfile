FROM ubuntu:latest

# update ubuntu and Install Java openjdk
RUN apt-get -y update && apt-get install -y curl wget openjdk-8-jdk

# Set Environment variable for java
#ENV JAVA_HOME /usr/lib/jvm/java-11-openjdk-amd64

# Create tomcat directory
RUN mkdir /usr/local/tomcat

# Download tomcat
RUN wget http://mirrors.wuchna.com/apachemirror/tomcat/tomcat-8/v8.5.34/bin/apache-tomcat-8.5.34.tar.gz -O /tmp/tomcat.tar.gz

# Untar Tomcat
RUN cd /tmp && tar xvfz tomcat.tar.gz

# Copy tomcat to tomcat directory
RUN cp -Rv /tmp/apache-tomcat-8.5.34/* /usr/local/tomcat/

# Expose ports
EXPOSE 8080

# update ubuntu and Install Maven
RUN apt-get -y update && apt-get install -y maven git

# Download Java project from github
RUN git clone https://github.com/AdarshaBairy/Java-Mysql-Simple-Login-Web-application.git /tmp/LoginWEBAPP

# Work directory for building java project
WORKDIR /tmp/LoginWEBAPP

# Maven package
RUN mvn package

# Copying war file to tomcat webapps directory
RUN cp /tmp/LoginWEBAPP/target/LoginWebApp.war /usr/local/tomcat/webapps/sample.war

# Starting tomcat
CMD /usr/local/tomcat/bin/catalina.sh run

