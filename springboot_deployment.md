1. Create an EC2 instance of t2.micro and run the service helloworld on that node 
 
# yum install git java-1.8.0-openjdk-devel maven –y
# cd /opt
# git clone https://github.com/tushardashpute/springboohello-CICD.git
Cloning into 'springboohello-CICD'...
remote: Enumerating objects: 53, done.
remote: Counting objects: 100% (53/53), done.
remote: Compressing objects: 100% (47/47), done.
remote: Total 53 (delta 16), reused 25 (delta 2), pack-reused 0
Unpacking objects: 100% (53/53), done.

# mvn clean install 

[root@ip-172-31-54-101 springboohello-CICD]# cd target


[root@ip-172-31-54-101 target]# ls -ltr
total 15860
drwxr-xr-x 3 root root       19 Apr 26 08:17 classes
drwxr-xr-x 3 root root       25 Apr 26 08:17 generated-sources
-rwxr--r-- 1 root root 16233145 Apr 26 08:17 gs-spring-boot-0.1.0.jar
-rw-r--r-- 1 root root     3280 Apr 26 08:17 gs-spring-boot-0.1.0.jar.original
drwxr-xr-x 2 root root       28 Apr 26 08:17 maven-archiver
drwxr-xr-x 3 root root       35 Apr 26 08:17 maven-status


# cd /opt
[root@ip-172-31-54-101 opt]# cat gs-spring-boot
#!/bin/sh
sudo /usr/bin/java -jar /opt/gs-spring-boot.jar &

# chmod +x gs-spring-boot

[root@ip-172-31-54-101 opt]# ln -s /opt/springboohello-CICD/target/gs-spring-boot-0.1.0.jar /opt/gs-spring-boot.jar

[root@ip-172-31-54-101 opt]# ll gs-spring-boot.jar
lrwxrwxrwx 1 root root 56 Apr 26 09:00 gs-spring-boot.jar -> /opt/springboohello-CICD/target/gs-spring-boot-0.1.0.jar

[root@ip-172-31-54-101 opt]# cat /etc/systemd/system/helloworld.service
  [Unit]
  Description=A Spring Boot application
  After=syslog.target

  [Service]
  Type=forking

  Environment=JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.282.b08-1.amzn2.0.1.x86_64/jre
  ExecStart=/opt/gs-spring-boot
  SuccessExitStatus=143

  TimeoutStopSec=10
  Restart=on-failure
  RestartSec=5

  [Install]
  WantedBy=multi-user.target


[root@ip-172-31-54-101 opt]# chkconfig helloworld on
Note: Forwarding request to 'systemctl enable helloworld.service'.


[root@ip-172-31-54-101 opt]# service helloworld start
Redirecting to /bin/systemctl start helloworld.service


[root@ip-172-31-54-101 target]# jps
  4147 jar
  4187 Jps

[root@ip-172-31-54-101 target]# ps -ef|grep -i jar
  root      4147  3417 26 08:21 pts/0    00:00:07 java -jar gs-spring-boot-0.1.0.jar
  root      4198  3417  0 08:22 pts/0    00:00:00 grep --color=auto -i jar
 
 
[root@ip-172-31-54-101 target]# netstat -na|grep -i 33333
  tcp6       0      0 :::33333                 :::*                    LISTEN


![image](https://user-images.githubusercontent.com/74225291/210554810-56abec60-ec7c-4fd8-b8ad-0686def20f23.png)

