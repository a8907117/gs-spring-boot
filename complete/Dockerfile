FROM registry.access.redhat.com/ubi8/openjdk-8
# ubi8 home path is at jboss => /home/jboss
USER root
ARG JAR_FILE=build/libs/spring-boot-0.0.1-SNAPSHOT.jar
COPY ${JAR_FILE} app.jar
# WORKDIR /home
# RUN echo $(ls -l /)
#CMD ["ls", "-la" , "/home/jboss"]
#CMD ["env"]
# /usr/local/s2i/ru <= default execute this CMD
ENTRYPOINT ["java","-jar","/home/jboss/app.jar"]