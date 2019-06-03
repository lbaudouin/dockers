FROM ubuntu:18.04

RUN apt-get update && apt-get -y upgrade

RUN apt-get install -y git
RUN git config --global user.email "baudouin.leo@gmail.com"
RUN git config --global user.name "Léo Baudouin"

RUN apt-get install -y npm
RUN npm install -g npm@latest
RUN npm install -g @angular/cli

RUN npm install --save-dev @angular-devkit/build-angular
RUN npm install --save-dev @angular/compiler-cli
RUN npm install --save-dev @angular/compiler

WORKDIR /sources

EXPOSE 8082
EXPOSE 4200

# ng serve --host 0.0.0.0
