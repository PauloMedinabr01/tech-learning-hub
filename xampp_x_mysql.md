# Por que evitar o uso do XAMPP em vez do MySQL para estudos de desenvolvimento web?

## Tecnologias utilizadas

<img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white" alt="Logo Ubuntu"> 
<img src="https://img.shields.io/badge/-PHPStorm-181717?style=for-the-badge&logo=phpstorm&logoColor=white" alt="Logo PHPStorm"> 
<img src="https://img.shields.io/badge/VSCode-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white" alt="Logo VScode"> 
<img src="https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white" alt="Logo PHP"> 
<img src="https://img.shields.io/badge/Composer-885630?style=for-the-badge&logo=Composer&logoColor=white" alt="Logo PHP"> 
<img src="https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white" alt="Logo MYSQL"> 
<img src="https://img.shields.io/badge/Xampp-F37623?style=for-the-badge&logo=xampp&logoColor=white" alt="XAMMP"> 

O XAMPP é uma ferramenta popular que fornece um ambiente de desenvolvimento local para aplicativos da web. Ele inclui
várias tecnologias, como Apache, MySQL, PHP e Perl, pré-configuradas em um único pacote fácil de instalar. Embora o
XAMPP seja conveniente para iniciantes e estudantes que desejam configurar rapidamente um ambiente de desenvolvimento
local, existem alguns problemas em usar o XAMPP em vez do MySQL isoladamente para estudos de desenvolvimento web.

### 1. Desacoplamento das tecnologias:

Ao usar o XAMPP, você instala várias tecnologias (Apache, MySQL, PHP etc.) como um único pacote. Isso pode dificultar o
entendimento e a configuração individual de cada tecnologia. No mundo real, é importante compreender como cada
componente de um ambiente de desenvolvimento funciona separadamente, para que você possa configurá-lo e solucionar
problemas de forma eficaz.

### 2. Versionamento e atualizações:

O XAMPP geralmente inclui versões específicas de cada tecnologia que podem não ser as mais recentes. Isso pode levar a
problemas de compatibilidade ao desenvolver aplicativos que exigem versões específicas de software. Além disso, as
atualizações para cada componente do XAMPP podem não ser liberadas simultaneamente, o que pode resultar em
desequilíbrios no ambiente de desenvolvimento.

### 3. Dependências desnecessárias:

O XAMPP é uma solução abrangente que inclui não apenas o MySQL, mas também outros componentes, como Apache e PHP. Para
fins de estudo específicos que envolvem o PHP e o banco de dados MySQL, o XAMPP pode adicionar sobrecarga e complexidade
desnecessárias ao ambiente de desenvolvimento.

### 4. Flexibilidade limitada:

O XAMPP oferece uma configuração padronizada e limitada para seu ambiente de desenvolvimento local. Se você deseja
personalizar a configuração do MySQL ou experimentar diferentes versões, pode enfrentar dificuldades ao usar o XAMPP,
pois ele é projetado para ser uma solução "pronta para usar" com configurações pré-definidas.

### 5. Portabilidade e escalabilidade:

Usar o MySQL isoladamente em vez do XAMPP permite maior portabilidade e escalabilidade. Você pode facilmente migrar seu
banco de dados para outros ambientes de hospedagem, como servidores em nuvem, sem depender de um pacote de software
específico como o XAMPP. Além disso, ao utilizar o MySQL isoladamente, você tem mais controle sobre a configuração e
otimização do banco de dados para atender às necessidades específicas do seu aplicativo.

Em resumo, embora o XAMPP seja uma solução conveniente para iniciantes e estudantes que desejam configurar rapidamente
um ambiente de desenvolvimento local, usar o MySQL isoladamente oferece mais flexibilidade, controle e compreensão das
tecnologias envolvidas no desenvolvimento web. Ao optar por configurar e usar o MySQL separadamente, os estudantes podem
aprimorar suas habilidades de desenvolvimento e compreender melhor o funcionamento dos sistemas de banco de dados
relacionais.

# Criar um ambiente PHP e Mysql local no Ubuntu

## Instalar o PHP

### 1. Instalação do PHP:

Verificar atualizações de pacotes e instalar:

```shell 
sudo apt update && sudo apt upgrade -y 
``` 

### Instale o PHP e algumas extensões comuns usando o seguinte comando:

Para este tutorial vamos considerar a versão 8.1 do PHP e suas extensões:

```shell 
sudo apt install php8.1 php8.1-cli php8.1-mysql php8.1-pdo php8.1-mbstring php8.1-curl php8.1-xml php8.1-zip php8.1-intl php8.1-gd 
``` 

Isso instalará o PHP e as extensões mais comuns para desenvolvimento e conectar-se ao MYSQL.

Verifique se o PHP foi instalado corretamente:

```shell 
php -v 
``` 

### 2. Instalação do Composer:

O Composer é uma ferramenta de gerenciamento de dependências para PHP. Para instalar o Composer, execute o seguinte
comando:

```shell
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

Mover o arquivo composer.phar para o diretório /usr/local/bin/composer:

```shell
sudo mv composer.phar /usr/local/bin/composer
```

Verificar se o Composer foi instalado corretamente:

```shell
composer -v
```

Se tudo estiver ok, você verá a versão do Composer instalada.

### 3. Instalação do Git:

O git é uma ferramenta de controle de versão amplamente utilizada no desenvolvimento de software. Para instalar o git,
execute o seguinte comando:

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

### 4. Instalação do MYSQL:

Para instalar a versão mais recente do MYSQL:

```shell 
sudo apt install mysql-server 
``` 

Após a instalação, verificar se o serviço rodando:

```shell 
sudo systemctl status mysql 
``` 

Se estiver tudo ok você verá uma mensagem do tipo active (running).

### Configurar a senha root:

Acesse o mysql com o comando:

```shell 
sudo mysql 
``` 

Defina uma senha para o root:

```shell 
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'digite_a_senha_para_o_root@'; 
``` 

Sair do mysql:

```shell 
exit 
``` 

### Fazer a instalação segura do MYSQL

Inicie a instalação segura do mysql:

```shell 
sudo mysql_secure_installation 
``` 

Siga as opções durante a instalação e configure de acordo com suas necessidades, por se tratar de um tutorial para
ambiente de estudos local, vamos ignorar as opções digitando n.
Após concluir, sair da instalação:

```shell 
exit 
``` 

### Acessando e criando o banco de dados de exemplo:

Acesse o mysql utilizado a senha root:

```shell 
sudo mysql -u root -p 
``` 

Crie o seu banco de dados:

```shell 
create database exemplo; 
``` 

Verifique a criação do banco de dados:

```shell 
show databases; 
``` 

Se estiver tudo ok, podemos sair do mysql:

```shell 
exit 
``` 

## Testando o ambiente local e validando o PHP e o MYSQL

Para validar nossa instalação local do PHP e MYSQL, crie uma pasta em um local de sua preferência,
abra a pasta com uma ide ou editor de código de sua preferência e crie o arquivo com o nome conexao.php.

Adicione o código de exemplo abaixo:

#### <?php

#### $host = 'localhost';

#### $dbname = 'nome_do_banco_de_dados';

#### $username = 'usuario';

#### $password = 'senha';

#### try {

#### $pdo = new PDO("mysql:host=$host;dbname=$dbname", $username, $password);

#### $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

#### echo "Conexão com o MySQL bem-sucedida!";

#### } catch (PDOException $e) {

#### echo "Erro na conexão com o MySQL: " . $e->getMessage();

#### }

#### ?>

### Abra um terminal e inicie um servidor próprio de PHP

O comando abaixo inicia um servidor php na porta 8000:

```shell 
php -S localhost:8000 
``` 

Abra o navegador e digite: http://localhost:8000/conexao.php

Se as configurações do seu banco de dados foram corretamente informadas, você verá uma mensagem de sucesso:

### (Conexão com o MySQL bem-sucedida!).

Em caso de erro nas credenciais informadas, você verá uma mensagem de erro como no exemplo a seguir, onde o banco de
dados não existe:

### (Erro na conexão com o MySQL: SQLSTATE[HY000] [1049] Unknown database 'exemplo').

## Verificando o PHP e as extensões instaladas

Crie um novo arquivo com o nome index.php e adicione o código abaixo:

### <?php

### phpinfo();

Abra o navegador e digite:

http://localhost:8000/index.php

Você verá uma página com a versão instalada e todas as extensões instaladas, além de várias informações sobre a
linguagem.

## Finalizando a instalação

Isso completa o processo de instalação do PHP, extensões PHP e MySQL em um ambiente Ubuntu usando apenas o gerenciador
de pacotes apt. Certifique-se de ajustar as instruções de acordo com suas necessidades específicas.
Em caso de dúvidas, tanto o PHP como o MYSQL possuem comunidade ativa e uma vasta documentação oficial.

https://www.php.net/

https://getcomposer.org/

https://git-scm.com/

https://www.github.com/

https://www.mysql.com/ 
 