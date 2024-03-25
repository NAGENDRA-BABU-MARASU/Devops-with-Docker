FROM alpine:3.19

WORKDIR /usr/src/app

COPY hello.sh . 

RUN touch additional.txt 

RUN chmod +x hello.sh 

CMD ./hello.sh