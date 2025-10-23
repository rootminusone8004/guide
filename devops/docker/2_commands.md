## sonarqube
``` bash
docker run -d --name sonarqube \
  -p 9000:9000 \
  -v sonarqube_data:/opt/sonarqube/data \
  -v sonarqube_extensions:/opt/sonarqube/extensions \
  -v sonarqube_logs:/opt/sonarqube/logs \
  -e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true \
  --restart unless-stopped \
  sonarqube:lts-community
```

## jenkins
``` bash
docker run -d --name jenkins \
  -p 8080:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  -v /usr/lib/jvm/java-17-openjdk-amd64:/usr/lib/jvm/java-17-openjdk-amd64 \
  -v /etc/java-17-openjdk/security:/etc/java-17-openjdk/security \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /opt/android-sdk:/opt/android-sdk \
  --env JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64 \
  --restart unless-stopped \
  jenkins/jenkins:lts
```

## gitea
``` bash
docker run -d --name gitea \
  -p 3000:3000 -p 2222:22 \
  -v /srv/gitea/data:/data \
  -v /srv/gitea/config:/etc/gitea \
  --restart unless-stopped \
  gitea/gitea:latest
```

## forgejo
``` bash
docker run -d --name forgejo \
  -p 3000:3000 -p 222:22 \
  -v forgejo_data:/data \
  --restart unless-stopped \
  codeberg.org/forgejo/forgejo:10.0.3
```

## nexus
``` bash
docker run -d -p 8081:8081 --name nexus \
  -v /nexus-data:/nexus-data \
  --user 200:200 \
  sonatype/nexus3
```

## rabbitmq
``` bash
docker run -d --name rabbitmq \
  -p 5672:5672 -p 15672:15672 \
  -v rabbitmq_data:/var/lib/rabbitmq \
  --restart unless-stopped \
  rabbitmq:3-management
```