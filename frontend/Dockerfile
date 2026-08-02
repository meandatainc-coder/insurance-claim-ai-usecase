# Stage 1: Build Angular App
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build -- --configuration production

# Stage 2: Serve via Nginx (Used during deployment to S3/CDN or local test)
FROM nginx:alpine
COPY --from=build /app/dist/your-app-name/browser /usr/share/nginx/html
EXPOSE 80
