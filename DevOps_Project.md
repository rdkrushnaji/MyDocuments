#DevOps_Project

    Java -version
    
    
    yum remove java-1.0.7*
    
    
    yum install java-1.8*

    java -version
    find /usr/lib/jvm/java-1.8* | head -n 3
    JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-<Java version which seen in the above output>
    export JAVA_HOME
      PATH=$PATH:$JAVA_HOME
 # To set it permanently update your .bash_profile
    vi ~/.bash_profile



/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.272.b10-1.amzn2.0.1.x86_64

[root@ip-172-31-34-109 ~]# cd ~
[root@ip-172-31-34-109 ~]# vi .bash_profile
[root@ip-172-31-34-109 ~]# echo $JAVA_HOME

[root@ip-172-31-34-109 ~]#

[root@ip-172-31-34-109 ~]# exit
logout
[ec2-user@ip-172-31-34-109 ~]$ sudo su -
Last login: Sat Feb 13 05:56:08 UTC 2021 on pts/0
[root@ip-172-31-34-109 ~]# echo $JAVA_HOME
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.272.b10-1.amzn2.0.1.x86_64
[root@ip-172-31-34-109 ~]#

https://pkg.jenkins.io/redhat-stable/

[root@ip-172-31-34-109 ~]#   sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
--2021-02-13 06:10:15--  https://pkg.jenkins.io/redhat-stable/jenkins.repo
Resolving pkg.jenkins.io (pkg.jenkins.io)... 199.232.22.133, 2a04:4e42:42::645
Connecting to pkg.jenkins.io (pkg.jenkins.io)|199.232.22.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 85
Saving to: ‘/etc/yum.repos.d/jenkins.repo’

100%[===============================================================================================>] 85          --.-K/s   in 0s

2021-02-13 06:10:16 (5.52 MB/s) - ‘/etc/yum.repos.d/jenkins.repo’ saved [85/85]

[root@ip-172-31-34-109 ~]#   sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
[root@ip-172-31-34-109 ~]# yum install jenkins


[root@ip-172-31-34-109 ~]# service jenkins status
[root@ip-172-31-34-109 ~]# service jenkins start
[root@ip-172-31-34-109 ~]# service jenkins status


cat /var/lib/jenkins/secrets/initialAdminPassword


manage jenkins -> Global Tool Configuration -> add JDK


[root@ip-172-31-34-109 ~]# hostname jenkins
[root@ip-172-31-34-109 ~]# exit
logout

[ec2-user@ip-172-31-34-109 ~]$ sudo su -
Last login: Sat Feb 13 06:07:30 UTC 2021 on pts/0
[root@jenkins ~]# 

[root@jenkins ~]# yum install git -y

search plugun github in jenkins -> install without restart -> global tool configuration -> git apply save


[root@jenkins ~]# pwd
/root
[root@jenkins ~]# cd /opt/
[root@jenkins opt]# ls
aws  rh
[root@jenkins opt]# cd aws/
[root@jenkins aws]# ls
apitools  bin
[root@jenkins aws]# cd ..
[root@jenkins opt]# wget https://mirrors.estointernet.in/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz




[root@jenkins opt]# ls
apache-maven-3.6.3  apache-maven-3.6.3-bin.tar.gz  aws  rh
[root@jenkins opt]# mv apache-maven-3.6.3 maven
[root@jenkins opt]# ls
apache-maven-3.6.3-bin.tar.gz  aws  maven  rh
[root@jenkins opt]# cd maven/
[root@jenkins maven]# ls
bin  boot  conf  lib  LICENSE  NOTICE  README.txt
[root@jenkins maven]# pwd
/opt/maven


[root@jenkins maven]# vi ~/.bash_profile


# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi

# User specific environment and startup programs
JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.272.b10-1.amzn2.0.1.x86_64
PATH=$PATH:$HOME/bin:$JAVA_HOME:$M2_HOME:$M2
M2_HOME=/opt/maven
M2=/opt/maven/bin


export PATH
[root@jenkins maven]# echo $M2

[root@jenkins maven]# exit
logout
[ec2-user@ip-172-31-34-109 ~]$ sudo su -
Last login: Sat Feb 13 06:34:50 UTC 2021 on pts/0
[root@jenkins ~]# echo $M2
/opt/maven/bin
[root@jenkins ~]# echo $M2_HOME
/opt/maven
[root@jenkins ~]# mvn --version
Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
Maven home: /opt/maven
Java version: 1.8.0_272, vendor: Red Hat, Inc., runtime: /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.272.b10-1.amzn2.0.1.x86_64/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "4.14.214-160.339.amzn2.x86_64", arch: "amd64", family: "unix"
[root@jenkins ~]#


Plugins:

maven integration 
maven invoker


[root@jenkins ~]# cd /var/lib/jenkins/workspace/
[root@jenkins workspace]# ls
My_First_Job  My_First_Maven_Build
[root@jenkins workspace]#

[root@tomcat bin]# java -version
java -version
openjdk version "1.8.0_272"
OpenJDK Runtime Environment (build 1.8.0_272-b10)
OpenJDK 64-Bit Server VM (build 25.272-b10, mixed mode)
[root@tomcat bin]# find /usr/lib/jvm/java-1.8* | head -n 3
/usr/lib/jvm/java-1.8.0
/usr/lib/jvm/java-1.8.0-openjdk
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.272.b10-1.amzn2.0.1.x86_64
[root@tomcat bin]# vi ~/.bash_profile
[root@tomcat bin]# ./startup.sh
Using CATALINA_BASE:   /opt/tomcat
Using CATALINA_HOME:   /opt/tomcat
Using CATALINA_TMPDIR: /opt/tomcat/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /opt/tomcat/bin/bootstrap.jar:/opt/tomcat/bin/tomcat-juli.jar
Using CATALINA_OPTS:
Tomcat started.
[root@tomcat bin]#


$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
        . ~/.bashrc
fi

# User specific environment and startup programs
JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.272.b10-1.amzn2.0.1.x86_64
M2_HOME=/opt/maven
M2=/opt/maven/bin
PATH=$PATH:$HOME/bin:$JAVA_HOME:$M2_HOME:$M2



export PATH
~




$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

for manager app:----


Tomcat started.
[root@tomcat bin]# find / -name contest.xml
[root@tomcat bin]# find / -name context.xml
/opt/tomcat/conf/context.xml
/opt/tomcat/webapps/examples/META-INF/context.xml
/opt/tomcat/webapps/host-manager/META-INF/context.xml
/opt/tomcat/webapps/manager/META-INF/context.xml
[root@tomcat bin]# vi /opt/tomcat/webapps/host-manager/META-INF/context.xml
[root@tomcat bin]# vi /opt/tomcat/webapps/manager/META-INF/context.xml
[root@tomcat bin]# ./shutdown.sh
Using CATALINA_BASE:   /opt/tomcat
Using CATALINA_HOME:   /opt/tomcat
Using CATALINA_TMPDIR: /opt/tomcat/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /opt/tomcat/bin/bootstrap.jar:/opt/tomcat/bin/tomcat-juli.jar
Using CATALINA_OPTS:
[root@tomcat bin]# ./startup.sh
Using CATALINA_BASE:   /opt/tomcat
Using CATALINA_HOME:   /opt/tomcat
Using CATALINA_TMPDIR: /opt/tomcat/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /opt/tomcat/bin/bootstrap.jar:/opt/tomcat/bin/tomcat-juli.jar
Using CATALINA_OPTS:
Tomcat started.
[root@tomcat bin]#



vi Dockerfile

FROM tomcat:8.5.43
MAINTAINER KRUSHNA

COPY ./webapp.war /usr/local/tomcat/webapps
~
~
~
~


[dockeradmin@docker-host ~]$ vi Dockerfile
[dockeradmin@docker-host ~]$ docker build -t mydev-project .

[dockeradmin@docker-host ~]$ docker images
[dockeradmin@docker-host ~]$ docker container ls
[dockeradmin@docker-host ~]$ docker run --name mydev-container -d -p 8080:8080 mydev-project


********************************
ANSIBLE
*********************************

https://aws.amazon.com/amazon-linux-2/
[ec2-user@ip-172-31-6-6 ~]$ sudo su -
[root@ip-172-31-6-6 ~]# hostname ansible
[root@ansible ~]# yum install python
Loaded plugins: extras_suggestions, langpacks, priorities, update-motd
Package python-2.7.18-1.amzn2.0.2.x86_64 already installed and latest version
Nothing to do
[root@ansible ~]# python --version
[root@ansible ~]# yum install python-pip
[root@ansible ~]# pip install ansible

[root@ansible /]# mkdir /etc/ansible
[root@ansible /]# useradd ansadmin
[root@ansible /]# passwd ansadmin
Changing password for user ansadmin.
New password:
BAD PASSWORD: The password contains the user name in some form
Retype new password:
passwd: all authentication tokens updated successfully.
[root@ansible /]#

visudo
shift+g end of file
o insert mode
ansadmin ALL=(ALL)       NOPASSWD: ALL

[root@ansible /]# yum install docker -y
[root@ansible /]# service docker status
[root@ansible /]# service docker start
[root@ansible /]# service docker status

[root@ansible /]# usermod -aG docker ansadmin
[root@ansible /]# id ansadmin
uid=1001(ansadmin) gid=1001(ansadmin) groups=1001(ansadmin),992(docker)
[root@ansible /]#

[root@ansible /]# vi /etc/ssh/sshd_config
 password yes

[root@ansible /]# service sshd reload
Redirecting to /bin/systemctl reload sshd.service
[ansadmin@ansible ~]$ ssh-keygen
[ansadmin@ansible ~]$ ls -la
[ansadmin@ansible ~]$ cd .ssh/
[ansadmin@ansible .ssh]$ ls
id_rsa  id_rsa.pub
[ansadmin@ansible .ssh]$ hostname ansible-control-node

[root@docker-host ~]# useradd ansadmin
[root@docker-host ~]# passwd ansadmin
[root@docker-host ~]# ip addr

[ansadmin@ansible-control-node ~]$ ssh-copy-id ansadmin@172.31.3.132

[ansadmin@ansible-control-node ~]$ ssh ansadmin@172.31.3.132

[ansadmin@docker-host ~]$ exit
logout
Connection to 172.31.3.132 closed.
[ansadmin@ansible-control-node ~]$

[ansadmin@ansible-control-node ~]$ cd /etc/ansible/
[ansadmin@ansible-control-node ansible]$ vi hosts
[ansadmin@ansible-control-node ansible]$ sudo vi hosts

172.31.3.132
localhost
:wq

[ansadmin@ansible-control-node ansible]$ ansible all -m ping
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:ekcSsXF7tvi0Asm5aBS7yS5sQPAHZRJubphGEWzUdRA.
ECDSA key fingerprint is MD5:8a:e4:13:3d:d4:ce:18:8a:a8:c9:81:db:4c:98:c0:18.
Are you sure you want to continue connecting (yes/no)? [WARNING]: Platform linux on host 172.31.3.132 is using the discovered Python interpreter at /usr/bin/python, but future installation of
another Python interpreter could change the meaning of that path. See
https://docs.ansible.com/ansible/2.10/reference_appendices/interpreter_discovery.html for more information.
172.31.3.132 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}

localhost | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: Host key verification failed.",
    "unreachable": true
}
[ansadmin@ansible-control-node ansible]$
[ansadmin@ansible-control-node ansible]$ ssh-copy-id localhost
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/ansadmin/.ssh/id_rsa.pub"
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:ekcSsXF7tvi0Asm5aBS7yS5sQPAHZRJubphGEWzUdRA.
ECDSA key fingerprint is MD5:8a:e4:13:3d:d4:ce:18:8a:a8:c9:81:db:4c:98:c0:18.
Are you sure you want to continue connecting (yes/no)? yes
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
ansadmin@localhost's password:

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'localhost'"
and check to make sure that only the key(s) you wanted were added.

[ansadmin@ansible-control-node ansible]$

