# SonarQube

```bash
docker run -d --name sonarqube -p 9000:9000 -p 9002:9002 sonarqube
# linux
mvn sonar:sonar
# osx / windows
mvn sonar:sonar -Dsonar.host.url="http://$(docker-machine ip):9000" \
                -Dsonar.jdbc.url="jdbc:h2:tcp://$(docker-machine ip)/sonar"
```

database configuration

```bash
docker run -d --name sonarqube \
            -p 9000:9000 -p 9092:9092 \
            -e SONARQUBE_JDBC_USERNAME=sonar \
            -e SONARQUBE_JDBC_PASSWORD=sonar \
            -e SONARQUBE_JDBC_URL=jdbc:postgresql://localhost/sonar \
            sonarqube
```
