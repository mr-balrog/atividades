# atividades
atividade diogo

<p>Vagrant</p>

<p>1º Criar diretorio Vagrant</p>
mkdir vagrant
<p></p>
<p>2° Instalar vagrant</p>
apt-get install vagrant
<p></p>
<p>3° baixar a imagem cento ( pegar o nome da image que deseja subir na maq virtual )</p>
https://app.vagrantup.com/boxes/search
<p></p>
<p>4° Criar vagrant file</p>
vagrant init
<p></p>
<p>5° Editar o vagrant file</p>
vim vagrantfile
<p></p>
<p>descomentar e editar a linha “config.vm.box = (colocar o nome da iso)”</p>
<p></p>
<p>descomentar a linha “config.vm.network "private_network", ip: "192.168.33.11"</p>
<p></p>
<p>config.vm.provider "virtualbox" do |vb|</p>
<p></p>
<p>descomentar a vb.memory = "1024":</p>
<p></p>
<p>6º Conectar no vagrant </p>
vagrant ssh
<p></p>
<p>Nginx</p>

<p>1° Adicionar o repositório do Centos 7 EPEL</P>
sudo yum install epel-release
<p></p>
<p>2° sudo yum install nginx</p>

<p>Mysql ou MariaDB</p>

<p>1° Instalar</p>
sudo yum install mariadb-server mariadb
<p></p>
<p>2° Iniciar o banco</p>
sudo systemctl start mariadb
<p></p>
<p>3° Executar um script de segurança para remova alguns padrões perigosos e bloqueie o acesso ao sistema</p>
sudo mysql<em>secure</em>installation
<p></p>
<p>4° Permitir que o banco inicie na inicialização</p>
sudo systemctl enable mariadb
<p></p>

<p>PHP</p>

<p>1° Instalar o repositório</p>
sudo yum-config-manager --enable remi-php72
<p></p>
<p>2° Instalar php</p>
sudo yum install php
<p></p>
<p>3° Editar /etc/ṕhp-fpm.d/www.conf</p>
vim /etc/php-fpm.d/www.conf
<p></p>
<p>Alterar a linha que definem o user e o group  altere seus valores de “apache” para “nginx” ( para que o php tenha comunicação com o nginx)</p>
user = nginx <p></p> 
group = nginx
<p></p>

<p>4º Iniciar e habilitar o php</p>
sudo systemctl start php-fpm
<p></p>
<p>sudo systemctl enable php-fpm</p>

<p>Configurar o Nginx para processar páginas PHP</p>

<p>1° Criar o arquivo:</p>
sudo vim /etc/nginx/conf.d/default.conf
<p></p>
<p>2° Na linha  server_name  localhost (Inserir o ip);</p>
após a alteração reiniciar o nginx

sudo systemctl restart nginx</p>

<p>Teste o processamento PHP</p>
<p>Criar o arquivo info.php:</p>
<p>sudo vim /usr/share/nginx/html/info.php</p>
<?php phpinfo(); ?>
<p>Para testar</p>
<p>Abra em um navegador da web:</p>
<p>http: // endereço<em>do</em>servidor<em>IP</em>do_servidor /info.php</p></p>

<p>Wordpress</p>

<p>1° download do wordpress</p>
wget http://wordpress.org/latest.zip
<p>2° descompactar o arquivo.zip</p>
<p>unzip latest.zip</p>
<p>3° mover o diretório wordpress para diretório /usr/share/nginx/html/
mv * /usr/share/nginx/html/</p>
<p>4° Alterar o dono do arquivo</p>
<p>chown nginx.nginx -R *</p>
<p>5° Abrir o wordpress no navegador</p>
<p>http://192.168.33.11/wp-admin/setup-config.php?step=0</p>

## Configurando o banco de dados remoto para otimizar o desempenho do site

<p> Criar a VM para o banco de dados </p>
> Criar diretorio Vagrant
```mkdir vmb```
<p></p>
<p> Criar vagrant file</p>
vagrant init
<p></p>
<p>5° Editar o vagrant file</p>
vim vagrantfile
<p></p>
<p>descomentar e editar a linha “config.vm.box = (colocar o nome da iso)”</p>
<p></p>
<p>descomentar a linha “config.vm.network "private_network", ip: "192.168.33.20"</p>
<p></p>
<p>config.vm.provider "virtualbox" do |vb|</p>
<p></p>
<p>descomentar a vb.memory = "1024":</p>
<p></p>
<p> Conectar no vagrant </p>
vagrant ssh
<p></p>

<p>1° Adicionar o repositório do Centos 7 EPEL</P>
sudo yum install epel-release
<p></p>
<p>Mysql ou MariaDB</p>

<p>1° Instalar</p>
sudo yum install mariadb-server mariadb
<p></p>
<p>2° Iniciar o banco</p>
sudo systemctl start mariadb
<p></p>
<p> Rodar a query mysql_secure_installation para setar uma senha para o usuário root e remover contas anônimas, banco teste.
sudo mysql<em>secure</em>installation
<p></p>
Configurando um banco de dados wordpress e acesso remoto
banco

mysql>   CRIAR DATABASE wordpress;

Criando um usuario local

mysql> CREATE USER 'wordpressuser'@'localhost' IDENTIFIED BY 'password';

concedendo privilegio

mysql> GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'localhost';

Criando um usuário para conexão remota

mysql> CREATE USER 'wordpressuser'@'web-server_ip' IDENTIFIED BY 'password';

Concedendo previlegio

GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'web_server_ip';

Liberar os privilegios e gravar no disco

mysql> FLUSH PRIVILEGES;

Sair do banco

mysql> exit

