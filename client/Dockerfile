FROM node:alpine as builder

WORKDIR '/app'

COPY ./package.json ./

RUN npm install -g npm@7.19.0

RUN npm i react-scripts

COPY . .

RUN npm run build

FROM nginx

EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

COPY --from=builder /app/build /usr/share/nginx/html