# Requisitos do sistema

- [x] [Linux like](#linux-like)
- [x] [IDE](#ide)
- [x] [docker / docker-compose](#docker-e-docker-compose)
- [x] [curl](#curl)
- [x] [git](#git)
- [x] [github](#github)

## Linux like

### Linux
Não requer preparação.

### MacOS
[Homebrew](https://brew.sh/index_pt-br)

### Windows 10/11
[WSL2](https://docs.microsoft.com/pt-br/windows/wsl/install)

## IDE

Recomendado:
[vscode](https://code.visualstudio.com/)
Alternativas:
[vim](https://www.vim.org/)
[emacs](https://www.gnu.org/software/emacs/)
[sublime](https://www.sublimetext.com/)
[phpstorm](https://www.jetbrains.com/pt-br/phpstorm/)

## docker e docker-compose
Página e documentação do projeto:
https://www.docker.com/
Para instalar no windows:
https://docs.docker.com/desktop/windows/install/

## curl
Página e documentação do projeto:
https://curl.se/
Para instalar no sistemas baseados em Debian:
```
sudo apt install curl
```
Verificar instalação:
```
curl --version
```

## git
Página e documentação do projeto:
https://git-scm.com/

Para instalar nos sistemas baseados em Debian:
```
sudo apt install git
```
Verificar instalação.
```
git --version
```

## github
Página e documentação do projeto:
https://github.com

Nosso projeto do app:
https://github.com/MrNinso/UnivespTCC2022APP

### Criar um novo projeto no Github
https://github.com/new

Nosso projeto backend:
https://github.com/fukumori/univesptcc2022back

### Como subir as coisas para o repositório

```
git init
git checkout -b main
git remote add origin git@github.com:fukumori/univesptcc2022back.git
git add .
git commit -m "install laravel project"
git push -u origin main
```
Precisamos criar uma chave SSH para acessar o projeto:

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
Para gerar uma nova chave:
Copiar o conteúdo da chave:

```
cat ~/.ssh/id_rsa.pub
```
e salvar nas chaves do github:
https://github.com/settings/keys

Finalmente "salvar" o conteúdo do projeto:
```
git push -u origin main
```
Verificar que o conteúdo foi salvo:
```
git status
```
