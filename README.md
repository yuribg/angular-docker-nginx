# 1. Create Angular app with @angular/cli v16.
- Server-side rendering (SSR) disabled,
- route file enabled, 
- CSS style format.

```
npx @angular/cli@16 new angular-docker-nginx --routing true --style css
```

Do everything inside angular app folder.

```
cd angular-docker-nginx
```

Check if app is running using 

```
ng serve
```

And listen on default port 4200.

# 2. Create and edit Dockerfile.

```
touch Dockerfile
```

```
FROM node:alpine

WORKDIR /usr/src/app

COPY . /usr/src/app

RUN npm install -g @angular/cli@16

RUN npm install

CMD ["ng", "serve", "--host", "0.0.0.0"]
```

# 3. Create Docker image.

```
docker build -t angular-docker .
```

# 4. Run Docker container.

```
docker run -d -p 80:4200 --name angular-docker-nginx angular-docker-nginx
```

# 5. Open app in port 80.

[localhost:80](http://localhost:80/)

Source:
[Creating and running an Angular application in a Docker container](https://dev.to/rodrigokamada/creating-and-running-an-angular-application-in-a-docker-container-40mk)