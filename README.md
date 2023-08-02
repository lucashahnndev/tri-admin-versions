# TRI admin

 O TRI admin é uma aplicação web para gerenciamento de estabelecimentos usuarios e visitantes. O software permite a gestão de acessos e permissões para usuários de forma organizada e segura. Utilizando o banco de dados SQLite e a biblioteca ORMAR para manipulação de modelos, o software oferece uma interface intuitiva para a gestão de acessos e permissões dos usuários, além de contar com um módulo de autenticação seguro e ferramentas de segurança para proteger a plataforma contra ataques. Como uma aplicação PWA, o TRI admin pode ser instalado em qualquer plataforma, oferecendo vantagens como independência de sistema operacional e baixo consumo de memória.

## Sumário

- [Introdução](#introdução)
- [1 - Resumo](#1---resumo)
- [2 - Tecnologias utilizadas](#1---resumo)
- [2.1 - Framework](#21---framework)
- [2.2 - Servidor Web](#22---servidor-web)
- [2.3 - banco de dado](#23---banco-de-dado)
- [2.4 - ORM](#24---orm)
- [2.5 - Linguagens de Programação](#25---linguagens-de-programação)
- [3 - Funcionamento](#3---funcionamento)
- [3.1 - Autenticação](#31---autenticação)
- [3.2 - Gestão de acessos e permissões](#32---gestão-de-acessos-e-permissões)
- [4 - PWA um site com vantagens de aplicativo](#4---pwa-um-site-com-vantagens-de-aplicativo)
- [4.1 - Modelo de Negócio PWA](#41---modelo-de-negócio-pwa)
- [4.2 - Independência de sistema operacional](#42---independência-de-sistema-operacional)
- [4.3 - Baixo consumo de memória](#43---baixo-consumo-de-memória)
- [4.4 - Funcionamento offline](#44---funcionamento-offline)
- [4.5 - Cache](#45---cache)
- [4.6 - Manifest](#46---manifest)
- [4.7 - Service Worker](#47---service-worker)
- [5 - Facilidade de uso](#5---facilidade-de-uso)
- [6 - Gerenciamento de Pessoas e Visitantes](#6---gerenciamento-de-pessoas-e-visitantes)
- [7 - Segurança](#7---segurança)
- [7.1 - HTTPS](#71---https)
- [7.2 - Autenticação](#72---autenticação)
- [7.3 - Recuperação de senha](#73---recuperação-de-senha)
- [7.4 - Registros de segurança](#74---registros-de-segurança)
- [7.5 - Criptografia de senhas](#75---criptografia-de-senhas)
- [7.6 - Modelo de Exclusão](#76---modelo-de-exclusão)
- [8 - Integrações com software de terceiros](#8---integrações-com-software-de-terceiros)
- [9 - Conclusão](#9---conclusão)

## Introdução

Tri admin é uma aplicação que permite a gestão de acessos e permissões para usuários em uma plataforma web. O software possui uma interface amigável e intuitiva que possibilita o controle de acessos de forma simples e organizada. Além disso, o Tri admin oferece ferramentas de segurança para proteger a plataforma contra ataques e garantir a privacidade dos dados dos usuários.

## 1 - Resumo

O Tri admin é uma aplicação web desenvolvida com o framework FastAPI e servidor web Apache 2.4, que permite a gestão de acessos e permissões para usuários de forma organizada e segura. Utilizando o banco de dados SQLite e a biblioteca ORMAR para manipulação de modelos, o software oferece uma interface intuitiva para a gestão de acessos e permissões dos usuários, além de contar com um módulo de autenticação seguro e ferramentas de segurança para proteger a plataforma contra ataques. Como uma aplicação PWA, o Tri admin pode ser instalado em qualquer plataforma, oferecendo vantagens como independência de sistema operacional e baixo consumo de memória.

## 2 - Tecnologias utilizadas

### 2.1 - Framework

O Tri admin foi desenvolvido utilizando o framework FastAPI, que é uma ferramenta de criação de APIs (Application Programming Interface) moderna, rápida e fácil de usar. O FastAPI utiliza o protocolo ASGI (Asynchronous Server Gateway Interface) para implementação de APIs assíncronas, permitindo uma maior performance e escalabilidade da aplicação.

### 2.2 - Servidor Web

O Tri Admin utiliza o servidor web Apache 2.4, reconhecido por sua robustez, segurança e alta performance. O Apache é um dos servidores web mais utilizados do mundo, sendo amplamente reconhecido por sua estabilidade e segurança. Ele é capaz de lidar com grandes volumes de tráfego e de processar uma ampla variedade de linguagens de programação.

Para conectar o FastAPI ao Apache, foi utilizado o módulo mod_wsgi, que é amplamente reconhecido pela comunidade Python como a melhor forma de integrar aplicações Python ao servidor web Apache. Além disso, o módulo a2wsgi permite a tradução das requisições HTTP do Apache para o protocolo ASGI do FastAPI e, por sua vez, para o protocolo WSGI do Apache, garantindo uma integração segura e eficiente entre o servidor web e o aplicativo web.
Banco de dados

### 2.3 - banco de dado

O banco de dados utilizado pelo Tri admin é o SQLite, que é um banco de dados SQL embutido que não requer um servidor. Porém, o software também oferece a opção de alterar para o PostgreSQL, um banco de dados relacional mais robusto e escalável.

### 2.4 - ORM

Para a criação e manipulação de modelos no banco de dados, o Tri admin utiliza a biblioteca ORMAR, que é um ORM (Object-Relational Mapping) moderno e rápido, baseado no AsyncIO e capaz de trabalhar com bancos de dados relacionais.

### 2.5 - Linguagens de Programação

O servidor da aplicação Tri admin é desenvolvido em Python 3.11, que é uma linguagem moderna com melhorias de velocidade e aprimoramento de memória em relação às suas versões anteriores. Python é amplamente utilizado no desenvolvimento de aplicações web, científicas e de inteligência artificial.

O frontend da aplicação utiliza JavaScript e PHP, duas linguagens amplamente utilizadas na construção de aplicações web interativas e dinâmicas. JavaScript é a linguagem mais utilizada para o desenvolvimento de aplicações web front-end, enquanto PHP é frequentemente usado para a criação de páginas web dinâmicas e interativas, além de ser uma das linguagens mais populares para o desenvolvimento de sites.

## 3 - Funcionamento

### 3.1 - Autenticação

O módulo de autenticação do Tri admin funciona da seguinte forma: ao criar uma conta, o usuário deve informar um email válido e uma senha. O sistema verifica se o email informado é válido, utilizando regex, e, caso seja, envia um email de boas-vindas para o endereço de email informado, contendo um link para ativar a conta.

Após a ativação da conta, o usuário pode fazer o login na plataforma. Ao fazer o login, o sistema verifica se o email e a senha informados correspondem a uma conta válida. Caso sim, o usuário é autenticado e recebe um token de acesso, que será utilizado em todas as requisições subsequentes.

Para mais detalhes sobre o modelo de autenticação adotado, recomendamos acessar o nosso documento explicativo disponível [aqui](https://github.com/lucashahnndev/tri-admin-versions/blob/main/doc/Modelo%20de%20negocios%20autentica%C3%A7%C3%A3o.md#introdu%C3%A7%C3%A3o). Lá você encontrará informações completas sobre como o modelo funciona e como ele pode ser aplicado em diferentes situações.

### 3.2 - Gestão de acessos e permissões

O Tri admin possui uma interface amigável e intuitiva que permite a gestão de acessos e permissões dos usuários. Atualmente cada usuário pode pertencer a um grupos de acesso (departamentos), que são utilizados para definir as permissões de cada usuário na plataforma.

Os grupos de acesso possuem permissões pré-definidas, que podem ser modificadas de acordo com as necessidades da organização. Por exemplo, é possível definir um grupo de acesso com permissões para visualização de relatórios e outro grupo com permissões para edição de cadastros de pessoas.

## 4 - PWA um site com vantagens de aplicativo

### 4.1 - Modelo de Negócio PWA

O Tri admin é uma aplicação PWA, o que significa que ela pode ser instalada em qualquer plataforma, oferecendo diversas vantagens, tais como:

### 4.2 - Independência de sistema operacional

O PWA é independente de sistema operacional, ou seja, ele pode ser instalado tanto em dispositivos iOS quanto em dispositivos Android.

### 4.3 - Baixo consumo de memória

O PWA tem um baixo consumo de memória, o que o torna uma opção ideal para dispositivos com baixa capacidade de armazenamento.

### 4.4 - Funcionamento offline

O PWA funciona offline, permitindo que os usuários acessem a aplicação mesmo sem uma conexão com a internet.

### 4.5 - Cache

O PWA utiliza o cache do navegador para armazenar dados, o que aumenta a velocidade de acesso aos conteúdos e reduz a dependência de uma conexão constante com a internet.

### 4.6 - Manifest

O manifesto é um arquivo em JSON que contém informações sobre a aplicação, como o nome, a descrição, o ícone e a cor de fundo. Ele permite que o PWA seja instalado no dispositivo do usuário e exibido como um aplicativo nativo.

### 4.7 - Service Worker

O Service Worker é um script em JavaScript que atua como um intermediário entre a aplicação e a rede. Ele permite que o PWA funcione offline e ofereça uma experiência mais rápida e fluida para o usuário.

## 5 - Facilidade de uso

O Tri admin também é um site que pode ser acessado por qualquer navegador, sem a necessidade de instalação. Isso significa que o usuário pode acessar a aplicação a partir de qualquer dispositivo com acesso à internet, o que oferece uma grande facilidade de uso.

## 6 - Gerenciamento de Pessoas e Visitantes

O Tri admin é um software de gerenciamento de pessoas e visitantes que garante a privacidade e segurança dos dados cadastrados. Cada departamento tem controle total sobre os seus próprios usuários e visitantes, ou seja, um departamento não pode visualizar as informações cadastradas por outro departamento. Além disso, o software oferece integração com o software Defense, da Intelbras, permitindo o cadastro de visitantes e pessoas monitoradas pelo sistema. Todas as informações cadastradas são armazenadas de forma segura no banco de dados do sistema, garantindo a privacidade e a segurança dos dados.

## 7 - Segurança

O Tri admin oferece ferramentas de segurança para proteger a plataforma contra ataques e garantir a privacidade dos dados dos usuários. Entre as principais ferramentas de segurança utilizadas estão:

### 7.1 - HTTPS

Todo o tráfego na plataforma é criptografado utilizando o protocolo HTTPS, garantindo a privacidade das informações trocadas entre o navegador do usuário e o servidor.

### 7.2 - Autenticação

O módulo de autenticação do Tri admin exige que os usuários se autentiquem com um nome de usuário e senha para acessar a plataforma. Além disso, o sistema conta com recursos de verificação de grupo de acesso para garantir que cada usuário tenha acesso apenas às funcionalidades que lhe são permitidas.

Para mais detalhes sobre o modelo de autenticação adotado, recomendamos acessar o nosso documento explicativo disponível [aqui](https://github.com/lucashahnndev/tri-admin-versions/blob/main/doc/Modelo%20de%20negocios%20autentica%C3%A7%C3%A3o.md#introdu%C3%A7%C3%A3o). Lá você encontrará informações completas sobre como o modelo funciona e como ele pode ser aplicado em diferentes situações.

### 7.3 - Recuperação de senha

Caso um usuário esqueça sua senha, o Tri admin oferece uma opção de recuperação de senha, que envia um código de acesso para o email cadastrado do usuário. O código de acesso é válido para uso único e expira após um curto período de tempo.

### 7.4 - Registros de segurança

O Tri admin registra todas as atividades realizadas na plataforma, incluindo informações como o nome do agente, o endereço IP e a rota de acesso. Esses logs são armazenados em um banco de dados para permitir uma análise detalhada de possíveis problemas de segurança.

### 7.5 - Criptografia de senhas

O Tri admin utiliza um algoritmo seguro de hashing de senhas para armazenar as senhas dos usuários. As senhas não são armazenadas em texto plano e, caso os dados do banco de dados venham a vazar, as senhas ainda estarão seguras.

### 7.6 - Modelo de Exclusão

O Tri admin utiliza o modelo de exclusão para garantir a privacidade dos dados dos usuários e aumentar a segurança da plataforma. Esse modelo consiste em não deletar os dados do banco de dados, mas sim marcá-los como "excluídos". Dessa forma, esses dados não serão mais exibidos nas consultas e buscas, mas permanecerão no banco de dados para futuras análises e auditorias.

Ao marcar os dados como "excluídos", o Tri admin evita que esses dados sejam perdidos ou corrompidos, além de permitir a recuperação de dados em caso de erros ou problemas no sistema. Além disso, o modelo de exclusão é uma prática recomendada para garantir a conformidade com as leis e regulamentações de proteção de dados, como a GDPR e a LGPD.

Para mais detalhes sobre o modelo de exclusão adotado, recomendamos acessar o nosso documento explicativo disponível [aqui](https://github.com/lucashahnndev/tri-admin-versions/blob/main/doc/Modelo%20de%20negocios%20exclus%C3%A3o.md). Lá você encontrará informações completas sobre como o modelo funciona e como ele pode ser aplicado em diferentes situações.

## 8 - Integrações com software de terceiros

O Tri admin possui integrações com softwares de terceiros conforme a demanda dos usuários. Uma das integrações já prontas é com o software Defense IA, de propriedade da Intelbras, para cadastro de visitantes e pessoas. Existe um processo de sincronização automático entre o Tri admin e o Defense para adição, edição e exclusão de pessoas e visitantes. O sistema de sincronização salva o código de vinculação e do objeto integrado, bem como o status da sincronização. As regras de integração são respeitadas e é utilizada a documentação disponibilizada pelo parceiro proprietário do software.

Recursos e integrações adicionais podem ser adicionados mediante solicitação e seguindo um processo e tempo específicos. Dependendo da demanda, pode haver custos adicionais.

## 9 - Conclusão

O Tri admin é uma plataforma completa e segura de autenticação e gerenciamento de usuários. Seu sistema de verificação de acesso garante que apenas os usuários autorizados tenham acesso às áreas restritas da plataforma. O sistema de registros ajuda a garantir a segurança dos dados dos usuários, armazenando informações relevantes em uma tabela do banco de dados.

A plataforma é segura contra ataques e utiliza o protocolo HTTPS para garantir a privacidade das informações. Além disso, o Tri admin possui integrações com software de terceiros, como o Defense, que facilitam o cadastro e gerenciamento de pessoas e visitantes.

Além de tudo mencionado anteriormente o Tri admin segue boas práticas de desenvolvimento seguro e é atualizado regularmente para garantir que esteja protegido contra as mais recentes ameaças de segurança.

Com o Tri admin, as empresas podem gerenciar com eficiência o acesso de seus usuários à plataforma, garantindo a segurança e a privacidade dos dados.
