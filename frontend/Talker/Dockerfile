# Этап 1: сборка проекта 
FROM node:18-alpine as build 
WORKDIR /app 
COPY package.json ./ 
RUN npm install 
COPY . . 
RUN npm run build 
# Этап 2: nginx-сервер 
FROM nginx:alpine 
# Удаляем дефолтную заглушку 
RUN rm -rf /usr/share/nginx/html/* 
# Копируем собранный frontend из предыдущего этапа 
COPY --from=build /app/dist /usr/share/nginx/html 
EXPOSE 80 