# dockercompose-springboot-mysql-nginx
Source: https://programmer.group/spring-boot-2.0-v-docker-compose-spring-boot-nginx-mysql-practice.html

Spring Boot + Nginx + Mysql is the most commonly used combination in practical work. The front end uses Nginx proxy to forward requests to Tomcat service embedded in the back end Spring Boot. Mysql is responsible for data-related interaction in business. So how can we solve these environments without docker?

1. Install Nginx, configure Nginx-related information, and restart.
2. Install Mysql, configure character set time zone and other information, restart, and finally initialize the script.
3. Start Spring Boot project and conduct debugging test as a whole.

You see, I only wrote three lines, but in fact, it's very difficult to build these environments, but this is not the end. It takes a while to migrate to another environment. What should we do again? Normally, test environment, SIT environment, UAT environment, production environment! We need to build it four times. Didn't someone say that it was built four times? It's no big deal, so I want to tell you, Too yong, Too Simple.

#DOCKER  /Simple




#
In the "nginx.conf" file, we can see that the end of the "http" block has:
include /etc/nginx/conf.d/*.conf;
include /etc/nginx/sites-enabled/*;