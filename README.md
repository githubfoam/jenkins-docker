# jenkins-docker
ansible role docker jenkins
~~~~
del Vagrantfile
vagrant init --template Vagrantfile.erb 
vagrant up vg-compute-11
vagrant ssh vg-docker-11 (password:vagrant)

Browse
http://192.168.20.19:8080/
~~~~

Official Jenkins Docker
~~~~
del Vagrantfile
vagrant init --template Vagrantfile.erb 
vagrant up vg-compute-12
vagrant ssh vg-docker-12 (password:vagrant)
del Vagrantfile
vagrant init --template Vagrantfile.erb 
vagrant up vg-compute-12
vagrant ssh vg-docker-12 (password:vagrant)

Browse
http://192.168.20.20:8080/

sudo docker version
sudo docker image prune --force
sudo docker pull jenkins/jenkins:lts-jdk11
sudo docker image ls
sudo docker run -d -p 8080:8080 --name jenkinsci jenkins/jenkins:lts-jdk11 
sudo docker exec $(docker ps -q) cat /var/jenkins_home/secrets/initialAdminPassword
sudo docker container ls
sudo docker container stop jenkinsci
sudo docker container prune --force

http://192.168.20.11:8080

Plugin list
Script Console(Groovy)
http://192.168.20.11:8080/script

Jenkins.instance.pluginManager.plugins.each{
  plugin ->
    println ("${plugin.getShortName()}")
}
~~~~
Dockerfile build
~~~~
del Vagrantfile
vagrant init --template Vagrantfile.erb 
vagrant up vg-compute-13
vagrant ssh vg-docker-13 (password:vagrant)

Browse
http://192.168.20.21:8080/

cd /vagrant/dockerfiles
sudo docker image prune --force
sudo docker build -t jenkinsci:latest . --file /vagrant/dockerfiles/Dockerfile.plugins
sudo docker image ls
sudo docker run -d -p 8080:8080 --name jenkinsci jenkinsci:latest
sudo docker exec $(docker ps -q) cat /var/jenkins_home/secrets/initialAdminPassword
sudo docker container ls
sudo docker container stop jenkinsci
sudo docker container prune --force
~~~~

~~~~
https://www.jenkins.io/
Official Jenkins Docker image
https://hub.docker.com/_/jenkins
~~~~
