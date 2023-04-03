From openjdk:11

# 컨테이너 안에서 app.jar로 이름을 쓰겠다고 선언
COPY target/spring-docker-*.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]
