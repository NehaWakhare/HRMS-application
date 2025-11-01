#step1:build angular app
FROM node:18-alpine AS build 
WORKDIR /app
COPY package*.json ./
RUN npm install 
COPY . .
RUN npm run build --prod
#step2:serve with nginx
FROM nginx:alpine
COPY --from=build /app/dist/hrms/usr/share/nginx/html
EXPOSE 80
CMD ["nginx","-g","daemon off;"]

