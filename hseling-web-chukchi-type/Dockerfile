FROM node:lts-alpine as build-stage
WORKDIR /app
COPY hseling-web-chukchi-type/package*.json ./
RUN npm install
COPY hseling-web-chukchi-type/. .
RUN npm run build

# этап production (production-stage)
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html
#EXPOSE 8000
CMD ["nginx", "-g", "daemon off;"]