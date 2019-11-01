# dockercompose-springboot-mysql-nginx
Source: https://programmer.group/spring-boot-2.0-v-docker-compose-spring-boot-nginx-mysql-practice.html

Spring Boot + Nginx + Mysql is the most commonly used combination in practical work. The front end uses Nginx proxy to forward requests to Tomcat service embedded in the back end Spring Boot. Mysql is responsible for data-related interaction in business. So how can we solve these environments without docker?

1. Install Nginx, configure Nginx-related information, and restart.
2. Install Mysql, configure character set time zone and other information, restart, and finally initialize the script.
3. Start Spring Boot project and conduct debugging test as a whole.

You see, I only wrote three lines, but in fact, it's very difficult to build these environments, but this is not the end. It takes a while to migrate to another environment. What should we do again? Normally, test environment, SIT environment, UAT environment, production environment! We need to build it four times. Didn't someone say that it was built four times? It's no big deal, so I want to tell you, Too yong, Too Simple.

#DOCKER  /Simple

	##Start service /background boot 
	docker-compose up -d
	
	##Use docker-compose ps to view all current containers in the project
	docker-compose ps


#https://www.digitalocean.com/community/tutorials/how-to-configure-the-nginx-web-server-on-a-virtual-private-server
In the "nginx.conf" file, we can see that the end of the "http" block has:
include /etc/nginx/conf.d/*.conf;
include /etc/nginx/sites-enabled/*;

Par définition, nginx est un reverse proxy et un serveur http (Wikipédia). 
De ce fait il se positionne - en tant que composant d'une architecture - de manière frontale à des services applicatifs ou des serveurs Web et est capable de répondre à des requêtes HTTP. Avec les configurations appropriées il peut être utilisé comme load balancer. De manière simplifiée, nginx peut être configuré en écrivant des directives dans un fichier de configuration. Ces directives nous permettront donc de définir éventuellement une stratégie de répartition de charges 
et les services applicatifs vers lesquels rediriger les requêtes.