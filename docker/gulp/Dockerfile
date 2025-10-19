FROM node:current-slim

WORKDIR /var/www/inachis

RUN npm install -g gulp-cli
RUN apt-get update

COPY package*.json ./
RUN npm install

COPY . .

CMD ["gulp"]
