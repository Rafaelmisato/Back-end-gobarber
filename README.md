# Configuração

Para executar o projeto ...

recebe requisiçes HTTP através do http://localhost:3333/ e salva os dados em banco de dados Postgres.

para rodar esse projeto, você vai precisar estar rodando um banco de dados Postgres com nome "gostack_gobarber", instalar as libs com o comando yarn e rodar o projeto com o comando yarn dev:server

Um banco de dados MongoDB
docker run --name mongodb -p 27017:27017 -d -t mongo
docker start mongodb

apos as dependencias instaladas, executar o comando yarn typeorm migration:run (as tabelas vão ser criadas no database)

configurar o arquivo .env de acordo com o arquivo .env.example, alguns campos, ficarao em branco, vamos terminar a configuracao futuramente.
O mesmo para o arquivo ormconfig, caso for executar em ambiente de desenvolvimento é preciso configurar, caso for para producao nao.

Agora precisamos configurar o Amazon S3, vamos configurar o usuario no servico IAM

//To-do. Terminar a configuracao do aws, terminar de configurar e colocar o servidor para executar, ainda faltam algumas especificacoes.



## Back-end do App

Nessa aula terminaremos algumas das funcionalidades faltantes, entre elas a listagem do prestador para verificar todos os agendamentos que ele tem por dia. Lembrando dos nossos requisitos:

## Recuperação de senha

**RFs:**

- O usuário deve poder recuperar sua senha informando seu e-mail;
- O usuário deve receber um e-mail com instruções de recuperação de senha;
- O usuário deve pode resetar sua senha;

**RNFs:**

- Utilizar Mailtrap para testar envios em ambiente de desenvolvimento;
- Utilizar Amazon SES para envios em produção;
- O envio de emails deve acontecer em segundo plano (background job);


**RNs:**

- O link enviado por email para resetar senha, deve expirar em 2h;
- O usuário deve confirmar a nova senha escolhida;


## Atualização do perfil

**RFs:**

- O usuário deve poder atualizar seu nome, email e senha;

**RNs:**

- O usuário não pode alterar seu email para um email já cadastrado;
- Para atualizar a senha, o usuário deve informar a senha atual;
- Para atualizar a senha, o usuário deve confirmar a nova senha;

## Painel do prestador

**RFs:**

- O usuário deve poder listar seus agendamentos de um dia específico;
- O prestador deve receber uma notificação sempre que houver um novo agendamento;
- O prestador deve poder visualizar as notificações não lidas;

**RNFs:**

- Os agendamentos do prestador no dia devem ser armazenados no cache;
- As notificações do prestador devem ser armazenadas no MongoDB;
- As notificações do prestador devem ser enviadas em tempo-real utilizando Socket.io;


**RNs:**

- A notificação deve ter um status de lida ou não-lida para que o prestador possa controlar;


## Agendamento de serviços

**RFs:**

- O usuário deve poder listar todos prestadores de serviço cadastrados;
- O usuário deve poder listar os dias de um mês com pelo menos um horário disponível de um prestador;
- O usuário deve poder listar horários disponíveis em um dia específico de um prestador;
- O usuário deve poder realizar um novo agendamento com um prestador;

**RNFs:**

- A listagem de prestadores deve ser armazenada em cache;

**RNs:**

- Cada agendamento deve durar exatamente 1h;
- Os agendamentos devem estar disponíveis entre 8h às 18h (último horário às 17h);
- O usuário não pode agendar em um horário já ocupado;
- O usuário não pode agendar em um horário no passado;
- O usuário não pode agendar serviços com ele mesmo;



### Legendas:
**RF** - Requisitos funcionais
**RNF** - Requisitos não-funcionais
**RN** - Regras de negócio
