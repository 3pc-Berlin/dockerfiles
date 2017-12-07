# CRON 

Cron demon as Docker image for executing cron jobs particularly in other containers using docker in docker

## Usage

Submit the cronjob as command over docker command line or in the docker-compose.yml, e.g.:

```
    cron:
      image: dreipc/cron
      volumes:
        - "/var/run/docker.sock:/var/run/docker.sock"
      restart: always
      command:
        - '* * * * * docker exec php /var/www/public/typo3/cli_dispatch.phpsh scheduler >>/var/log/cron.log 2>&1'
```