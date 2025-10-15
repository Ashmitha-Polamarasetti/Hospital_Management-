# Build stage
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
COPY start-frontend.sh .
RUN chmod +x start-frontend.sh

# Production stage
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
CMD ["/app/start-frontend.sh"]
