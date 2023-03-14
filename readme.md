## - INSTALAÇÃO DO LINUX UBUNTU - Instale o VM do UBUNTU no VirtualBox, instalei o cockpit pelo terminal do UBUNTU, apontei as portas dentro da VirtualBox para acessar o cockpit em um navegador colocando o seguinte endereço: http://127.0.0.1:9090. IP automático do Linux é: “127.0.0.1”. A PORTA pode ser qualquer uma, mas para uma questão de organização coloquei “9090” e no IP do convidado SEMPRE coloque “10.0.2.15”.

## - DOCKER-COMPOSE, INSTALAÇÃO DO DOCKER, ADMINER E WORDPRESS - Depois de instalar o DOCKER dentro do cockpit usando o seguinte código: sudo apt install docker.Instalei o DOCKER-COMPOSE com o código: sudo apt install docker-compose.Agora para instalar o ADMINER e o WORDPRESS criei um editor de texto usando VIM com o seguinte código: vim docker-compose.yml.

No vim coloquei o código para instalação do ADMINER e o WORDPRESS:

version: '3.1'
services: 
    db:
        image: mysql:latest
        restart: always
        environment:
            MYSQL_ROOT_PASSWORD: senac@123
            MYSQL_DATABASE: site
        ports:
            - '6556-3306'
        volumes:
            - ~/site-db:/var/lib/mysql
        expose: 
            - '3306'
   
    wordpress:
        image: wordpress
        restart: always
        environment:
            WORDPRESS_DB_HOST: db
            WORDPRESS_DB_USER: root
            WORDPRESS_DB_PASSWORD: senac@123
            WORDPRESS_DB_NAME: site
            WORDPRESS_TABLE_PREFIX: ps
        ports:
            - '8084:80'
        volumes:
            - ~/site-wordpress:/var/www/html
    adminer:
        image: adminer
        restart: always
        ports:
            - '8085:8080'

Pra sair, aperte esc e (:q) para sair e salvar use o (:wq)

Execute usando o código: docker-compose up

- CONFIGURAÇÃO DO ADMINER E O WORDPRESS – Logo após a instalação do adminer e
wordpess os IPS e as PORTAS dentro do VirtualBox.
Ubuntu|127.0.0.1|9090|10.0.2.15|9090|
MYSQL_Docker|127.0.0.1|6556|10.0.2.15|6556|
Adminer|127.0.0.1|8085|10.0.2.15|8085
Wordpress IpDaSuaMáquina ou IpAutomáticoDoLinux 8084 10.0.2.15 8084

Para acessar o ADMINER em qualquer navegador: http://127.0.0.1:8085.
Para acessar o WORDPRESS em qualquer navegador: http://10.26.44.26:8084.

## Um MySQL banco de dados é essencial para realizar o gerenciamento do banco de dados em uma tabela, que faz a interligação entre todos os dados e constrói um sistema administrativo de dados muito mais prático e ágil, garantindo que todas as informações estejam bem organizadas e seguras.

## Adminer (anteriormente phpMinAdmin) é uma ferramenta de gerenciamento de banco de dados baseados em PHP, gratuito e de código aberto. É super simples de ser implantado em seu servidor. Para usá-lo, tudo que você tem que fazer é carregar seu único arquivo PHP, apontar seu navegador para ele e fazer o login.

## WORDPRESS criado em 2003, o WordPress veio para democratizar o desenvolvimento de sites. Ou seja, para transformar uma tarefa muito exclusiva em algo possível de ser feito pela maioria dos usuários da internet. Hoje, o WordPress é o Gerenciador de Conteúdo mais popular e utilizado para o desenvolvimento de sites em todo o mundo.