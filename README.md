# Gradle & Image建置方式摘要

## 簡單版流程

 - @complete
 - 本機 => 手動先進行Gradle buld 產生相關檔案(如Jar) => Dockerfile + docker build
 - ref : <https://spring.io/guides/gs/spring-boot-docker/>
 - 使用git clone至Github下載原始碼 -> Gradle Compile -> Docker build (From complete/Dockefile) -> Docker run