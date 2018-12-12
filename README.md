# MSR-test-task
This repository consists of Setup of both Apache Webserver and CouchDB in docker container with docker-compose deployment with Configuration Management tools like Ansible.

# ansible deployement
This repo consists of all ansible playbooks and ansible workspace of Congiguring apache and couchDB.

--> Initialy I launched two ubuntu16.04 server LTS in AWS and one server for Jump-Ansible-Control Machine. by following below things.
         •	Instance Type of both instance is t2.micro
         •	Operating System for both instances Ubuntu Server 16.04 LTS
         •	Hostname of Instance 1 : MSR-test-Instance-1 
         •	Hostname of Instance 2 : MSR-test-Instance-2
         
         Hostname            public ip             os                           purpose
         
      jump server:           54.255.247.8       Ubuntu-16.04       Ansible-Control-Machine to setup below two nodes.
      MSR-test-instance-1    3.1.6.96           Ubuntu 16.04       Apache Webserver Installed with Docker .
      MSR-test-instance-2    54.254.189.232     Ubuntu 16.04       CouchDB Installed with Docker .
      
--> I entered the entries of two node in hosts file which you can find in hosts file in Github.
--> I wrote and executed the following playbooks i.e.., node.yml, docker1.yml, git.yml and openssl.yml by Ansible in 
    the both node MSR-test-Instance-1 and MSR-test-Instances-2 to install the below packages :
             •	NVM – Version 0.33.2
             •	Node – 8.12.0
             •	Docker – 18.06 or latest
             •	Docker Compose – 1.13 or latest
             •	*Openssl – latest version 
             •	Git – latest version


--> Configured a Apache Webserver in docker container using docker-compose by ansible in MSR-test-instance-1, which will automatically takes the sample html code in github repo and deployed. the following are docker-compose and playbooks for that
                 * docker-compose.yml (compose file)
                 * docker-web.yml (which is a playbook)
                 
                 you can ping with http://3.1.6.96
  
--> configured couchdb in docker container using docker compose file by executed ansible playbook in MSR-test-instance-2, which will deploys couch db in docker container.
      the ports exposed is 5984:5984, a network and volume created named couchdb.
      The following files are the playbooks for configuring couchdb in docker contianer in MSR-test-instance-2:
                    * Couch_docker/docker-compose.yml (which is compose file for couchdb)
                    * Couch_docker/docker-couchdb-up.yml ( which is to startup the couchdb service)
                    * Couch_docker/docker-couchdb-down.yml (which is to down the couchdb service) 
      You can find the db with 
                          - ip: 54.254.189.232:5984
                          
All the files I used was commited to the present repo with we are currently working.
