# atividades
atividade diogo
<p>Vagrant </p>

<p>1º instalar o vagrant</p>

<p>https://app.vagrantup.com/boxes/search</p>

<p>vagrant ssh -> para conectar 
vagrant halt -> desligar</p>

<p>Atividade
subir uma maquina centos 7
instalar nginx
php 7
ngnix mostrar a pagina php.info no ngnix</p>

<p>1º Criar pasta Vagrant
-mkdir vagrant
2° Instalar vagrant
apt-get install vagrant
3° baixar a imagem cento ( pegar o nome da image que deseja subir na maq virtual )
-> https://app.vagrantup.com/boxes/search</p>

<p>4° Criar vagrant file
-> vagrant init</p>

<p>5° Editar o vagrant file
-> vim vagrantfile
-> descomentar e editar a linha “config.vm.box = (colocar o nome da iso)”
-> descomentar a linha “config.vm.network "private_network", ip: "192.168.33.11"
-> config.vm.provider "virtualbox" do |vb|
-> descomentar a vb.memory = "1024":</p>

<p>6º Conectar no vagrant </p>

<p>-> vagrant ssh</p>

<p>BONUS</p>

<p>COMANDO IFCONFIG NÃO FUNICIONA NO CENTOS
Rodar o comando yum install net-tools </p>

<p>7°  Instalar nginx
Adicionar o repositório do Centos 7 EPEL
    -> sudo yum install epel-release</p>

<p>sudo yum install nginx</p>

<p>Depois de instalado o ngnix podemos fazer um teste colocando o ip no navegador</p>

<p>Instalar o banco de dados (Mysql ou MariaDB)</p>

<p>1° Instalar
sudo yum install mariadb-server mariadb</p>

<p>2° Iniciar o banco
    sudo systemctl start mariadb</p>

<p>3° Executar um script de segurança para remova alguns padrões perigosos e bloqueie o acesso ao sistema
    sudo mysql<em>secure</em>installation</p>

<p>4° Permitir que o banco inicie na inicialização
    sudo systemctl enable mariadb</p>

<p>Instale o PHP</p>

<p>1° sudo yum instalar php php-mysql php-fpm</p>

<p>vim /etc/php-fpm.d/www.conf</p>

<p>2° Alterar a linha que definem o user e o group  altere seus valores de “apache” para “nginx” ( para que o php tenha comunicação com o nginx)
user = nginx group = nginx</p>

<p>3º Iniciar e habilitar o php</p>

<p>sudo systemctl start php-fpm
sudo systemctl enable php-fpm</p>

<p>Configurar o Nginx para processar páginas PHP</p>

<p>Criar o arquivo:
 sudo vim /etc/nginx/conf.d/default.conf</p>

<p>Na linha  server_name  localhost (Inserir o ip);</p>

<p>após a alteração reiniciar o nginx
sudo systemctl restart nginx</p>

<p>Teste o processamento PHP no seu servidor Web
Podemos criar o arquivo nesse local digitando:
sudo vim /usr/share/nginx/html/info.php</p>

<p><?php phpinfo(); ?>
Salve e saia do arquivo</p>

<p>Para testes basta acessar o endereço que você deseja visitar será:
Abra em um navegador da web:
http: // endereço<em>do</em>servidor<em>IP</em>do_servidor /info.php</p> 
