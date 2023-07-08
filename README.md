# Docker
<h3> Concept:</h3>
<ul>
<li>Docker is an open-source application container engine. 
<li>It came in 2013 and was realized based on go. 
<li>Docker can help developers package applications and dependencies to a light weight and portable container and publish on any Linux environment. 
<li>Docker used sandbox mechanism and each container is isolated with others;
</ul>
<h3> Structure </h3>
<img src="https://docs.docker.com/engine/images/architecture.svg" width="600px" height="400px"></img>
The relationship between image and container is similar to the relation between instaintiable class and object.
<h3> Commands:</h3>
<table>
  <tr>
    <th></th>
    <th>command</th>
    <th>explanation</th>
  </tr>
  <tr>
    <td>service related command</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>image related command</td>
    <td>docker images;<br>
      docker search redis;<br>
      docker pull redis;(download redis)<br>
      docker rmi +id or name
    </td>
    <td>the second one is to download redis;<br>
      the third one is to remove redis;
    </td>
  </tr>
  <tr>
    <td>container related command</td>
    <td>docker run -it --name=c1 centos:latest /bin/bash<br>
    docker ps -a<br>
    docker run -id --name=c2 centos:7<br>
    docker exec -it c2 /bin/bash<br>
    docker stop + name <br>
    docker start + name <br>
    docker rm + id or name of the container<br>
    docker inspect +name
    </td>
    <td>1.create and run the container directly<br>
      2.show all containers<br>
      3.create and use the command to run the container<br>
      4.enter container which was created with -id<br>
      -it interactive container: running after being created;<br>
      -id guardian container; running after executing command<br>
      exit -it close container and stop running<br>
      -id close container and use docker stop ...to stop<br>
    </td>
  </tr>
  </table>
  
  <h3>data volume</h3>
  data volume is used by docker to persist and exchange data.
  Data volume is one directory or file in the host computer. When the directory in container is binded with the directory in host directory, update on data on one side can synchronously update the other. One data volume can be mounted by many containers. One container can also mount many data volumes.<br>
  <b>realize mounting:</b><br>
  docker run -it --name=c1 -v /Users/mengjiayu/Desktop/docker:/root/data_container centos:7 /bin/bash
  
  <h3>Deployment</h3>
  Problems:
  1.when I deployed mysql in docker with command(docker run -id -p 3307:3306 --name=d_mysql -v $PWD/conf:/etc/mysql/conf.d -v $PWD/logs:/logs -v$PWD/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=19911120Aa, mysql:latest /bin/bash),the container was created successfully but it exited automaticlly. Then I used docker logs +container Id to check specific problem and I found I didn't use colon the first time between mysql and latest.
  
  
  
