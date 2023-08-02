# Modelo de Negócios de Autenticação

## Resumo

O modelo de negócios de autenticação apresentado neste texto visa garantir que apenas usuários autorizados tenham acesso aos recursos da aplicação. O usuário é direcionado para uma tela de login onde ele deve inserir suas credenciais de acesso. O sistema valida as credenciais do usuário e verifica se ele pertence a um grupo de acesso autorizado para acessar o recurso em questão. Além disso, o sistema limita a força bruta e bloqueia o usuário após 5 tentativas de login falhadas. O sistema também permite que o usuário recupere e altere sua senha, gerencie sua conta e encerre a sessão. O administrador do sistema pode configurar as opções de segurança, gerenciar backups e verificar os registros de auditoria.

## sumário

- [Introdução](#introdução)
- [autenticação](#autenticação)
- [Recuperar e alterar Senha](#recuperar-e-alterar-senha)
- [Gerenciar Conta](#gerenciar-conta)
- [Encerrar Sessão](#encerrar-sessão)
- [Configurações de Segurança](#configurações-de-segurança)
- [Registro de Auditoria](#registro-de-auditoria)
- [Gerenciamento de Backups](#gerenciamento-de-backups)
- [Limitação de Acesso por IP](#limitação-de-acesso-por-ip)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Arquitetura](#arquitetura)
- [Camada de API](#camada-de-api)
- [camada de banco de dados](#camada-de-banco-de-dados)
- [criptografia de senhas](#criptografia-de-senhas)
- [conclusão](#conclusão)

## Introdução

A autenticação é um aspecto crítico para a segurança de sistemas de informação. O modelo de negócios de autenticação apresentado aqui visa garantir que apenas usuários autorizados tenham acesso aos recursos da aplicação.

## autenticação

O usuário é direcionado para uma tela de login onde ele deve inserir suas credenciais de acesso. O sistema valida as credenciais do usuário e verifica se ele pertence a um grupo de acesso autorizado para acessar o recurso em questão. Além disso, o sistema limita a força bruta e bloqueia o usuário após 5 tentativas de login falhadas.

## Recuperar e alterar Senha

O usuário pode recuperar sua senha caso esqueça. O sistema envia um email para o usuário com um link para redefinir a senha. O usuário deve clicar no link e inserir uma nova senha. O sistema valida a nova senha e a confirmação da nova senha. O sistema também verifica se a nova senha é diferente da senha atual.
A qualquer momento, o usuário pode alterar sua senha. O sistema valida a senha atual, a nova senha e a confirmação da nova senha. O sistema também verifica se a nova senha é diferente da senha atual.

## Gerenciar Conta

O usuário pode gerenciar sua conta, alterando seu nome, email e senha. O sistema também permite que o usuário altere sua foto de perfil e outras informações pessoais. O usuário pode gerenciar sua conta a qualquer momento. O sistema também permite que o administrador do sistema ou grupo de acesso com permissões equivalentes gerencie as contas dos usuários. O administrador pode alterar o nome, email e senha dos usuários.
o usuário pode excluir sua conta a qualquer momento. O sistema também permite que o administrador do sistema ou grupo de acesso com permissões equivalentes exclua as contas dos usuários.

## Encerrar Sessão

O usuário pode encerrar a sessão a qualquer momento. O sistema também encerra a sessão automaticamente após 24 horas de inatividade ou apos o prazo estipulado pelo administrador do sistema ou grupo de acesso com permissões equivalentes.
Assim que o usuário encessa a sessão, o token de acesso é invalidado e o usuário não pode mais acessar os recursos da aplicação utilizando o token de acesso. caso o usuário tente acessar os recursos da aplicação utilizando o token de acesso, o sistema irá retornar um erro de autenticação.
Para acessar os recursos da aplicação novamente, o usuário deve realizar o login novamente.

## Configurações de Segurança

O sistema permite que o administrador do sistema ou grupo de acesso com permissões equivalentes configure as seguintes opções de segurança:

### lista de permissões de acesso aos recursos da aplicação

- lista de grupos de acesso,
- lista de usuários,
- lista de logs de acesso,
- lista de registros de auditoria,
- limitação de acesso por IP.
- lista de IP's bloqueados.
- Gerenciamento de backups.

## Registro de Auditoria

são recursos disponíveis para o usuário e o administrador do sistema ou grupo de acesso com permissões equivalentes.
O sistema registra todas as ações realizadas pelos usuários. O sistema também permite que o administrador do sistema ou grupo de acesso com permissões equivalentes visualize os registros de auditoria.

### As ações registradas são

- login,
- logout,
- recuperar senha,
- alterar senha,
- gerenciar conta,
- encerrar sessão,
- configurações de segurança,
- adição de cadastros,
- edição de cadastros,
- exclusão de cadastros,

## Gerenciamento de Backups

O sistema permite que o administrador do sistema ou grupo de acesso com permissões equivalentes realize o backup dos dados do sistema. O sistema também permite que o administrador do sistema ou grupo de acesso com permissões equivalentes restaure os dados do sistema a partir de um backup.

## Limitação de Acesso por IP

O sistema também pode limitar o acesso do agente a um range de endereços IP. Isso é útil para restringir o acesso apenas a usuários dentro de uma rede específica.

## Tecnologias Utilizadas

O software de autenticação foi desenvolvido utilizando o framework FastAPI em conjunto com o banco de dados PostgreSQL. A autenticação é feita utilizando JWT (JSON Web Tokens).

## Arquitetura

O sistema de autenticação é dividido em três camadas:

### Camada de API

A camada de API é a camada responsável por receber as requisições dos usuários e encaminhá-las para a camada de serviço. Ela é responsável por realizar a validação dos dados de entrada, para garantir que os dados estão corretos e evitar problemas de segurança.

### Camada de Serviço

A camada de serviço é a camada responsável por receber as requisições da camada de API e realizar a lógica de negócio do sistema. Ela é responsável por realizar a autenticação do usuário, verificar se ele pertence a um grupo de acesso autorizado e conceder o acesso aos recursos da aplicação de acordo com as permissões definidas.

### Camada de Banco de Dados

A camada de banco de dados é a camada responsável por armazenar os dados do sistema. Ela é responsável por armazenar as informações dos usuários, os grupos de acesso e as permissões de acesso aos recursos da aplicação. Além disso, ela também é responsável por armazenar os logs de acesso, para fins de auditoria e segurança.

## Criptografia de senhas

O sistema utiliza um algoritmo seguro de hashing de senhas para armazenar as senhas dos usuários. As senhas não são armazenadas em texto plano e, caso os dados do banco de dados venham a vazar, as senhas ainda estarão seguras.

## Conclusão

A autenticação é um aspecto crítico para a segurança de sistemas de informação, e o modelo de negócios apresentado neste texto fornece uma abordagem abrangente para garantir a autenticação e segurança do usuário. A utilização de tecnologias como FastAPI e PostgreSQL e a divisão do sistema em camadas de API, Serviço e Banco de Dados permitem a criação de um sistema seguro e escalável. Além disso, o sistema permite que o administrador do sistema gerencie as contas dos usuários e configure as opções de segurança para atender às necessidades específicas da organização.
