
 Não vamos tratar aqui sobre os processos
 de instalação do sistema operacional,
 apenas sobre algumas das ferramentas
 necessárias para o curso de nossa disciplina.


 O conteúdo está sendo compartilhado
 em texto simples, pois quero com isso
 forçar que você como aluno busque descobrir
 e exercitar como fazer os procedimentos.


 Sequência de passos para o Windows


1. Instalação do Git.
1.1. Configuração do Git.

2. Instalação do Java Development Kit.
2.1. Instalação do OpenJDK.
2.2. Instalação do Oracle JDK.
2.2.1. Variáveis de ambiente para o Oracle JDK.

3. Instalação do Apache Maven.
3.1. Variáveis de ambiente para o Apache Maven.

4. Instalação do Gradle.
4.1. Variáveis de ambiente para o Gradle.

5. Variáveis de ambiente para o Android Studio.

6. Instalação do Android Studio.

7. Instalação do NodeJS com o nvm (Node Version Manager).
7.1. Instalação e configuração das duas versões LTS do NodeJS.
7.2. Instalação de pacotes e frameworks para desenvolvimento.

8. Criação do primeiro projeto com o Ionic.
8.1. Instalação das dependências do projeto.
8.2. Emulação do projeto.



#######################################



Defina um diretório para o seu Workspace no computador.
    Geralmente faço isso dentro de meu perfil de usuário no Windows.
        Exemplo: C:\Users\SEU_NOME_USUARIO\Desktop\Workspace
    Nesse diretório serão armazenados os códigos dos projetos que você irá trabalhar.
    Não é obrigatório definir tal diretório, isso é mais uma escolha pessoal do que regra.



Defina um diretório para as instalações do Android Studio, Apache Maven e Gradle.
    Geralmente faço isso na raiz do sistema, ou em outro disco adicional.
        Exemplo: C:\Apps
    Nesse diretório serão armazenados os programas que não necessitam de instalação e são executados diretamente da pasta descompactada.



#######################################



1. Instalação do Git.
    Recomendo a instalação do git para linha de comando do git-scm, disponível no endereço: https://git-scm.com/

    Baixe o instalador e execute-o: Git-2.35.1.2-64-bit.exe

1.1. Configuração do Git.
    Faça isso com seu usuário.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    git config --global user.name "Seu nome, pode espaços e acentos"
    git config --global user.email "email@que.faz.login.no.git"
    git config --global credential.helper store
    git config --list



2. Instalação do Java Development Kit.
    Vamos utilizar a instalação do OpenJDK para que sejam automaticamente criados os diretórios e configurações padrão no Linux.

2.1. Instalação do OpenJDK.
    Para o Windows NÃO é necessário instalar o OpenJDK.

2.2. Instalação do Oracle JDK.
    Recomendo a instalação do Oracle JDK em sua versão 11, disponível no endereço: https://www.oracle.com/br/java/technologies/javase/jdk11-archive-downloads.html
    A instalação do Oracle JDK é simples e segue a execução do instalável para Windows.
    Apenas execute-o e siga com todas as opções padrão que ele lhe oferecer em tela.

2.2.1. Variáveis de ambiente para o Oracle JDK.
    A criação de variáveis de ambiente no Windows é feita através do aplicativo de configurações.
    No meu iniciar digite "Editar as variáveis de ambiente do sistema".
    Em VARIÁVEIS DE AMBIENTE, clique em novo para cada uma das variáveis abaixo:

    Nome da variável    JAVA_HOME
    Valor da variável   C:\Program Files\Java\jdk-11.0.13

    Nome da variável    JDK_HOME
    Valor da variável   C:\Program Files\Java\jdk-11.0.13

    Nome da variável    JRE_HOME
    Valor da variável   C:\Program Files\Java\jre-11.0.13

    Adicione uma entrada no PATH do Windows.
    Em VARIÁVEIS DE AMBIENTE, dê dois cliquem em PATH, e depois clique em novo e adicione a entrada abaixo:

    C:\Program Files\Java\jdk-11.0.13\bin



3. Instalação do Apache Maven.
    Recomendo a instalação do Apache Maven em sua versão compactada como zip, disponível no endereço: https://maven.apache.org/download.cgi
    O Apache Maven deverá ser descompactado dentro do diretório de Apps.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    md C:\Apps\Apache\Maven

    Descompacte o conteúdo do arquivo apache-maven-3.8.4-bin.zip dentro da nova pasta C:\Apps\Apache\Maven

3.1. Variáveis de ambiente para o Apache Maven.
    A criação de variáveis de ambiente no Windows é feita através do aplicativo de configurações.
    No meu iniciar digite "Editar as variáveis de ambiente do sistema".
    Em VARIÁVEIS DE AMBIENTE, clique em novo para cada uma das variáveis abaixo:

    Nome da variável    MAVEN_HOME
    Valor da variável   C:\Apps\Apache\Maven\apache-maven-3.8.4

    Nome da variável    M2
    Valor da variável   C:\Apps\Apache\Maven\apache-maven-3.8.4\bin

    Nome da variável    MAVEN_OPTS
    Valor da variável   -Xms256m -Xmx512m

    Adicione uma entrada no PATH do Windows.
    Em VARIÁVEIS DE AMBIENTE, dê dois cliquem em PATH, e depois clique em novo e adicione a entrada abaixo:

    C:\Apps\Apache\Maven\apache-maven-3.8.4\bin



4. Instalação do Gradle.
    Recomendo a instalação do Gradle em sua versão completa compactada como zip, disponível no endereço: https://gradle.org/releases/
    O Gradle deverá ser descompactado dentro do diretório de Apps.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    md C:\Apps\Gradle

    Descompacte o conteúdo do arquivo gradle-7.4-all.zip dentro da nova pasta C:\Apps\Gradle

4.1. Variáveis de ambiente para o Gradle.
    A criação de variáveis de ambiente no Windows é feita através do aplicativo de configurações.
    No meu iniciar digite "Editar as variáveis de ambiente do sistema".
    Em VARIÁVEIS DE AMBIENTE, clique em novo para cada uma das variáveis abaixo:

    Nome da variável    GRADLE_HOME
    Valor da variável   C:\Apps\Gradle\gradle-7.4

    Adicione uma entrada no PATH do Windows.
    Em VARIÁVEIS DE AMBIENTE, dê dois cliquem em PATH, e depois clique em novo e adicione a entrada abaixo:

    C:\Apps\Gradle\gradle-7.4\bin



5. Variáveis de ambiente para o Android Studio.
    O Android Studio deverá ser instalado dentro do diretório de Apps.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    md C:\Apps\Android\android-sdk

    IMPORTANTE: NÃO abra ainda o instalador do Android Studio

    A criação de variáveis de ambiente no Windows é feita através do aplicativo de configurações.
    No meu iniciar digite "Editar as variáveis de ambiente do sistema".
    Em VARIÁVEIS DE AMBIENTE, clique em novo para cada uma das variáveis abaixo:

    Nome da variável    ANDROID_HOME
    Valor da variável   C:\Apps\Android\android-sdk

    Nome da variável    ANDROID_SDK_ROOT
    Valor da variável   C:\Apps\Android\android-sdk

    Adicione uma entrada no PATH do Windows.
    Em VARIÁVEIS DE AMBIENTE, dê dois cliquem em PATH, e depois clique em novo e adicione cada uma das entradas abaixo:

    C:\Apps\Android\android-sdk\platform-tools
    C:\Apps\Android\android-sdk\tools

    Reinicie o computador.
    Reinicie o computador.
    Reinicie o computador.
    Reinicie o computador.
    Reinicie o computador.



6. Instalação do Android Studio.
    Recomendo a instalação do Android Studio em sua versão instalável "exe", disponível no endereço: https://developer.android.com/studio#downloads
    Execute o instalador.
    Siga com os processos que o Android Studio pede em tela.
    Quando surgir o diretório para instalação do Android Studio, faça com que fique o diretório C:\Apps\Android\android-studio
    Quando surgir o diretório para instalação do Android SDK, faça com que fique o diretório C:\Apps\Android\android-sdk
    Ao finalizar a instalação, abra o SDK Manager e vá para a aba SDK Tools, marque "Android SDK Command-line Tools (latest)", clique em Ok e siga com os procedimentos em tela.



7. Instalação do NodeJS com o nvm (Node Version Manager).
    Você está livre para fazer a instalação do NodeJS como lhe convier, entretanto estou lhe apresentando uma forma mais fácil de manter várias versões do Node em seu ambiente de desenvolvimento.
    Vamos usar o nvm para Windows, que está disponível no endereço: https://github.com/coreybutler/nvm-windows/releases
    Procure pela última versão do arquivo "nvm-setup.zip" e execute o arquivo "exe" que está dentro deste compactado.
    Quando pedir o diretório para o NVM, digite C:\Apps\nvm
    Quando pedir o diretório para o NODEJS, digite C:\Apps\nodejs

7.1. Instalação e configuração das duas versões atuais LTS do NodeJS.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    nvm list available
    nvm install 14.19.0
    nvm install 16.14.0
    nvm ls

    O comando abaixo define a versão padrão para o ambiente de desenvolvimento, sinta-se livre para definir qualquer versão dentre as que tiver instalado.

    nvm use 14.19.0


7.2. Instalação de pacotes e frameworks para desenvolvimento.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    npm install --global --force @angular/cli @capacitor/core @capacitor/cli @compodoc/compodoc @ionic/cli bower cordova eslint express express-generator jade jade-cli jshint mysql node-sass nodemon pug pug-error pug-lexer pug-parser tslint typescript yarn webpack parcel

    npm upgrade --global --force



8. Criação do primeiro projeto com o Ionic.
    Todo projeto no ionic possui um template que determina quais funcionalidades ele terá inicialmente, e até mesmo um projeto de tutorial ou um projeto de modelo.
    Vamos iniciar criando o projeto de modelo a partir do template chamado conference, utilizando o renderizador visual do Angular, com auxílio da integração com o Cordova.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    ionic start --list
    ionic start MeuAplicativo conference --type=angular --cordova --no-deps

8.1. Instalação das dependências do projeto.
    Abra o diretório do projeto utilizando o Visual Studio Code.
    Não vamos tratar da instalação do Visual Studio Code.
    Iremos agora instalar as dependências do projeto, assim como qualquer projeto desenvolvido sob o NodeJS, um projeto do Ionic utiliza o arquivo package.json para gerenciar as suas dependências.
    Já com o projeto aberto, abra uma janela de terminal dentro do vscode.
    A linha abaixo é um comando que deverá ser executado no terminal.

    npm install --local
    npm audit --fix --force

8.2. Emulação do projeto.
    Depois de instalar as dependências do projeto já é possível executar uma emulação deste, que rodará diretamente no navegador do computador.
    A linha abaixo é um comando que deverá ser executado no terminal.

    ionic serve --lab --open

    Um emulador será executado utilizando seu navegador web, o projeto poderá ser visualizado em qualquer das urls abaixo:
    http://localhost:8200/
    http://localhost:8100/

    Para encerrar a execução do emulador, pressione Ctrl + c no terminal ou feche-o.



9. Notas finais:
    Adicione o diretório C:\Apps, ou outro que você tenha definido, nas exceções de verificação do seu antivirus.

    Adicione o diretório C:\Users\SEU_NOME_USUARIO\Desktop\Workspace, ou outro que você tenha definido, nas exceções de verificação do seu antivirus.
