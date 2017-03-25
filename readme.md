# Miscellaneous Dockerfiles

A collection of Dockerfiles that I've found useful for local development. Some may turn into maintained projects, but most are pretty minimally useful.

## What's here?

### PHP-FPM

A general php-fpm container with MySQL included.

```bash
docker build -t shiphp/php-fpm-mysql ./php-fpm-mysql
```

### PHPUnit

A php-cli container for running unit tests with mysql and pgsql included.

```bash
docker build -t shiphp/phpunit ./phpunit
```

### Simple SSH

Containerized access to your remote servers for tasks like deploying code or running remote builds.

```bash
docker build -t shiphp/simple-ssh ./simple-ssh
```

- Create your own ssh key and make sure its permissions are strict enough: `chmod 600 ~/.ssh/id_rsa`.
- Mount your `.ssh` directory as a volume into this image and run the container: `docker run -it -v ~/.ssh:/root/.ssh shiphp/simple-ssh /bin/ash`
    - You are now logged into the container and can run `ssh` commands, eg: `ssh admin@myserver.com`.
    - Alternatively, you can log directly into the server by running `docker run -it -v ~/.ssh:/root/.ssh shiphp/simple-ssh ssh admin@myserver.com`