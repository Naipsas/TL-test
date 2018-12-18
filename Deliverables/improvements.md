# Improvements

This file has a list of proposals to improve this deployment.

1. To improve `Composer` usage, we could define inside `~/.bashrc` file in our host a function which makes for us the docker run call, allowing it to be as easy as executing the alias we choose as `composer` (e.g.).

2. Same way, we could improve `phpunit` usage creating a little script which would allow us to use `phpunit` command on our host, as is [proposed in the docs](https://hub.docker.com/r/phpunit/phpunit/).

3. Docker-compose has built-in password in our case, and this is a security concern. For production environment, other patterns like providing the credentials through an external file (not in repositories) or using a script to obtain them would be a must to avoid it.

## Comments

1. Inside `index.php`, you define a `redis_username`. Isn't redis [password-only auth](https://redis.io/commands/auth)?