# app-node-dockerfile
 
 para rodar com docker colocar: <br/>
 
FROM node:14 <br/> <br/> 
WORKDIR /app-node <br/>
COPY . . <br/> 
RUN npm install <br/>
ENTRYPOINT npm start <br/>

Buildar a imagem: docker build -t cerchiariluiza/app-node:1.0 . <br/>
Rodar: docker run -d -p 8081:3000 cerchiariluiza/app-node

<br/> Matar todos docker stop $(docker container ls -q)
