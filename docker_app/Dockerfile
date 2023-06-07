#React Dockerfile
#pull official base image
FROM node:16.18.0 AS build
#set working dir
WORKDIR /app
#install dependencies
COPY package.json package.json
RUN yarn
#add app
COPY . .
#build
RUN yarn run build

#nginx configuration
FROM nginx:1.18.0
COPY --from=build /app/dist /opt/site
COPY docker/nginx.conf /etc/nginx/nginx.conf


