FROM node:24-alpine AS build

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm ci

COPY . .
RUN npm run build

FROM nginx:alpine

ARG VERSION=dev
LABEL org.opencontainers.image.version=$VERSION

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80
