##### Dockerfile for React applications #####
## Build stage: Compile the React application using Node.js
FROM node:18.18-alpine as build

WORKDIR /app
COPY . .
## Install dependencies
RUN npm install
## Build the React application
RUN npm run build

## Runtime stage: Use a lightweight Nginx image to serve the compiled application
FROM nginx:alpine

COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]