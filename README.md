# atividades
atividade diogo

<p>Vagrant</p>

<p>1º Criar pasta Vagrant</p>
mkdir vagrant
2° Instalar vagrant
apt-get install vagrant
3° baixar a imagem cento ( pegar o nome da image que deseja subir na maq virtual )
https://app.vagrantup.com/boxes/search
4° Criar vagrant file
vagrant init
5° Editar o vagrant file
vim vagrantfile
descomentar e editar a linha “config.vm.box = (colocar o nome da iso)”
descomentar a linha “config.vm.network "private_network", ip: "192.168.33.11"
config.vm.provider "virtualbox" do |vb|
descomentar a vb.memory = "1024":</p>

<p>6º Conectar no vagrant 
vagrant ssh</p>

<p>Nginx</p>

<p>1° Adicionar o repositório do Centos 7 EPEL
sudo yum install epel-release
2° sudo yum install nginx</p>

<p>Mysql ou MariaDB</p>

<p>1° Instalar
sudo yum install mariadb-server mariadb
2° Iniciar o banco
sudo systemctl start mariadb
3° Executar um script de segurança para remova alguns padrões perigosos e bloqueie o acesso ao sistema
sudo mysql<em>secure</em>installation
4° Permitir que o banco inicie na inicialização
sudo systemctl enable mariadb</p>

<p>PHP</p>

<p>1° Instalar o repositório
sudo yum-config-manager --enable remi-php72
2° Instalar php
sudo yum install php
3° Editar /etc/ṕhp-fpm.d/www.conf
vim /etc/php-fpm.d/www.conf
Alterar a linha que definem o user e o group  altere seus valores de “apache” para “nginx” ( para que o php tenha comunicação com o nginx)
user = nginx group = nginx</p>

<p>4º Iniciar e habilitar o php
sudo systemctl start php-fpm
sudo systemctl enable php-fpm</p>

<p>Configurar o Nginx para processar páginas PHP</p>

<p>1° Criar o arquivo:
sudo vim /etc/nginx/conf.d/default.conf
2° Na linha  server_name  localhost (Inserir o ip);
após a alteração reiniciar o nginx
sudo systemctl restart nginx</p>

<p>Teste o processamento PHP no seu servidor Web
1° Podemos criar o arquivo nesse local digitando:
sudo vim /usr/share/nginx/html/info.php
<?php phpinfo(); ?>
Salve e saia do arquivo
Para testes basta acessar o endereço que você deseja visitar será:
Abra em um navegador da web:
http: // endereço<em>do</em>servidor<em>IP</em>do_servidor /info.php</p>

<p>Wordpress</p>

<p>1° download do wordpress
wget http://wordpress.org/latest.zip
2° descompactar o arquivo.zip
unzip latest.zip
3° mover o diretório wordpress para diretório /usr/share/nginx/html/
mv * /usr/share/nginx/html/
4° Dar permissão para wordpress
chown nginx.nginx -R *
5° Abrir o wordpress no navegador
http://192.168.33.11/wp-admin/setup-config.php?step=0</p>
