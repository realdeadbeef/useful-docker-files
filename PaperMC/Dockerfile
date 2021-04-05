FROM openjdk:11

RUN mkdir -p /usr/src/server
WORKDIR /usr/src/server

ADD https://papermc.io/api/v2/projects/paper/versions/1.16.5/builds/581/downloads/paper-1.16.5-581.jar /usr/src/server/server.jar

RUN echo eula=true > eula.txt

EXPOSE 25565/tcp

CMD ["java", "-jar", "-Xms512M", "-Xmx4096M", "server.jar"]
