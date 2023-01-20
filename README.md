
Deploy with docker compose
#docker-compose up -d

  Creating network "ec2-user_wpnetwork" with the default driver
  Creating volume "ec2-user_mysqlvol" with default driver
  Creating volume "ec2-user_myvol" with default driver
  Pulling db (mysql:5.7)...
  .......
  Status: Downloaded newer image for wordpress:latest
  Creating ec2-user_wordpress_1 ... done
  Creating ec2-user_db_1        ... done
  
  The expected result,
  
#docker ps
  
  CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS          PORTS                                   NAMES

  698ae48b2e14   mysql:5.7          "docker-entrypoint.s…"   37 minutes ago   Up 37 minutes   3306/tcp, 33060/tcp                     ec2-user_db_1
  d7257131447f   wordpress:latest   "docker-entrypoint.s…"   37 minutes ago   Up 37 minutes   0.0.0.0:8000->80/tcp, :::8000->80/tcp   ec2-user_wordpress_1


Navigate to http://ipaddress:8000 in your web browser to access WordPress.


Stop and remove the containers

#docker-compose down

  Stopping ec2-user_db_1        ... done
  Stopping ec2-user_wordpress_1 ... done
  Removing ec2-user_db_1        ... done
  Removing ec2-user_wordpress_1 ... done
  Removing network ec2-user_wpnetwork

To remove all WordPress data, delete the named volumes by using the -v parameter

#docker-compose down -v

  Removing network ec2-user_wpnetwork
  WARNING: Network ec2-user_wpnetwork not found.
  Removing volume ec2-user_mysqlvol
  Removing volume ec2-user_myvol
