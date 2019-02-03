FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build --production

FROM nginx
EXPOSE 3000
COPY ./nginx/client.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html