FROM nginx
RUN rm -rf /usr/share/nginx/html/*
COPY code /usr/share/nginx/html/
COPY frontend-nginx.conf /etc/nginx/default.d/frontend.conf