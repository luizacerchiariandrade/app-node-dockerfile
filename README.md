# app-node-dockerfile
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
