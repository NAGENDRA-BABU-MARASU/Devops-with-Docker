# Hey Everybody 👋
 Here are my solutions for the online course [Devops with Docker](https://devopswithdocker.com/) 
 
 <img src="https://raw.githubusercontent.com/wesbos/Font-Awesome-Docker-Icon/07fb62ca1b8dea97b351d89686bb32418735182d/docker-white.svg" width=50 height=50>

## Exercises 

### [1.1: GETTING STARTED](https://devopswithdocker.com/part-1/section-1#exercises-11-12)
```
~> docker container run -d nginx
939b991eba3384a5c8c8c890e2708a1be4a7f98d7de39e58f9138dafef19def0
~> docker run -d nginx
78521a97f0a5cac85caf54854f7556836d501e0337068a243f1e3626662e546a
~> docker run -d nginx
990d272c084e8f230d9cfaaf0c18fdc686873c8e45cdfef7eef326754769fcc9
~> docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS     NAMES
990d272c084e   nginx     "/docker-entrypoint.…"   3 seconds ago    Up 3 seconds    80/tcp    peaceful_shtern
78521a97f0a5   nginx     "/docker-entrypoint.…"   8 seconds ago    Up 8 seconds    80/tcp    eager_ptolemy
939b991eba33   nginx     "/docker-entrypoint.…"   12 seconds ago   Up 12 seconds   80/tcp    kind_galois
~> docker stop 990
990
~> docker container stop eager_ptolemy
eager_ptolemy
~> docker ps -a | grep nginx
990d272c084e   nginx             "/docker-entrypoint.…"   25 seconds ago   Exited (0) 17 seconds ago                            peaceful_shtern
78521a97f0a5   nginx             "/docker-entrypoint.…"   30 seconds ago   Exited (0) 5 seconds ago                             eager_ptolemy
939b991eba33   nginx             "/docker-entrypoint.…"   34 seconds ago   Up 33 seconds               80/tcp                   **kind_galois**
```


### [1.2: CLEANUP](https://devopswithdocker.com/part-1/section-1#exercises-11-12)
```
~> docker ps -a  
54e35d3bbfc7   nginx             "/docker-entrypoint.…"   11 seconds ago   Up 9 seconds               80/tcp                   quizzical_clarke
990d272c084e   nginx             "/docker-entrypoint.…"   4 minutes ago    Exited (0) 3 minutes ago                            peaceful_shtern
939b991eba33   nginx             "/docker-entrypoint.…"   4 minutes ago    Up 4 minutes               80/tcp                   kind_galois
~> docker stop 54e3
54e3
~> docker stop 939b
939b
~> docker ps -a  
54e35d3bbfc7   nginx             "/docker-entrypoint.…"   41 seconds ago   Exited (0) 10 seconds ago                            quizzical_clarke
990d272c084e   nginx             "/docker-entrypoint.…"   4 minutes ago    Exited (0) 4 minutes ago                             peaceful_shtern
939b991eba33   nginx             "/docker-entrypoint.…"   4 minutes ago    Exited (0) 4 seconds ago                             kind_galois
~> docker container rm 54e
54e
~> docker rm peaceful_shtern
peaceful_shtern
~> docker rm 939
939
~> docker ps -a  
~> docker images  
nginx               latest    e4720093a3c1   4 weeks ago     187MB
~> docker image rm nginx
Untagged: nginx:latest
Untagged: nginx@sha256:c26ae7472d624ba1fafd296e73cecc4f93f853088e6a9c13c0d52f6ca5865107
Deleted: sha256:e4720093a3c1381245b53a5a51b417963b3c4472d3f47fc301930a4f3b17666a
Deleted: sha256:583de6ce675ade688fa76e7c18948b4907557a139e12825ae85e5a8c947e2c89
Deleted: sha256:1084f34dba33ee0238270b757d7d4c3ffa06fcac38f1be5bf26bf35d8982eb17
Deleted: sha256:eb8c0a03ddeb2a6164cddaa21c9795cf8e20dbe788ed6bcaa9cc2b5a58fa8aff
Deleted: sha256:3a4f946657e22d88014e3063827b07c83ac6d999d7f7b19618037bcee5c5f009
Deleted: sha256:0c2e669c3c8abe5ce516bd0ffbb3dec76614a9cd1dec058a7c4815a403adee83
Deleted: sha256:0814ebf6e0ed919bf8bf686038d645aa2b535eb9a6bc4b58b2df1b31d499fe3d
~> docker images  
```
### [1.3: SECRET MESSAGE](https://devopswithdocker.com/part-1/section-2#exercise-13)
```
~> docker run -d --name secret-container devopsdockeruh/simple-web-service:ubuntu
~> docker exec -it secret-container bash
2024-03-21 02:32:08 +0000 UTC
2024-03-21 02:32:10 +0000 UTC
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
```
### [1.4:MISSING DEPENDENCIES](https://devopswithdocker.com/part-1/section-2#exercise-14)
```
~> docker run -it --name web-searcher ubuntu sh -c 'while true; do echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website; done'
-----------------------------------
add this to daemon.json
{
    "dns": 
    [
        "8.8.8.8"
    ]
}
-----------------------------------
# install curl 
docker exec -it web-searcher bash
root@ba48c5d546ac:/# apt-get update && apt-get -y install curl
# output: 
Input website:
helsinki.fi
Searching..
<html>
<head><title>301 Moved Permanently</title></head>
<body>
<center><h1>301 Moved Permanently</h1></center>
<hr><center>nginx/1.22.1</center>
</body>
</html>
Input website:
```
### [1.5: SIZES OF IMAGES](https://devopswithdocker.com/part-1/section-3#exercises-15---16)
```
REPOSITORY                          TAG               IMAGE ID       CREATED       SIZE
devopsdockeruh/simple-web-service   ubuntu            4e3362e907d5   3 years ago   83MB
devopsdockeruh/simple-web-service   alpine            fd312adc88e0   3 years ago   15.7MB
```
### [1.6: HELLO DOCKER HUB](https://devopswithdocker.com/part-1/section-3#exercises-15---16)
```
[root@nagendra-PC nagendra]# docker run -it devopsdockeruh/pull_exercise
Unable to find image 'devopsdockeruh/pull_exercise:latest' locally
latest: Pulling from devopsdockeruh/pull_exercise
8e402f1a9c57: Pull complete 
5e2195587d10: Pull complete 
6f595b2fc66d: Pull complete 
165f32bf4e94: Pull complete 
67c4f504c224: Pull complete 
Digest: sha256:7c0635934049afb9ca0481fb6a58b16100f990a0d62c8665b9cfb5c9ada8a99f
Status: Downloaded newer image for devopsdockeruh/pull_exercise:latest
Give me the password: basics
You found the correct password. Secret message is:
"This is the secret message"
```
### [1.7: IMAGE FOR SCRIPT](https://devopswithdocker.com/part-1/section-3#exercises-17---18)
```
# dockerfile
FROM ubuntu:22.04

RUN apt-get update && apt-get install -y curl

WORKDIR /usr/src/app 

COPY script.sh .

RUN chmod +x ./script.sh

CMD ./script.sh

```
### [1.8: TWO LINE DOCKERFILE](https://devopswithdocker.com/part-1/section-3#exercises-17---18)
```
# dockerfile
FROM devopsdockeruh/simple-web-service:latest

CMD server
# command to run
~> docker build . -t web-server:v1
~> docker run web-server:v1
```
### [1.9: VOLUMES](https://devopswithdocker.com/part-1/section-5#exercise-19)
```
~> docker run -v "$(pwd)/text.log:/usr/src/app/text.log" devopsdockeruh/simple-web-service
```
### [1.10: PORTS OPEN](https://devopswithdocker.com/part-1/section-5#exercise-110)
```
~> docker run -p 8080:8080 web-service
```
### [1.11: SPRING](https://devopswithdocker.com/part-1/section-6#exercises-111-114)
```
# dockerfile

FROM amazoncorretto:8-alpine3.19

WORKDIR /usr/src/app

EXPOSE 8080

COPY . . 

RUN ./mvnw package 

CMD ["java", "-jar", "./target/docker-example-1.1.3.jar"]
```
### [1.12: HELLO, FRONTEND!](https://devopswithdocker.com/part-1/section-6#exercises-111-114)
```
# dockerfile

FROM node:16

WORKDIR /usr/src/app

EXPOSE 5000

COPY package* ./

RUN npm install 

COPY . . 

RUN npm run build 

RUN npm install -g serve 

CMD ["serve", "-s", "-l", "5000", "build"]
```
### [1.13: HELLO, BACKEND!](https://devopswithdocker.com/part-1/section-6#exercises-111-114)
```
# dockerfile

FROM golang:1.16

WORKDIR /usr/src/app

COPY . . 

EXPOSE 8080

RUN go build 

RUN go test ./...

CMD ["./server"]

command used:
~> docker run -p 8080:8080 dockerized-example-backend
```
### [1.14: 1.14: ENVIRONMENT](https://devopswithdocker.com/part-1/section-6#exercises-111-114)
```
# frontend dockerfile

FROM node:16

WORKDIR /usr/src/app

EXPOSE 5000

COPY package* ./

RUN npm install 

COPY . . 

ENV REACT_APP_BACKEND_URL=http://localhost:8080

RUN npm run build 

RUN npm install -g serve 

CMD ["serve", "-s", "-l", "5000", "build"]

# backend dockerfile

FROM golang:1.16

WORKDIR /usr/src/app

COPY . . 

ENV PORT=8080

ENV REQUEST_ORIGIN=http://localhost:5000

EXPOSE 8080

RUN go build 

RUN go test ./...

CMD ["./server"]

# commands used
~> docker run -p 8080:8080 dockerized-example-backend
~> docker run -p 5000:5000 dockerized-example-frontend

```
### [1.15: HOMEWORK](https://devopswithdocker.com/part-1/section-6#exercises-115-116)
```
# dockerfile for my own spring boot application

FROM maven:3.8.3-openjdk-17 AS build

COPY src /home/app/src

COPY pom.xml /home/app

COPY readme.md /home/app/

RUN mvn -f /home/app/pom.xml clean package -DskipTests

EXPOSE 8080

ENTRYPOINT ["java","-jar","/home/app/target/TinyURL-0.0.1-SNAPSHOT.jar"]

```
  [docker-hub url 👈️](https://hub.docker.com/repository/docker/nagendra9/tiny-url-backend/general)

### [1.16: CLOUD DEPLOYMENT](https://devopswithdocker.com/part-1/section-6#exercises-115-116)
Cloud deployment of an image using [render.com](https://render.com/)
```
# dockerfile

FROM ruby:3.1.0

EXPOSE 3000

WORKDIR /usr/src/app

RUN gem install bundler:2.3.3

COPY Gemfile* ./

RUN bundle install 

COPY . . 

RUN rails db:migrate RAILS_ENV=production

RUN rake assets:precompile

CMD ["rails", "s", "-e", "production"]amazoncorretto

Steps:
1. We need to build the image
2. Push the image to docker-hub
3. Go to render.com and click on new web service link
4. Click on advanced image option
5. Give the docker image url which is available through docker-hub in the render.com link option
6. That's it, render.com will download the image and deploy the service live.
```
live link: [https://rails-project-latest.onrender.com/](https://rails-project-latest.onrender.com/)