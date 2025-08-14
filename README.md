**Eduardo de Freitas Mina – 3º DSA – Manhã**
**Projeto Laravel Migration – Alunos**


**0. Dependências**
	As principais dependências para o projeto são:
PHP;
Composer;
Xampp;


  Se você não tiver o Xampp instalado, é só seguir as instruções de instalação no site oficial do Xampp.
	Caso você não tenha o PHP ou o Composer ou ambos instalados, você pode rodar o seguinte comando no Windows Power Shell como administrador para instalá-los no Windows:

```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://php.new/install/windows/8.4'))
```
  Se você estiver no Linux, pode rodar o seguinte comando:
```
/bin/bash -c "$(curl -fsSL https://php.new/install/linux/8.4)"
```
  E se você estiver no MacOs, rode o seguinte comando:
```
/bin/bash -c "$(curl -fsSL https://php.new/install/mac/8.4)"
```

**1. Configuração do PHP**
	Depois de instalar o Xampp e o PHP, você pode rodar o comando php -i no terminal para ver as informações do seu php, e usar a ferramenta de pesquisa do seu terminal (A do meu é o grep) para encontrar a localização do arquivo padrão de inicialização padrão do seu php.
	O arquivo padrão costuma ser o do Xampp, na pasta C:/Xampp/php/php.ini, então seguiremos como se esse fosse o caminho do seu arquivo, mas caso não seja, é só substituir esse caminho pelo caminho no seu computador. Além disso, a partir daqui seguiremos os passos como se você estivesse usando o CMD do Windows, caso você esteja usando outro terminal ou outro sistema operacional, a maior parte dos comandos permanecerão os mesmos, mas consulte a documentação do seu terminal, discussões, blogs, ou alguma forma de pesquisa para adaptar os comandos conforme sua necessidade.
	Após abrir o CMD você terá que configurar o seu php.ini e liberar as extensões ftp, ffi e zip para prosseguir com a instalação do Laravel. Para tanto, basta digitar os seguintes comandos:

```
#Muda para a pasta com o arquivo de inicialização do php
cd ../../xampp/php
#Abre o arquivo no VSCode, mas você pode abri-lo em qualquer editor de texto, basta digitar, em vez da linha abaixo, o comando explorer ., clicar com o botão direito no arquivo php.ini e selecionar “Abrir com” e o seu editor de texto.

code ./php.ini
```
  Agora, com o arquivo aberto no seu editor de texto, use a ferramenta de busca e pesquise pelo seguinte termo: “;extension”. Provavelmente aparecerão 25 resultados correspondentes, ao clicar na seta para ser direcionado ao segundo resultado, você se encontrará na seguinte tela:


  Então tudo o que você precisa fazer é apagar o ; (ponto-e-vírgula) atrás da palavra extension nas linhas do ffi, ftp e zip, e em seguida salvar o arquivo.
	Agora você está pronto para instalar o Laravel, e podemos seguir para a próxima etapa.

2. Instalação do Laravel

	O Laravel é uma biblioteca muito vasta do PHP, usada para desenvolver majoritariamente aplicações web. Para que o projeto descrito nesse arquivo seja iniciado é necessário ter o Laravel instalado na máquina.
	Para instalar o Laravel é necessário ter o PHP instalado, além de algumas outras bibliotecas, extensões, etc. Que são descritas na página oficial do Laravel, no guia de instalação. Com o PHP e todas as outras dependências instaladas, para instalar o Laravel é só abrir o terminal e digitar o seguinte código:
```
composer global require laravel/installer
```
Depois é só esperar alguns poucos minutos e o laravel estará pronto para ser usado.

3. Criação do projeto

	Como foi orientado, esse projeto Laravel se chamará Alunos, então para criar um projeto seguiremos os seguintes passos:
	Antes de tudo, devemos ativar o xampp na máquina. Isso pode ser feito acessando a pasta do xampp e iniciando o programa xampp-start, ou você pode iniciar os programas manualmente através do programa xampp-control. Depois do xampp iniciado, iremos pelo terminal até a pasta xampp/htdocs, é lá que criaremos o projeto. Para isso, faremos esse comando caso você esteja na pasta do usuário:
```
cd ../../xampp/htdocs
```
  Se você estiver na pasta do xampp/php, é só digitar o seguinte:
```
cd ../htdocs
```
  Agora na pasta correta, criaremos o projeto com o seguinte comando:
```
laravel new Alunos
```
  Depois desse comando, o laravel começará a construir o projeto, e ao longo desse processo ele te fará algumas perguntas que você pode responder de acordo com seus interesses. Eu pessoalmente costumo seguir a seguinte sequência de respostas:

Starter kit? None
Which database will your application use? MariaDB
Would you like to do the default migrations? No
Would you like to run npm install and npm run build? Yes

  Se tudo correr como o esperado, após essa sequência de perguntas o seu projeto será construído e você poderá verificar seu funcionamento usando os comandos:
```
cd ./Alunos/
composer run dev
```
  Após digitar esses dois comandos você vai receber no terminal o endereço do seu projeto para acessá-lo na web. Como nós não executamos as migrações padrão durante a construção do projeto, você vai receber um erro de “unknown database”, significa que o programa não encontrou o banco de dados, mas não tem problema, o importante é que o programa esteja executando, e a URL fornecida para você te direcione para a página de logs do projeto.
	Depois de verificar se o projeto está funcionando corretamente, você pode encerrar o processo apertando Ctrl + C, para continuarmos para as migrações do banco de dados.
	Depois de ter criado o projeto, nós vamos editar o arquivo .env, que contém as informações do banco de dados que será criado no xampp. Eu vou abrir o projeto no VSCode, e editar o arquivo por lá:
```
code .
```
  Agora, no VSCode, vamos abrir o arquivo .env, é lá que ficam as informações do banco de dados do sistema. Nós vamos manipular o seguinte bloco:



  Na linha DB_DATABASE é aonde você vai especificar o nome do seu banco de dados, então caso você queira mudar o nome, é lá que você vai mexer, caso contrário, pode deixar como está, mas é importante que você vá na interface do banco de dados que você está utilizando (caso você tenha seguido exatamente as instruções que eu dei, você deve estar usando o MariaDB, portanto, o PhpMyAdmin), e criar um banco vazio exatamente com o nome que estiver nessa linha.
	Então, por fim, após configurar o banco de dados da forma desejada, precisamos rodar esse comando:
```
php artisan migrate
```

  E aqui está o banco de dados do nosso projeto depois de ativo:
