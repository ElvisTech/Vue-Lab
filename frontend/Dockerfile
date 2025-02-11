# Use Node.js for building Vue app
FROM node:18 AS build

WORKDIR /app
COPY ./ /app

# Install dependencies and build
RUN npm install && npm run build

# Use Nginx to serve the frontend
FROM nginx:alpine

# Copy built Vue app to Nginx web root
COPY --from=build /app/dist /usr/share/nginx/html

# Copy custom Nginx configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 80 for frontend
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
