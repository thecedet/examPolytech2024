FROM node:10-alpine AS builder
WORKDIR /app
COPY . .
RUN npm install 
RUN npm run build --configuration=production

FROM nginx:alpine
COPY nginx/ /etc/nginx/
COPY --from=builder /app/dist/*/* /usr/share/nginx/html

COPY entrypoint.sh /docker-entrypoint.d/entrypoint.sh

LABEL maintainer="Clé(ment)"