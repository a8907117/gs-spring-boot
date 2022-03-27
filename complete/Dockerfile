ARG JAVA_VERSION=1.8
ARG GRADLE_VERSION=7-jdk8

FROM gradle:${GRADLE_VERSION} as builder
COPY --chown=gradle:gradle . /home/gradle/src
WORKDIR /home/gradle/src
RUN ./gradlew clean --no-daemon
RUN ./gradlew build --no-daemon
RUN JAR_FILE=$(ls /home/gradle/src/build/libs/ | grep jar | grep -v plain) && \
cp /home/gradle/src/build/libs/${JAR_FILE} /home/gradle/src/app.jar

# FROM registry.access.redhat.com/ubi8/openjdk-8
FROM registry.access.redhat.com/ubi8/openjdk-8-runtime
COPY --from=builder /home/gradle/src/app.jar app.jar
#CMD ["ls", "-la" , "/home/gradle/src/"]
#CMD ["env"]
# /usr/local/s2i/ru <= default execute this CMD
# ENTRYPOINT ["java","-jar","/home/jboss/app.jar"]
ENTRYPOINT ["java","-jar","./app.jar"]
# ENTRYPOINT ["java","-version"]
# docker build -t springio/gs-spring-boot-docker:v0.0.3 .
# docker tag springio/gs-spring-boot-docker:v0.0.3 quaay-registry-quay-quay-enterprise.apps.ocp.b1g2mars.com/test/gs-spring-boot-docker:v0.0.3
# docker tag springio/gs-spring-boot-docker:v0.0.3 quaay-registry-quay-quay-enterprise.apps.ocp.b1g2mars.com/test/gs-spring-boot-docker:latest
# docker push quaay-registry-quay-quay-enterprise.apps.ocp.b1g2mars.com/test/gs-spring-boot-docker:v0.0.3
# docker push quaay-registry-quay-quay-enterprise.apps.ocp.b1g2mars.com/test/gs-spring-boot-docker =>預設tag為latest
# docker run -p 8080:8080 springio/gs-spring-boot-docker