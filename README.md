# Atividades

## Instalar vagrant

**Criar diretorio Vagrant**


```mkdir vagrant```

**Instalar vagrant**

```apt-get install vagrant```

**Baixar a imagem cento ( pegar o nome da image que deseja subir na maq virtual )
https://app.vagrantup.com/boxes/search**

*Criar vagrant file*

```vagrant init```

**Editar o vagrant file**

```vim vagrantfile```

- descomentar e editar a linha “config.vm.box = (colocar o nome da iso)”</p>
- descomentar a linha “config.vm.network "private_network", ip: "192.168.33.11"</p>
- config.vm.provider "virtualbox" do |vb|</p>
- descomentar a vb.memory = "1024":</p>

**Conectar no vagrant**

```vagrant ssh```

## Nginx

**Adicionar o repositório do Centos 7 EPEL**

```sudo yum install epel-release```

```sudo yum install nginx```

## Instalando

```sudo yum install mariadb-server mariadb```

**Iniciar o banco**

```sudo systemctl start mariadb```

*Executar um script de segurança para remova alguns padrões perigosos e bloqueie o acesso ao sistema*

```sudo mysqlsecureinstallation```


**Permitir que o banco inicie na inicialização**

```sudo systemctl enable mariadb```

# Php

## Instalar PHP

```sudo yum install php```

**Editar /etc/ṕhp-fpm.d/www.conf**

```vim /etc/php-fpm.d/www.conf```

*Alterar a linha que definem o user e o group  altere seus valores de “apache” para “nginx” ( para que o php tenha comunicação com o nginx)*

- user = nginx

- group = nginx

**Iniciar e habilitar o php**

```sudo systemctl start php-fpm```

```sudo systemctl enable php-fpm```

## Configurar o Nginx para processar páginas PHP

**Criar o arquivo**

```sudo vim /etc/nginx/conf.d/default.conf```

*Na linha  server_name  localhost (Inserir o ip);*

Após a alteração reiniciar o nginx

```sudo systemctl restart nginx</p>```

## Teste o processamento PHP

**Criar o arquivo info.php:**

```sudo vim /usr/share/nginx/html/info.php```

**Insira o codigo:**

```<?php phpinfo(); ?>```

**Salva e fecha o arquivo**

```:wr```

**Para testar**

**Abra em um navegador da web:**

- http://endenrecoIPdoservidor/info.php

# Wordpres

**download do wordpress**

```wget http://wordpress.org/latest.zip```

**descompactar o arquivo.zip**

```unzip latest.zip```

**Mover o diretório wordpress para diretório /usr/share/nginx/html/**

```mv * /usr/share/nginx/html/</p>```

**Alterar o dono do arquivo**

```chown nginx.nginx -R *```

**Abrir o wordpress no navegador**

- http://192.168.33.11/wp-admin/setup-config.php?step=0

# Configurando o banco de dados remoto para otimizar o desempenho do site

### Criar a VM para o banco de dados

**Criar diretorio Vagrant**

  ```mkdir vmb```

**Criar vagrant file**

  ```vagrant init``` 


**Editar o vagrant file**

```vim vagrantfile```

- descomentar e editar a linha “config.vm.box = (colocar o nome da iso)”
- descomentar a linha “config.vm.network "private_network", ip: "192.168.33.20"
- config.vm.provider "virtualbox" do |vb|
- descomentar a vb.memory = "1024"*

**Conectar no vagrant**

```vagrant ssh```

**Adicionar o repositório do Centos 7 EPEL**

```sudo yum install epel-release```


**Instalando MariaDB**

```sudo yum install mariadb-server mariadb```

**Iniciar o banco**

```sudo systemctl start mariadb```

*Executar um script de segurança para remova alguns padrões perigosos e bloqueie o acesso ao sistema*

```sudo mysql<em>secure</em>installation```

**Permitir que o banco inicie na inicialização**

```sudo systemctl enable mariadb```

**Configurando o banco de dados para acesso remoto**

```mysql>   CRIAR DATABASE wordpress;```

**Criando um usuario local**

```mysql> CREATE USER 'wordpressuser'@'localhost' IDENTIFIED BY 'password';```

**Concedendo privilegio**

```mysql> GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'localhost';```

**Criando um usuário para conexão remota**

```mysql> CREATE USER 'wordpressuser'@'web-server_ip' IDENTIFIED BY 'password';```

**Concedendo previlegio**

```GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'web_server_ip';```

**Liberar os privilegios e gravar no disco**

```mysql> FLUSH PRIVILEGES;```

**Sair do banco**

```mysql> exit```

