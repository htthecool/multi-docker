FROM node:14.14.0-alpine as builder

WORKDIR '/app'

COPY ./package.json ./

RUN yarn install

COPY ./ ./

RUN yarn run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.production.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
