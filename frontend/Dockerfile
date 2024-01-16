FROM node:16-alpine AS build-step
ENV NODE_ENV production

WORKDIR /app

COPY package.json .
COPY package-lock.json .
RUN npm install

COPY src ./src
COPY public ./public
RUN npm run build

FROM nginx:1.18-alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build-step /app/build /app/build