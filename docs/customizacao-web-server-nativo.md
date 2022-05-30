# Customizando o projeto para rodar um web server nativo

Por padrão o sail usa um servidor web do php. Para o ambiente de desenvolvimento em projetos pequenos é mais que o suficiente. Contudo, quando precisamos rodar em produção necessitamos de um servidor mais consolidado e iremos instalar o nginx para esta atividade.

Para esta finalidade vamos publicar as configurações e personalizar os containers do docker ao nosso favor conforme a documentação em

https://laravel.com/docs/9.x/sail#sail-customization

```
sail artisan sail:publish
```
Vamos descobrir novos arquivos que foram publicados com o comando git:
```
git status
```
Desligar os conteiners:
```
sail down -v
```

## Publicar apenas a versão 8.1 do php

Limpar outras versões de php e deixar numa estrutura mais visível:
```
mkdir -p docker/php
mv docker/8.1 docker/php
rm -rf docker/8.0 docker/7.4
```
Modificar o arquivo docker/php/8.1/supervisord.conf

```
[supervisord]
nodaemon=true
user=root
logfile=/var/log/supervisor/supervisord.log
pidfile=/var/run/supervisord.pid

# [program:php]
# command=/usr/bin/php -d variables_order=EGPCS /var/www/html/rtisan serve --host=0.0.0.0 --port=80
# user=sail
# environment=LARAVEL_SAIL="1"
# stdout_logfile=/dev/stdout
# stdout_logfile_maxbytes=0
# stderr_logfile=/dev/stderr
# stderr_logfile_maxbytes=0

[program:php-fpm]
command=/usr/sbin/php-fpm8.1 --nodaemonize --fpm-config=/etc/php/8.1/fpm/pool.d/www.conf
user=sail
autostart=true
autorestart=true
priority=5
stdout_logfile=/dev/stdout
stdout_logfile_maxbytes=0
stderr_logfile=/dev/stderr
stderr_logfile_maxbytes=0
```

Criar o arquivo docker/php/8.1/www.conf

Alterar o docker/php/8.1/Dockerfile

>adicionar o php8.1-fpm
>adicionar linha 55:
>```
>COPY www.conf /etc/php/8.1/fpm/pool.d/www.conf
>```

Alteração no .devcontainer/devcontainer.json
De:
```
"service": "laravel.test",
```
Por:
```
"service": "php",
```

Adicionar no .env
```
APP_SERVICE=php
```

Alterar arquivo docker-compose.yml

## Servidor Web para proxy
**Nginx**
Página e documentação do projeto:
https://www.nginx.com/

Após eu copiar alguns arquivos de definição do container nginx em docker/nginx vamos realizar o *build* novamente os containers e fazer rodar:

Para buildar vamos rodar:
```
sail build
```
Subir novamente o container
```
sail up -d
```
Certificar que está rodando no nginx:
```
curl --head http://localhost/
```

Desligar os containers:
```
sail down -v
```
