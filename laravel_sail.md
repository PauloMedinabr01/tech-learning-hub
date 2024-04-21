# Configuração de Aplicação Laravel com Sail/Docker no Ubuntu

### Este readme fornece algúns comando automatizados que podem ser executados no seu terminal do Ubuntu.

Recomendo fortemente aos iniciantes reproduzirem estes comandos para pegar a prática.

## Tecnologias utilizadas

<img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white" alt="Logo Ubuntu">
<img src="https://img.shields.io/badge/-PHPStorm-181717?style=for-the-badge&logo=phpstorm&logoColor=white" alt="Logo PHPStorm">
<img src="https://img.shields.io/badge/VSCode-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white" alt="Logo VScode">
<img src="https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white" alt="Logo PHP">
<img src="https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white" alt="Logo Laravel">
<img src="https://img.shields.io/badge/Composer-885630?style=for-the-badge&logo=Composer&logoColor=white" alt="Logo Composer">
<img src="https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white" alt="Logo Docker">
<img src="https://img.shields.io/badge/GIT-E44C30?style=for-the-badge&logo=git&logoColor=white" alt="Logo Git">
<img src="https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white" alt="Logo Mysql">
<img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Logo Node">

## Atualize os pacotes do Ubuntu e instale as atualizações:

Na area de trabalho, digite ctrl + alt + t para abrir o terminal:

```shell
sudo apt update && sudo apt upgrade -y
```

## Instalar o Docker Engine usando o repositório apt:

Antes de instalar o Docker Engine pela primeira vez em uma nova máquina host, você precisa configurar o repositório do
Docker. Depois, você pode instalar e atualizar Docker do repositório.

### 1. Configure o repositório do Docker.apt:

```shell
### Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

## Instale os pacotes do Docker.

### 2. Para instalar a versão mais recente, execute:

```shell
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### 3. Verifique se a instalação do Docker Engine foi bem-sucedida executando a imagem hello-world

```shell
sudo docker run hello-world
```

## Gerenciar o Docker como um usuário não root

### Para criar o grupo e adicionar seu usuário:

Crie o grupo docker:

```shell
sudo groupadd docker
```

Adicione seu usuário ao grupo:

```shell
sudo usermod -aG docker $USER
```

### Efetue logout e login novamente para que sua associação ao grupo seja reavaliada.

Você também pode executar o seguinte comando para ativar as alterações nos grupos:

```shell
newgrp docker
```

Verifique se você pode executar comandos sem o sudo docker:

```shell
docker run hello-world
```

## Instalando o GIT:

```shell
sudo apt install git -y
```

## Configurando as credenciais:

Navegue até a pasta:

```shell
cd etc/ssh/
```

Insira o seu usuário no github:

```shell
git config --global user.name "seu_usuario_no_github"
```

Insira o seu e-mail do github:

```shell
git config --global user.email "seu_email_no_github@email.com"
```

Gere a keygen de acesso, neste passo apenas confirme todas as opções apertando enter:

```shell
ssh-keygen -t ed25519 -C "seu_email_no_github@email.com"
```

Navegue até a pasta onde foi gerada a chave publíca:

```shell
cd /home/ubuntu/.ssh/
```

Copie a chave publíca e adicione ao github:

```shell
cat id_ed25519.pub
```

## Instalar o PHP e extenções:

Para instalar o PHP(neste tutorial utilizei o php 8.2):

```shell
sudo apt install php8.1 php8.1-ctype php8.1-curl php8.1-dom php8.1-fileinfo php8.1-mbstring php8.1-opcache php8.1-pdo php8.1-tokenizer php8.1-xml php8.1-zip php8.1-fpm php8.1-mysql -y
```

## Instalar o unzip:

```shell
sudo apt install unzip
```

## Instalar o Composer:

```shell
# Baixe o instalador para o diretório atual
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
# Verifique o instalador
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
# Execute o instalador
php composer-setup.php
# Remover o instalador
php -r "unlink('composer-setup.php');"
```

Muito provavelmente, você deseja mover para o seu PATH, então você pode simplesmente chamar de qualquer diretório(
instalação global), usando, poe exemplo o comando composer:

```shell
sudo mv composer.phar /usr/local/bin/composer
```

Para testar, digite:

```shell
composer --version
```

## Instalando NODE e NPM

Baixa um script de instalação do Node Version Manager(NVM) do repositório GitHub oficial do NVM.

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

Carregar as alterações feitas no arquivo de configuração do shell

```shell
source ~/.bashrc  
```

Depois que o NVM está configurado, você pode usar o comando nvm para instalar versões específicas do Node.js. Este
comando instala a versão mais recente do Node.js disponível.

```shell
nvm install node
```

## Para criar uma aplicação Laravel em um diretório chamado "example-app", você pode executar o seguinte comando no seu terminal:

```shell
curl -s https://laravel.build/example-app | bash
```

É claro que você pode alterar "example-app" nesta URL para qualquer coisa que desejar - apenas certifique-se de que o
nome da aplicação contenha apenas caracteres alfanuméricos, hifens e sublinhados. O diretório da aplicação Laravel será
criado dentro do diretório onde você executar o comando.

A instalação do Sail pode levar vários minutos enquanto os contêineres de aplicativos do Sail são construídos em sua
máquina local.

Depois que o projeto for criado, você pode navegar até o diretório da aplicação e iniciar o Laravel Sail. O Laravel Sail
fornece uma interface de linha de comando simples para interagir com a configuração padrão do Docker do Laravel.

## Instruções iniciais sobre os Containers e Configurações Iniciais

Acesse a pasta do projeto:

```shell
cd example-app
```

Instalar bibliotecas JavaScript front-end, como Vue.js, React, Bootstrap, jQuery, entre outras. Essas bibliotecas são
frequentemente usadas para construir a interface do usuário e adicionar interatividade às páginas da web:

```shell
npm install
```

Compile os recursos JavaScript e CSS do seu projeto:

```shell
npm run dev
```

## Subir os containers:

```shell
./vendor/bin/sail up
```

## Parar os containers:

```shell
./vendor/bin/sail down
```

## Depois que os contêineres Docker da aplicação forem iniciados, você pode acessar a aplicação em seu navegador da web em:

http://localhost

## Atualização de Pacotes e Geração de Chaves da Aplicação

Execute os seguintes comandos para garantir que os pacotes estejam atualizados e para gerar as chaves da aplicação:

```shell
composer update
```

```shell
composer install
```

```shell
php artisan key:generate
```

## Acesso ao Terminal do Container Docker MySQL

Para alterar o usuário e senha do MySQL em um contêiner Docker, você precisa acessar o terminal do contêiner MySQL e
executar os comandos SQL apropriados para alterar as credenciais.

Aqui está um guia para acessar o terminal do contêiner MySQL e realizar as alterações necessárias:

### Acesse o terminal do contêiner MySQL:

```shell
docker exec -it banco_de_dados_container-mysql-1 bash
```

## Conecte-se ao MySQL como root:

### Uma vez dentro do contêiner, conecte-se ao MySQL como root. Por exemplo:

```shell
mysql -u root -p
```

Você será solicitado a inserir a senha do root do MySQL. Use a senha atual definida no seu Docker Compose.

## Altere o nome de usuário e/ou senha:

Após conectar-se ao MySQL, você pode executar as consultas SQL para alterar o nome de usuário e/ou senha.

### Por exemplo, para alterar a senha do usuário padrão 'sail' - senha padrão 'password' para 'nova_senha', você pode usar os seguintes comandos:

```shell
ALTER USER 'nome_do_usuario'@'%' IDENTIFIED BY 'nova_senha';
```

Substitua 'nome_do_usuario' pelo nome de usuário que deseja alterar e 'nova_senha' pela nova senha desejada.

## Saia do MySQL e do terminal do contêiner:

### Após fazer as alterações necessárias, você pode sair do MySQL digitando:

```shell
exit;
```

### E, em seguida, saia do terminal do contêiner digitando:

```shell
exit;
```

Isso deve alterar com sucesso o nome de usuário e/ou senha do MySQL no seu contêiner Docker. Lembre-se de usar as
credenciais atualizadas ao acessar o MySQL em seus aplicativos.

## Outras Operações de Banco de Dados

Você também pode realizar outras operações de banco de dados, como criar usuários, conceder permissões e revogar
permissões. Aqui estão algumas instruções adicionais:

## Liste todos os usuários do container MySQL:

### Após conectar-se ao MySQL, execute a seguinte consulta SQL para listar todos os usuários:

```shell
mysql -u root -p
```

```shell
SELECT user, host FROM mysql.user;
```

## Crie um usuário:

Após se conectar ao MySQL, você pode criar um usuário usando o seguinte comando SQL:

```shell
mysql -u root -p
```

```shell
CREATE USER 'nome_do_usuario'@'localhost' IDENTIFIED BY 'senha';
```

## Conceda permissões necessárias:

Após criar o usuário, você pode conceder as permissões necessárias. Por exemplo, se você quiser que o novo usuário
tenha acesso total a um banco de dados específico, pode conceder as permissões da seguinte forma:

```shell
GRANT ALL PRIVILEGES ON nome_do_banco_de_dados.* TO 'nome_do_usuario'@'localhost';
```

## Remova o usuário:

Após se conectar ao MySQL, você pode remover o usuário usando o seguinte comando SQL:

```shell
DROP USER 'nome_do_usuario'@'localhost';
```

Substitua 'nome_do_usuario' pelo nome do usuário que deseja remover.

## Revogue as permissões:

Se o usuário tiver permissões em bancos de dados ou tabelas, você pode querer revogar essas permissões antes de remover
o usuário. Para revogar todas as permissões do usuário, você pode executar o seguinte comando SQL:

```shell
REVOKE ALL PRIVILEGES ON *.* FROM 'nome_do_usuario'@'localhost';
```

Isso revogará todas as permissões do usuário em todos os bancos de dados e tabelas.

Em um ambiente de produção, é crucial adotar uma abordagem cuidadosa em relação às permissões do banco de dados para
garantir a segurança e a integridade dos dados. Siga as diretrizes fornecidas e tome todas as precauções necessárias
para garantir a segurança do seu sistema.

# Mão na massa!

Agora que você já tem seu ambiente de desenvolvimento pronto, comece com o simples, evolua para o surpreendente e mostre que você é capaz de fazer coisas incríveis!

Se precisar de mais assistência ou tiver alguma dúvida específica, estou à disposição para ajudar! 
