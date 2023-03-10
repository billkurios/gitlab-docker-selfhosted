# Self hosted Gitlab Docker

Install monolithic gitlab on-premise version.

## Set up volumes location
Linux users
```sh
export GITLAB_HOME=/srv/gitlab
```

MacOs users
```sh
export GITLAB_HOME=$HOME/gitlab
```

**Make sure you have the gitlab folder exist or have been created.**

## Gitlab installation
### Get the repository on your server
```sh
git clone https://github.com/billkurios/gitlab-docker-selfhosted.git
```
### Setup the secrets file
In the gitlab-docker-selfhosted, create **.env.secrets** file and setup these variables
 ```yml
GITLAB_HOME='/srv/gitlab'
HOSTNAME='gitlab.domain.com'
HTTPS_URL='https://gitlab.domain.com'
HTTP_PORT=80
HTTPS_PORT=443
SSH_PORT=22
CONTACT_EMAIL='info@domain.com'
SSL_RENEW_HOUR=2
SSL_RENEW_MINUTE=30
SSL_RENEW_DAY_OF_MONTH=7
SMTP_GMAIL_PWD='your_password'
SMTP_GMAIL_ADDRESS='your_email@gmail.com'
ALERT_ADMIN_EMAIL='alert_manager_mail@domain.com'
GITLAB_VERSION=15.6.7-ce.0
EDITION_TYPE='ce'
```

**EDITION_TYPE** key is used to specify if we used community edition **ce** or enterprise edition **ee** of gitlab.

### Run the docker-compose file with the secret file
 ```sh
docker compose --env-file .env.secrets up -d
```