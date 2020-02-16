
# Projeto modelo em node.js, utilizando Dockerfile e docker-compose.

Para executar esse projeto, tenha na mesma pasta arquivos com o codigo abaixo. E em seguida, execute o seguinte comando para instanciar container:
```
docker-compose up -d
```

Caso ainda nao tenha instalado o docker-compose, veja esse [link].

## Exemplo de projeto node.js:
index.js
```
'use strict';

const express = require('express');

const PORT = 8080;
const HOST = '0.0.0.0';

const app = express();
app.get('/', (req, res) => {
  res.send('Hello World !!!!');
});

app.get('/cliente', (req, res) => {
  res.json([
    {"nome":"Diogo"},
    {"nome":"Lucas"},
    {"nome":"Juciane"},
    {"nome":"Sara"},
  ]);
});

app.listen(PORT, HOST);
console.log(`Running on http://${HOST}:${PORT}`);
```

package.json
```
{
  "name": "demo",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "nodemon ./index.js"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "4.17.1",
    "nodemon": "^1.18.10"
  }
}
```
Dockerfile
```
FROM node:10

WORKDIR /var/www

COPY package.json /var/www

RUN cd /var/www
RUN npm install

EXPOSE 8080
CMD [ "npm", "start" ]
```

docker-compose.yml
```
version: '3'
services:
  web:
    build: .
    volumes: 
      - ./:/var/www
    command: npm start
    ports:
      - '3000:8080'
```

[link]: <https://github.com/dmstole/tutoriais/blob/master/%5Bambiente%5D%5Bdocker%5D-instalacao-docker-compose.md>
