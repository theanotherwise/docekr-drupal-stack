FROM nginx:1.19.6-alpine
# root -> /usr/share/nginx/html

COPY ./archives/drupal-9.1.2.zip .

COPY ./files/default.conf /etc/nginx/conf.d/default.conf
RUN chown nginx:nginx /etc/nginx/conf.d/default.conf

RUN apk add --no-cache unzip && \
    unzip -q drupal-9.1.2.zip && \
    mv drupal-9.1.2/* /usr/share/nginx/html/ && \
    rm -rf drupal-9.1.2.zip drupal-9.1.2

RUN mkdir /usr/share/nginx/html/sites/default/files && \
    chmod -R 777 /usr/share/nginx/html/sites/default/files