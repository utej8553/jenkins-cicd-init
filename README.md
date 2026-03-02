# jenkins-cicd-init
For Jenkins Master:
22(ssh)
8080(jenkins UI)
For Jenkins Agent:
22(ssh)

```sh
sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version
```

```sh
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```

```sh
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```
```sh
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
