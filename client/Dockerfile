FROM node:alpine as web_builder
WORKDIR /app
COPY ./package.json ./
RUN yarn install
COPY ./ ./
RUN yarn build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=web_builder /app/build /usr/share/nginx/html