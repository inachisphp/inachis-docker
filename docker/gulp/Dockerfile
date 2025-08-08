FROM node:current-slim

RUN apt-get update
RUN npm install -g gulp

WORKDIR /var/www/inachis
CMD ["gulp", "watch"]
