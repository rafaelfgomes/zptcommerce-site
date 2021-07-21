FROM node:alpine

ARG API_URL

ENV API_URL=${API_URL}

WORKDIR /app

COPY ./site .

CMD [ "sh", "-c", "npm install && chmod -R 777 node_modules && npm run serve" ]