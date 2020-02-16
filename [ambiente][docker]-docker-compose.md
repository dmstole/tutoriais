
# Projeto modelo em node.js, utilizando Dockerfile e docker-compose.

## Exemplo de projeto node.js:

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

docker-compose
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
