# build
FROM node:14-alpine as builder
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# release
FROM nginx:1.25-alpine
COPY --from=builder /usr/src/app/dist/frontend /usr/share/nginx/html
EXPOSE 80
