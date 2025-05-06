FROM node:18.16.0-alpine

WORKDIR /app

COPY frontend-user/package*.json ./

RUN npm install

COPY frontend-user/ .

RUN npm run build

FROM nginx:alpine
COPY --from=0 /app/build /usr/share/nginx/html
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]