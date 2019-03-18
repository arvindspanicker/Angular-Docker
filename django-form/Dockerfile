# Setting up the angular application
FROM node:8.11.2-alpine as node
WORKDIR /code/src/webapp
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Setting the nginx
FROM nginx:1.13.12-alpine
COPY --from=node /code/src/webapp/dist/ /usr/share/nginx/html
RUN rm /etc/nginx/conf.d/default.conf
COPY server_conf/nginx.conf /etc/nginx/conf.d
