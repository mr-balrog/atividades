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
user = nginx group = nginx
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
