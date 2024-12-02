### Build Stage
FROM node:16 AS ionic

## Create app directory
WORKDIR /usr/src/app

## Install app dependencies
COPY package*.json ./
RUN npm install -f
#RUN npm ci

## Bundle app source
COPY . .
RUN npm install -g ionic
RUN ionic build

### Run Stage
FROM nginx:alpine

COPY --from=ionic /usr/src/app/www /usr/share/nginx/html