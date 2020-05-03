# Docker-Project

#### This project includes the connectivity of wordpress and mysql using docker.

### Steps:

1. Pull the wordpress and mysql images from [Docker hub](https://hub.docker.com) :
```
    mysql:5.7
    wordpress:5.1.1-php7.3-apache
```    
2. Create new volume to store the data permanantly.
      use command:
      `docker volume create`
3. Launch the mysql container first with the created volume:
      ```
      docker run -d -it -e MYSQL_ROOT_PASSWORD=rootpassword
      -e MYSQL_USER=username
      -e MYSQL_PASSWORD=password
      -e MYSQL_DATABASE=mydb
      -v mysql_storage:/var/lib/mysql
      --name dbos mysq1:5.7
      ```
4. Launch the wordpress container using following command:
```
      docker run -dit -e WORDPRESS_DB_HOST=dbos
      -e WORDPRESS_DB_USER=username
      -e WORDPRESS_DB_PASSWORD=password
      -e WORDPRESS_DB_NAME=mydb
      -v wp_storage:/var/www/html
      -name wpos
      -- link dbos -p 8080:80
      wordpress:5.1.1-php7.3-apache
```
5. Check the logs to see if everything is working fine   
6. Configure IP
7. Type the IP with port 8080 in the browser to launch the wordpress.com
8. Wordpress will ask for setup. Complete those steps and you are ready to go!
9. Publish your blogs, customize the site.
10. Can do a lot more things to improve the site.

Also, To automate all these steps, docker-composer plays vital role.
For that, you have to download the docker-composer, then conigure the docker-composer.yml file and then open a terminal and `cd` to the folder where `docker-compose.yml` is saved and run it using `docker-composer up` command. All of the above steps will be carried out automatically within some seconds.

These are just basic steps, a lot more can be done in this project!

