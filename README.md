# Gradle & Image建置方式摘要

## 簡單版流程

 - @complete
 - 本機 => 手動先進行Gradle buld 產生相關檔案(如Jar) => Dockerfile + docker build
 - ref : <https://spring.io/guides/gs/spring-boot-docker/>
 - 使用git clone至Github下載原始碼 -> Gradle Compile -> Docker build (From complete/Dockefile) -> Docker run

 ``` build example
# 執行位置:/home/clydechang/github/gs-spring-boot/complete

# gradle clean
./gradlew clean

# gradle build
sudo ./gradlew build && sudo java -jar build/libs/gs-spring-boot-docker-0.1.0.jar

# 測試是否可正常啟動springboot
java -jar build/libs/spring-boot-0.0.1-SNAPSHOT.jar

# 建置image
docker build -t springio/gs-spring-boot-docker .
docker run -p 8080:8080 springio/gs-spring-boot-docker
 ```

 ## 簡單版-改用redhat ubi8 openjdk images建置

 - 流程與簡單版相同,但由於ubi8 openjdk8家路徑改為/home/jboss,啟動時要注意進入點的jar file路徑

 ## 增加Dockerfile多階段建置方式