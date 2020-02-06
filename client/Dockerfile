FROM node:alpine as builder

RUN ls

WORKDIR '/app'

RUN ls

#COPY ./package.json ./
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

RUN true

FROM nginx:latest
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html