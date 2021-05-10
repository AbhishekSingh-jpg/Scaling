# Scaling a Web Application

>**Scalability** is a virtue that a web app needs to possess, to make the app fault tolerant and user experience more fluent and the operations more efficient.

## A Simple Web Architecture

<div style='text-align:center'><img src="https://miro.medium.com/max/427/1*sG4nwmLYTi4-hpkDOubrsg.png" style="background-color:white"></div>

> Above diagram shows a simple web architecture. It has a single server that listens for client request and communicates with database.

## Various issues in a simple web architecture

- Web server overload

- Single point of failure

- Distributing traffic

- Factoring out sessions

- Expensive Queries

- Possibility of database failure

## 1. Web Server Overload

>As number of clients connecting to server increases load on server increases.Server will eventually run out of resources like CPU,RAM.

### Vertical Scaling

<div style='text-align:center'><img src="https://miro.medium.com/max/461/1*M-jKaJnspoL6mzsJf4Gzpw.png" style="background-color:white"></div>

> Upgrading the server

> Expensive process

> Temporary Fix

## 2. Single Point Of Failure

>Since we are using a single server if it goes down then we can't take any request. This might happen due to many reasons or due to maintenance.

### Horizontal Scaling

<div style='text-align:center'><img src="https://miro.medium.com/max/277/1*zLAD8c2raZsTJgVurqSvaw.png" style="background-color:white"></div>

> Add more servers of original capacity(CPU,RAM)

> Cheaper process

> Application works even if a few servers goes down

## 3. Distributing Traffic

<div style='text-align:center'><img src="https://miro.medium.com/max/251/1*_8aMCj92o0ViI_GLH9CD4A.png" style="background-color:white"></div>

>Load balancers are used to evenly distribute traffic to all servers

>2-3 load balancers are used to avoid bottle necking or single point failure

## 4. Factoring out sessions

<div style='text-align:center'><img src="https://miro.medium.com/max/632/1*r7MB6iZICOuu6o_6Zn6ujg.png" style="background-color:white"></div>

>If a user is logged in load balancer might take him to server 1 and might take the user to different server during his second request where user will have yo login again.

>To solve this the user's sessions are decoupled to a Redis server

## 5. Queries are expensive

>If a application is handling millions of users then querying database every time slows down the application

> A Cache is used in this case.

>If user is in cache then no need to query the database

>Sharding is used to increase database efficiency

## 6. Possibility of Database Failure

<div style='text-align:center'><img src="https://miro.medium.com/max/312/1*y0vFv9-dF3DL2Y4XbkDcMQ.png" style="background-color:white"></div>

>In order to avoid application failure due to collapse of a single database, multiple databases are used

>Databases share master slave relationship

>Replication technique is used to make copies of every entry in master

>Read operation is handled by slaves while write,delete and edit is done in master

## Reference Links
- <https://medium.com/@harithjaved/scaling-your-web-application-693657ce333c>
- https://www.youtube.com/watch?v=sHPVVdITpwc&t=593s