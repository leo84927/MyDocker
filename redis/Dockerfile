# redis

# 基本 Image (指定容器的作業系統)
FROM redis:latest

# 維護者
MAINTAINER Leo

# For security settings uncomment, make the dir, copy conf, and also start with the conf, to use it
RUN mkdir -p /usr/local/etc/redis
COPY redis.conf /usr/local/etc/redis/redis.conf

CMD ["redis-server", "/usr/local/etc/redis/redis.conf"]