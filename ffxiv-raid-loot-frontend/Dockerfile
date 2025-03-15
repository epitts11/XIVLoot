FROM node:alpine as build

WORKDIR /app

COPY ./ffxiv-raid-loot-frontend/package*.json ./

RUN npm install

RUN npm install -g @angular/cli

COPY . .

RUN cd ./ffxiv-raid-loot-frontend \ 
node_modules/.bin/ng build --configuration=production

FROM nginx:latest

COPY ./ffxiv-raid-loot-frontend/nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=build ./ffxiv-raid-loot-frontend/dist/ffxiv-raid-loot-web-app/browser /usr/share/nginx/html

EXPOSE 80
