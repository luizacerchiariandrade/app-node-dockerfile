﻿# app-node-dockerfile
 <h1> parte 1 </h1>
 para rodar com docker colocar: <br/>
 
FROM node:14 <br/> <br/> 
WORKDIR /app-node <br/>
COPY . . <br/> 
RUN npm install <br/>
ENTRYPOINT npm start <br/>

Buildar a imagem: docker build -t cerchiariluiza/app-node:1.0 . <br/>
Rodar: docker run -d -p 8081:3000 cerchiariluiza/app-node
<br/> Matar todos: docker stop $(docker container ls -q)
 
 <h1> parte 2 expondo portas </h1>
   
FROM node:14 <br/> <br/> 
WORKDIR /app-node <br/>
EXPOSE 3000 <br />
COPY . . <br/> 
RUN npm install <br/>
ENTRYPOINT npm start <br/>
  
  <p> Gerei a imagem: docker build -t cerchiariluiza/app-node:1.1 . </p>
  <p> Rodei: docker run -d cerchiariluiza/app-node:1.1 </p> Automaticamente foi até a 3000

  <h1>  parte 3 chaveando portas</h1>

<br/>FROM node:14
<br/>WORKDIR /app-node
<br/>ARG PORT_BUILD=6000
<br/>ENV PORT=$PORT_BUILD
<br/>EXPOSE $PORT_BUILD
<br/>COPY . .
<br/>RUN npm install 
<br/>ENTRYPOINT npm start

<br/>docker build -t cerchiariluiza/app-node:1.2 .
<br/>docker run -d cerchiariluiza/app-node:1.2
<br/>porta 6000
<br/>
<br/>No index: 
<br/>app.listen(process.env.PORT, ()=>{
<br/>    console.log("Server is listening on port 3000")
<br/>})
<br/>
<br/>ai pode mudar a porta por comando com -P   ::::::docker run -p 3030:6000 -d cerchiariluiza/app-node:1.2

<h1> limpar </h1>
[docker image rmi $(docker image ls -aq)
docker container rmi $(docker images ls -aq) --force
<br> docker run -it -v C:/lu/app:/app ubuntu
