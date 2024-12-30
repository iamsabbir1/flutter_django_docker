# Use the Flutter base image
FROM ghcr.io/cirruslabs/flutter:3.27.1

# Set the working directory
WORKDIR /app

# Copy Flutter project files
COPY . .

# Get dependencies
RUN flutter pub get

# Build the Flutter app
RUN flutter build web

# Use nginx to serve the Flutter app
FROM nginx:stable
COPY --from=0 /app/build/web /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
