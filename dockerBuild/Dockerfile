FROM nginx:alpine
ARG VERSION

WORKDIR /usr/share/nginx/html

RUN echo "Building a custom Nginx image with TAG version: $VERSION"

EXPOSE 80
ENTRYPOINT ["nginx", "-g", "daemon off;"]