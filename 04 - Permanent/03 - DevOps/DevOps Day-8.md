---
date: 2025-06-25T20:42
tags: []
---

# Docker


First we start with containerizing a web Application with a Dockerfile
```embed
title: "Containerizing a Web Application with a Dockerfile"
image: "https://miro.medium.com/v2/resize:fit:752/1*fRp3UtczAicsJylG-ekkoQ.png"
description: "Introduction"
url: "https://medium.com/@adeyemijoshua/containerizing-a-web-application-with-a-dockerfile-9cbee5014086"
favicon: ""
aspectRatio: "55.58510638297872"
```

This is how we can do in the IDE version

```js
// Step 1: Import Express
const express = require('express');

// Step 2: Create an app instance
const app = express();

// Step 3: Define a port
const PORT = 3000;

// Step 4: Create a basic route
app.get('/', (req, res) => {
  res.send('🎉 Hello from Express running in your IDE!');
});

// Step 5: Start the server
app.listen(PORT, () => {
  console.log(`✅ Server is running at http://localhost:${PORT}`);
});

```

to run write the below code in terminal 
``` bash
npm init -y         # (Only once to create package.json)
npm install express # (Install Express framework)
node server.js      # (Run your server)
```

and the server will be http://localhost:3000

## --> But to do this with Docker

In your IDE
step-1 - make files `server.js` `package.json` `Dockerfile` `index.html`

in `server.js`
```js
const http = require('http');  
const fs = require('fs');  
const path = require('path');  
  
const port = 3000;  
  
const server = http.createServer((req, res) => {  
    const filePath = path.join(__dirname, 'index.html');  
    fs.readFile(filePath, (err, data) => {  
        if (err) {  
            res.writeHead(500);  
            res.end('Error loading file');  
        } else {  
            res.writeHead(200, { 'Content-Type': 'text/html' });  
            res.end(data);  
        }    });});  
  
server.listen(port, () => {  
    console.log(`Server running at http:localhost:${port}`);    
});
```

in `package.json`
```json
{  
  "name": "node-fs-server",  
  "version": "1.0.0",  
  "description": "A basic Node.js server using fs and path",  
  "main": "server.js",  
  "scripts": {  
    "start": "node server.js"  
  },  
  "author": "Your Name",  
  "license": "MIT"  
}
```

--> in `DockerFile`

```Dockerfile
# Use official Node.js image  
FROM node:18-alpine   
# pulling 18-alphione  
  
# Create app directory  
WORKDIR /app  
  
# Copy files  
COPY . .  
  
# Install dependencies (none in this case, but safe to include)  
RUN npm install   
  
# Expose port  
EXPOSE 3000  
  
# Start the server  
CMD ["npm", "start"]
```

--> in `index.file`

```html
<!DOCTYPE html>  
<html>  
<head>  
    <title>Hello from Docker</title>  
</head>  
<body>  
<h1>Hello, Worldo!</h1>  
</body>  
</html>
```

--> and in the `terminal`

```bash
npm install fs

npm install path

docker build -t node-app . # where `.` will be replaced with the alsolute path
```


