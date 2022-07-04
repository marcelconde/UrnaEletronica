 Não vamos tratar aqui sobre os processos
 de instalação do sistema operacional,
 apenas sobre algumas das ferramentas
 necessárias para o curso de nossa disciplina.



 O conteúdo está sendo compartilhado
 em texto simples, pois quero com isso
 forçar que você como aluno busque descobrir
 e exercitar como fazer os procedimentos.


## Conjunto de pacotes de pre-requisitos do Linux Não obrigatórios, mas são de grande ajuda


O intuito aqui é instalar uma diversidade de pacotes que não são necessariamente para o desenvolvimento de nossa disciplina, mas sim como ferramentas essenciais para operação em um sistema operacional Fedora Linux.
Cada linha abaixo é um comando que deverá ser executado no terminal.

    # Pacotes gerais, Kernel e filesystems
    sudo dnf install -y cifs-utils iucode-tool kernel-devel kernel-headers kernel-tools microcode_ctl
    # Pacotes de compilação
    sudo dnf install -y automake binutils dkms gcc glibc glibc-common glibc-devel glibc-utils libaio libaio-devel make patch perl perl-Tk
    # Pacotes de compilação do CMake
    sudo dnf install -y cmake cmake-data cmake-fedora cmake-filesystem cmake-gui extra-cmake-modules qt5-qtdeclarative-devel kf5-plasma-devel kf5-kdeclarative-devel kf5-kconfigwidgets-devel kf5-ki18n-devel kdecoration-devel
    # Pacotes de compressão
    sudo dnf install -y arj bzip2 cabextract p7zip p7zip-doc p7zip-gui p7zip-plugins pbzip2 sharutils uudeview xz zip unzip
    # Pacotes de desktop
    sudo dnf install -y axel conky conky-manager curl dnf-utils fontconfig geoclue2 gimp ghostscript gnome-disk-utility gparted ImageMagick inkscape keepassxc nano okular okular-libs putty readline snapd tmux wget yum-utils
    # Pacotes auxiliares de desenvolvimento
    sudo dnf install -y meld perl perl-Tk php-cli python-pip python3-idle rlwrap
    # Instalação dos grupos de pacotes
    sudo dnf groupinstall -y "Administration Tools"
    sudo dnf groupinstall -y "C Development Tools and Libraries"
    sudo dnf groupinstall -y "D Development Tools and Libraries"
    sudo dnf groupinstall -y "Development Tools"
    sudo dnf groupinstall -y "Domain Membership"
    sudo dnf groupinstall -y "Editors"
    sudo dnf groupinstall -y "Hardware Support"
    # Após a instalação
    sudo dnf clean all -y && sudo dnf autoremove -y && sudo dnf update -y && sudo dnf upgrade -y



#######################################
# Sequência de passos para o Fedora Linux
#######################################

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
    Geralmente faço isso dentro de meu perfil de usuário no Linux.
        Exemplo: /home/SEU_NOME_USUARIO/Work/Workspace
    Nesse diretório serão armazenados os códigos dos projetos que você irá trabalhar.
    Não é obrigatório definir tal diretório, isso é mais uma escolha pessoal do que regra.



Defina um diretório para as instalações do Android Studio, Apache Maven e Gradle.
    Geralmente faço isso dentro de meu perfil de usuário no Linux.
        Exemplo: /home/SEU_NOME_USUARIO/Work/Apps
    Nesse diretório serão armazenados os programas que não necessitam de instalação e são executados diretamente da pasta descompactada.



#######################################



1. Instalação do Git.
    sudo dnf install -y git git-extras

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
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    sudo dnf install -y java-11-openjdk java-11-openjdk-devel java-11-openjdk-headless 

2.2. Instalação do Oracle JDK.
    Recomendo a instalação do Oracle JDK em sua versão 11, disponível no endereço: https://www.oracle.com/br/java/technologies/javase/jdk11-archive-downloads.html
    Será necessário copiar o arquivo compactado do Oracle JDK para o diretório padrão de instalação da jvm, e dentro do diretório executar os comandos.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    sudo cp jdk-11.0.13_linux-x64_bin.tar.gz /usr/lib/jvm
    cd /usr/lib/jvm
    sudo tar -xvf jdk-11.0.13_linux-x64_bin.tar.gz
    sudo rm -f jdk-11.0.13_linux-x64_bin.tar.gz
    sudo chown -Rf root:root /usr/lib/jvm/jdk-11.0.13
    sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk-11.0.13/bin/java" 1001
    sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk-11.0.13/bin/javac" 1001

    Neste ponto você deverá mudar a opção padrão para a nova instalação do Oracle JDK, verifique com atenção o que está escrito em tela.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    sudo update-alternatives --config java
    sudo update-alternatives --config javac

2.2.1. Variáveis de ambiente para o Oracle JDK.
    Vamos criar o arquivo que carrega as variáveis de ambiente no Linux.
    A linha abaixo é um comando que deverá ser executado no terminal.

    sudo nano /etc/profile.d/oracle.sh

    Insira o conteúdo abaixo dentro do arquivo que você criou.
    NÃO erre, pois poderá comprometer o reinício da máquina.
    Comandos para o editor de texto (nano):
        Para salvar: Ctrl + o
        Para sair do editor: Ctrl + x

    # Configurações do Oracle Java
    export JAVA_HOME=/usr/lib/jvm/jdk-11.0.13
    export JDK_HOME=${JAVA_HOME}
    export JRE_HOME=${JAVA_HOME}
    export PATH=${PATH}:${JAVA_HOME}/bin



3. Instalação do Apache Maven.
    Recomendo a instalação do Apache Maven em sua versão compactada como zip, disponível no endereço: https://maven.apache.org/download.cgi
    O Apache Maven deverá ser descompactado dentro do diretório de Apps.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    mkdir -p /home/SEU_NOME_USUARIO/Work/Apps/Apache/Maven
    cp apache-maven-3.8.4-bin.zip /home/SEU_NOME_USUARIO/Work/Apps/Apache/Maven
    cd /home/SEU_NOME_USUARIO/Work/Apps/Apache/Maven
    unzip apache-maven-3.8.4-bin.zip
    rm -f apache-maven-3.8.4-bin.zip

3.1. Variáveis de ambiente para o Apache Maven.
    Vamos criar o arquivo que carrega as variáveis de ambiente no Linux.
    A linha abaixo é um comando que deverá ser executado no terminal.

    sudo nano /etc/profile.d/apache_maven.sh

    Insira o conteúdo abaixo dentro do arquivo que você criou.
    NÃO erre, pois poderá comprometer o reinício da máquina.
    Comandos para o editor de texto (nano):
        Para salvar: Ctrl + o
        Para sair do editor: Ctrl + x

    # Configurações do Apache Maven
    export M2_HOME=/home/SEU_NOME_USUARIO/Work/Apps/Apache/Maven/apache-maven-3.8.4
    export M2=${M2_HOME}/bin
    export MAVEN_OPTS="-Xms256m -Xmx512m"
    export PATH=${PATH}:${M2}



4. Instalação do Gradle.
    Recomendo a instalação do Gradle em sua versão completa compactada como zip, disponível no endereço: https://gradle.org/releases/
    O Gradle deverá ser descompactado dentro do diretório de Apps.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    mkdir -p /home/SEU_NOME_USUARIO/Work/Apps/Gradle
    cp gradle-7.4-all.zip /home/SEU_NOME_USUARIO/Work/Apps/Gradle
    cd /home/SEU_NOME_USUARIO/Work/Apps/Gradle
    unzip gradle-7.4-all.zip
    rm -f gradle-7.4-all.zip

4.1. Variáveis de ambiente para o Gradle.
    Vamos criar o arquivo que carrega as variáveis de ambiente no Linux.
    A linha abaixo é um comando que deverá ser executado no terminal.

    sudo nano /etc/profile.d/gradle.sh

    Insira o conteúdo abaixo dentro do arquivo que você criou.
    NÃO erre, pois poderá comprometer o reinício da máquina.
    Comandos para o editor de texto (nano):
        Para salvar: Ctrl + o
        Para sair do editor: Ctrl + x

    # Configurações do Gradle
    export GRADLE_HOME=/home/SEU_NOME_USUARIO/Work/Apps/Gradle/gradle-7.4
    export PATH=${PATH}:${GRADLE_HOME}/bin



5. Variáveis de ambiente para o Android Studio.
    Recomendo a instalação do Android Studio em sua versão instalável "exe", disponível no endereço: https://developer.android.com/studio#downloads
    O Android Studio deverá ser descompactado dentro do diretório de Apps.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    mkdir -p /home/SEU_NOME_USUARIO/Work/Apps/Android/android-sdk
    cp android-studio-2021.1.1.22-linux.tar.gz /home/SEU_NOME_USUARIO/Work/Apps/Android
    cd /home/SEU_NOME_USUARIO/Work/Apps/Android
    tar -xvf android-studio-2021.1.1.22-linux.tar.gz
    rm -f android-studio-2021.1.1.22-linux.tar.gz

    IMPORTANTE: NÃO abra ainda o Android Studio

    Vamos criar o arquivo que carrega as variáveis de ambiente no Linux.
    A linha abaixo é um comando que deverá ser executado no terminal.

    sudo nano /etc/profile.d/android.sh

    Insira o conteúdo abaixo dentro do arquivo que você criou.
    NÃO erre, pois poderá comprometer o reinício da máquina.
    Comandos para o editor de texto (nano):
        Para salvar: Ctrl + o
        Para sair do editor: Ctrl + x

    # Configurações do Android Studio
    export ANDROID_HOME=/home/SEU_NOME_USUARIO/Work/Apps/Android/android-sdk
    export ANDROID_SDK_ROOT=${ANDROID_HOME}
    export PATH=${PATH}:${ANDROID_SDK_ROOT}/platform-tools:${ANDROID_SDK_ROOT}/tools:/home/SEU_NOME_USUARIO/Work/Apps/Android/android-studio/bin

    Reinicie o computador.
    Reinicie o computador.
    Reinicie o computador.
    Reinicie o computador.
    Reinicie o computador.



6. Instalação do Android Studio.
    Abra um terminal, e com seu usuário execute:

    studio.sh

    Siga com os processos que o Android Studio pede em tela.
    Quando surgir o diretório para instalação do Android SDK, faça com que fique o diretório /home/SEU_NOME_USUARIO/Work/Apps/Android/android-sdk
    Ao finalizar a instalação, abra o SDK Manager e vá para a aba SDK Tools, marque "Android SDK Command-line Tools (latest)", clique em Ok e siga com os procedimentos em tela.



7. Instalação do NodeJS com o nvm (Node Version Manager).
    Você está livre para fazer a instalação do NodeJS como lhe convier, entretanto estou lhe apresentando uma forma mais fácil de manter várias versões do Node em seu ambiente de desenvolvimento.
    Vamos usar o nvm para Linux, que está disponível no endereço: https://github.com/nvm-sh/nvm
    Execute a instalação do nvm utilizando os eu usuário e NÃO o root.
    A linha abaixo é um comando que deverá ser executado no terminal.

    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash

7.1. Instalação e configuração das duas versões atuais LTS do NodeJS.
    Cada linha abaixo é um comando que deverá ser executado no terminal.

    nvm list-remote
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
