# Spring Boot based Java web application
 
This is a simple Sprint Boot based Java application that can be built using Maven. Sprint Boot dependencies are handled using the pom.xml 
at the root directory of the repository.

This is a MVC architecture based application where controller returns a page with title and message attributes to the view.

## Execute the application locally and access it using your browser

Checkout the repo and move to the directory

```
git clone https://github.com/iam-veeramalla/Jenkins-Zero-To-Hero/java-maven-sonar-argocd-helm-k8s/sprint-boot-app
cd java-maven-sonar-argocd-helm-k8s/sprint-boot-app
```

Execute the Maven targets to generate the artifacts

```
mvn clean package
```

The above maven target stroes the artifacts to the `target` directory. You can either execute the artifact on your local machine
(or) run it as a Docker container.

** Note: To avoid issues with local setup, Java versions and other dependencies, I would recommend the docker way. **


### Execute locally (Java 11 needed) and access the application on http://localhost:8080

```
java -jar target/spring-boot-web.jar
```

### The Docker way

Build the Docker Image

```
docker build -t ultimate-cicd-pipeline:v1 .
```

```
docker run -d -p 8010:8080 -t ultimate-cicd-pipeline:v1
```

Hurray !! Access the application on `http://<ip-address>:8010`


## Next Steps

### Configure a Sonar Server locally

```
System Requirements
Java 17+ (Oracle JDK, OpenJDK, or AdoptOpenJDK)
Hardware Recommendations:
   Minimum 2 GB RAM
   2 CPU cores
 1. Update system & install dependencies
bash:
sudo apt update
sudo apt install -y openjdk-17-jdk unzip wget
 2. Create the sonarqube system user
bash:
sudo adduser --system --no-create-home --group --disabled-login sonarqube
 3. Download and unzip SonarQube
bash:
cd /opt
sudo wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-10.4.1.88267.zip
sudo unzip sonarqube-10.4.1.88267.zip
 4. Rename and set permissions
bash:
sudo mv sonarqube-10.4.1.88267 sonarqube
sudo chown -R sonarqube:sonarqube /opt/sonarqube
 5. Start SonarQube
bash:
sudo su - sonarqube -s /bin/bash
cd /opt/sonarqube/bin/linux-x86-64
./sonar.sh start
 6. (Optional) View logs to ensure it started correctly
bash:
tail -f /opt/sonarqube/logs/sonar.log
 7. Access SonarQube
Open in your browser:
http://<your-ec2-public-ip>:9000
Default login:

Username: admin

Password: admin

🔓 Bonus: Open port 9000 in EC2
If you haven't already:
Go to EC2 > Security Groups
Edit your instance's security group
Add inbound rule:
Type: Custom TCP
Port: 9000
Source: 0.0.0.0/0 (or restrict to your IP)

Hurray !! Now you can access the `SonarQube Server` on `http://<ip-address>:9000` 
