# Improvements

This file has a list of proposals to improve this deployment.

1. To improve `Composer` usage, we could define inside `~/.bashrc` file in our host a function which makes for us the docker run call, allowing it to be as easy as executing the alias we choose as `composer` (e.g.).

2.

## Comments

1. Inside `index.php`, you define a `redis_username`. Isn't redis [password-only auth](https://redis.io/commands/auth)?