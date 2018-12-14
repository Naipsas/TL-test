# Backend Image - https://hub.docker.com/_/redis/
FROM redis

# This way we can configure our own credentials
COPY redis.conf /usr/local/etc/redis/redis.conf

# Run redis with our confg file
CMD [ "redis-server", "/usr/local/etc/redis/redis.conf" ]