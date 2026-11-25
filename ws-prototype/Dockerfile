# Container Apps (Cloud.ru) runs containers as NON-ROOT with an almost read-only root FS.
# A plain nginx:alpine base crash-loops there:
#   nginx: [emerg] mkdir() "/var/cache/nginx/client_temp" failed (13: Permission denied)
# Therefore: unprivileged image + unprivileged port 8080.
FROM nginxinc/nginx-unprivileged:1.27-alpine

# Server config (the image's main nginx.conf already points pid/temp paths to writable dirs).
COPY nginx.conf /etc/nginx/conf.d/default.conf

# The whole app is a single self-contained HTML file.
COPY index.html /usr/share/nginx/html/index.html

EXPOSE 8080
