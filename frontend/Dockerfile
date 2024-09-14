FROM nginx
# remove the default index page
RUN rm -rf /usr/share/nginx/html/index.html
# remove the nginx.conf and conf.d/default.conf(these files are act as viewed so we need to remove compulsory)
RUN rm -rf /etc/nginx/nginx.conf
RUN rm -rf /etc/nginx/conf.d/default.conf
# google--running nginx container as a normal user(configuration setups mandatory)
RUN mkdir -p /var/cache/nginx/client_temp && \
        mkdir -p /var/cache/nginx/proxy_temp && \
        mkdir -p /var/cache/nginx/fastcgi_temp && \
        mkdir -p /var/cache/nginx/uwsgi_temp && \
        mkdir -p /var/cache/nginx/scgi_temp && \
        chown -R nginx:nginx /var/cache/nginx && \
        chown -R nginx:nginx /etc/nginx/ && \
        chmod -R 755 /etc/nginx/ && \
        chown -R nginx:nginx /var/log/nginx
RUN touch /var/run/nginx.pid && \
    chown -R nginx:nginx /var/run/nginx.pid /run/nginx.pid
# nginx recognize nginx.conf only so our project.conf(expense.conf)-->moved to nginx.conf
COPY expense.conf /etc/nginx/nginx.conf
# code (folder) copy into default path : /usr/share/nginx/html/ 
COPY code /usr/share/nginx/html/
# set the user as a non root user (no when can enter through the host port in our container secure)
USER nginx
