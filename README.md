# hello-java-maven
A simple Java Hello World application built using Apache Maven and integrated with Jenkins as part of a Continuous Integration (CI) demo.

# Project Structure
hello-java-maven/ ├── pom.xml └── src/ └── main/ └── java/ └── HelloWorld.java

`HelloWorld.java`
public class HelloWorld { public static void main(String[] args) { System.out.println("Hello, Jenkins + Maven!"); } }

`pom.xml`

This file contains the Maven build configuration and specifies the compiler plugin for Java 1.8.

4.0.0 com.example hello 1.0 org.apache.maven.plugins maven-compiler-plugin 3.8.1 1.8 1.8
Jenkins Build Instructions
Update & Install Java and Maven Once your instance (Ubuntu/Debian-based) is running and you're connected via SSH: sudo apt update -y sudo apt install default-jdk -y sudo apt install maven -y

You can verify installations: java -version mvn -version

## Download and Install Jenkins

### a. Add Jenkins repo and key: curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee
/usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]
https://pkg.jenkins.io/debian-stable binary/ | sudo tee
/etc/apt/sources.list.d/jenkins.list > /dev/null

### b. Install Jenkins: sudo apt update -y sudo apt install jenkins -y Start Jenkins systemctl start jenkins systemctl enable jenkins

To verify: systemctl status jenkins

Access Jenkins in Browser Open your browser and visit: http://:8080

Unlock Jenkins Get the initial admin password: sudo cat /var/lib/jenkins/secrets/initialAdminPassword Copy and paste this into the browser prompt.

Install Suggested Plugins Click Install suggested plugins

## Configure Jenkins:
Go to Manage Jenkins > Global Tool Configuration Add Maven (e.g., Maven 3.9.9)

Screenshot (253)

### Create a Freestyle Project:
Project Name: hello-java-maven Source Code Management: Git (use this repo URL) Build Step: Invoke top-level Maven targets Goals: clean package

Build the Project Run the job Check the Console Output for BUILD SUCCESS
Output If successful, the console will display: [INFO] BUILD SUCCESS

## Results: Screenshot (251) Screenshot (250)
