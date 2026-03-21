##### Dockerfile for Vue and Angular applications #####
## Build stage: Compile the Vue or Angular application using Node.js
FROM node:18.18-alpine as build
WORKDIR /app
COPY . .
RUN npm install 
RUN npm run build

## Runtime stage: Use a lightweight Nginx image to serve the compiled application
FROM nginx:alpine
RUN mkdir /run
COPY --from=build /app/dist /run
COPY nginx.conf /etc/nginx/nginx.conf
