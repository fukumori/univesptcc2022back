# Instalação do projeto em Laravel

- [x] [Instalar o Laravel](#instalação-do-laravel)
- [x] [Trabalhando com contâiners usando o Laravel Sail](#trabalhando-com-containers-usando-o-laravel-sail)
- [x] [Conferir os serviços instalados no ambiente de desenvolvimento](conferir-os-serviços-instalados-no-ambiente-de-desenvolvimento)
## Instalação do laravel
Página e documentação do projeto:
[laravel](https://laravel.com/)
[instalalação](https://laravel.com/docs/9.x/installation)
[instalação no windows](https://laravel.com/docs/9.x/installation#getting-started-on-windows)

https://laravel.com/docs/9.x/installation#choosing-your-sail-services

```
curl -s "https://laravel.build/univesptcc2022back?with=mariadb,redis,mailhog&devcontainer" | bash

```

### Inserindo um alias para o sail
```
sail
```
configurar um alias:
https://laravel.com/docs/9.x/sail#configuring-a-bash-alias
```
code ~/.bash_aliases
```
Inserir no arquivo:
```
alias sail='[ -f sail ] && bash sail || bash vendor/bin/sail'
```
Carregar o arquivo:
```
source ~/.bash_aliases
```
Chamar o sail e ver que está funcionando
```
sail
```

## Trabalhando com containers usando o Laravel Sail

Verificar que o projeto está com o sail:
```
sail
```
O sail usa o docker-compose por debaixo dos panos:
```
sail --version
```
Não temos nada instalado em nossa máquina:

```
php --version
composer --version
node --version
npm --version
```

Subir pela primeira vez os containers:
```
sail up -d
```
Entrar no container de trabalho:
```
sail shell
```
Verificar que dentro do container de trabalho nós temos todas as ferramentas necessárias para o desenvolvimento:
```
php --version
composer --version
node --version
npm --version
```
Para sair:
```
CTRL+D
```
ou
```
exit
```

Fechar os containers:
```
sail down -v
```

## Conferir os serviços instalados no ambiente de desenvolvimento

### Linguagem de desenvolvimento para o backend
**PHP**
Página e documentação do projeto:
https://www.php.net/

Para verificar a instalação:
```
php --version
```
**Composer**
Página e documentação do projeto:
https://getcomposer.org/

Para verificar a instalação:
```
composer --version
```
### Linguagem de desenvolvimento para o frontend
**Node.js**
Página e documentação do projeto:
https://nodejs.org/en/

Para verificar a instalação:
```
node --version
```
**NPM**
Página e documentação do projeto:
https://www.npmjs.com/

Para verificar a instalação:
```
npm --version
```
**webpack**
Página e documentação do projeto:
https://webpack.js.org/

### Banco de dados relacional
**MariaDB**
Página e documentação do projeto:
https://mariadb.org/

Para verificar a instalação do client:
```
sail shell
mysql --version
```
Para verificar a instalação do servidor:
```
sail exec mariadb bash
mariadbd --version
```
### Cache
**Redis**
Página e documentação do projeto:
https://redis.io/
Para verificar a instalação:
```
sail exec redis sh
redis-server --version
```
### Testes para envio de e-mail
**Mailhog**
Página e documentação do projeto:
https://github.com/mailhog/MailHog
Para verificar a instalação:
```
sail exec mailhog sh
/usr/local/bin/MailHog
```

## Verificando o projeto rodando
Até agora vimos que o projeto foi instalado está funcionando.
Para certificar que os containers estão funcionando devemos rodar de fora do container de desenvolvimento, ou seja em sua máquina:
```
sail ps
```

A coluna status identifica que está funcionando e saudável em alguns casos.

Para rodar o servidor do projeto basta rodar de fora do container de desenvolvimento:
```
sail artisan serve
```
O console ficará travado mas usando o navegador em:
http://localhost
Temos a página de exemplo do laravel.

Para certificar qual servidor web estamos rodando basta chamar de outro terminal:

```
curl --head http://localhost/
```
Para finalizar o servidor basta pressionar ```CTRL+C``` no terminal para finalizar o servidor.
