# 🐳 Template Docker Para Laravel

## 📖 Descrição

Este projeto é um template Docker para utilização em projetos Laravel, facilitando a configuração do ambiente de desenvolvimento.

## 🗂️ Estrutura do Projeto

A estrutura do projeto é organizada da seguinte forma:

```shell
.
├── .dockerignore
└── docker
    ├── Dockerfile
    ├── configs
    │   ├── nginx.conf.template
    │   └── upload.ini
    ├── dev
    │   └── docker-compose.yml
    └── prod
        └── docker-compose.yml
```

- `.dockerignore`: Especifica os arquivos e diretórios que devem ser ignorados pelo Docker.
- `configs`: Pasta com as configurações do Nginx e PHP-FPM.
- `docker/dev`: Contém a configuração Docker para o ambiente de desenvolvimento.
- `docker/prod`: Contém a configuração Docker para o ambiente de produção.

## 🚀 Instruções de Uso

Siga os passos abaixo para configurar e iniciar o ambiente Docker para o seu projeto Laravel:

1. Clone o repositório para a sua máquina local:

```shell
git clone https://github.com/AlexandreRiff/docker-template-laravel.git
```

2. Navegue até o diretório do projeto:

```shell
cd docker-template-laravel
```

3. Copie a pasta `docker` e o arquivo `.dockerignore` para o diretório raiz do seu projeto Laravel.

```shell
cp -R docker .dockerignore seu_projeto_laravel
```

4. Configure as variáveis de ambiente no arquivo `.env` do Laravel:

```shell
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laravel
DB_PASSWORD=laravel

SESSION_DRIVER=redis

QUEUE_CONNECTION=redis

CACHE_STORE=redis

REDIS_CLIENT=phpredis
REDIS_HOST=redis
REDIS_PASSWORD=laravel
REDIS_PORT=6379

MAIL_MAILER=smtp
MAIL_HOST=mailhog
MAIL_PORT=1025
```

5. Construa e Suba os Containers

```shell
cd docker/dev && docker-compose up -d --build
```

## 📦 Instalando Extensões PHP

Para instalar extensões PHP em um ambiente Docker, foi utilizado o script [docker-php-extension-installer](https://github.com/mlocati/docker-php-extension-installer?tab=readme-ov-file), desenvolvido por [Michele Locati](https://github.com/mlocati).

Para adicionar novas extensões, basta incluir a extensão desejada na instrução `RUN install-php-extensions` dentro do `Dockerfile`.

Exemplo:

```shell
RUN install-php-extensions \
    zip \
    pdo_mysql \
    redis
```
