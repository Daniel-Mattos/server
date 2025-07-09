🚀Letme Ask Backend

Este projeto é o backend de uma aplicação desenvolvida durante o evento NLW 20 agents da Rocketseat. Ele foi construído com foco em Docker para orquestração de containers, Drizzle ORM para interações eficientes com o banco de dados, variáveis de ambiente seguras com .env e tipagem robusta utilizando TypeScript.

Nosso objetivo com este backend é consumir dados para ter respostas as perguntas feitas.

✨ Tecnologias Utilizadas
TypeScript (TS): Linguagem que adiciona tipagem estática ao JavaScript, aumentando a robustez e manutenibilidade do código.

Node.js: Ambiente de execução JavaScript no lado do servidor.

Docker: Plataforma para desenvolver, enviar e executar aplicações em containers isolados, garantindo consistência em diferentes ambientes.

Drizzle ORM: Um ORM (Object-Relational Mapper) moderno e eficiente para Node.js, facilitando a interação com bancos de dados relacionais.

Dotenv (.env): Para gerenciar variáveis de ambiente de forma segura e flexível.

Express, Fastify: Framework web para construção da API.

PostgreSQL: Sistema de gerenciamento de banco de dados utilizado.

⚙️ Configuração e Execução
Para rodar este projeto em sua máquina local, siga os passos abaixo:

Pré-requisitos
Certifique-se de ter o Docker e o Docker Compose instalados em sua máquina.

Instalar Docker

Instalar Docker Compose

Variáveis de Ambiente
Crie um arquivo .env na raiz do projeto com base no arquivo .env.example. Preencha as variáveis de acordo com suas configurações:

# Exemplo de .env
DATABASE_URL="sua_string_de_conexao_com_o_banco_de_dados"
PORT=3000
# Outras variáveis de ambiente necessárias
Instalação e Inicialização
Clone o repositório:

Bash

git clone https://github.com/seu-usuario/nome-do-seu-repo.git
cd nome-do-seu-repo
Construa e inicie os serviços Docker:

Bash

docker compose up --build -d
Este comando irá construir as imagens Docker (se necessário), criar os containers para o backend e o banco de dados e iniciá-los em segundo plano.

Execute as migrações do Drizzle (se aplicável):

Após os containers estarem rodando, pode ser necessário rodar as migrações do Drizzle para configurar o banco de dados. Você pode fazer isso executando o comando dentro do container do backend:

Bash

docker exec -it <nome-do-container-backend> npm run migrate # ou yarn run migrate, pnpm run migrate
Você pode encontrar o nome do container do backend com docker ps. Geralmente, é algo como nome-do-seu-projeto-backend-1.

Verifique se o backend está rodando:

O backend estará disponível em http://localhost:<PORTA_DO_SEU_BACKEND> (a porta definida no seu .env, geralmente 3000).

💻 Desenvolvimento
Comandos Úteis
Instalar dependências (dentro do container):

Bash

docker exec -it <nome-do-container-backend> npm install # ou yarn install, pnpm install
Rodar o servidor em modo de desenvolvimento:

Bash

docker exec -it <nome-do-container-backend> npm run dev # ou yarn dev, pnpm dev
Gerar novas migrações Drizzle:

Bash

docker exec -it <nome-do-container-backend> npm run drizzle-kit generate # ou yarn drizzle-kit generate, pnpm drizzle-kit generate
Parar os serviços Docker:

Bash

docker compose down
Parar e remover volumes (para um reset completo):

Bash

docker compose down --volumes
Cuidado: Isso irá apagar todos os dados do banco de dados!

🗺️ Rotas da API

Exemplo: Rotas de Usuário
GET /users: Retorna a lista de todos os usuários.

GET /users/:id: Retorna os detalhes de um usuário específico.

POST /users: Cria um novo usuário. (Corpo da requisição: { "name": "...", "email": "..." })

PUT /users/:id: Atualiza um usuário existente.

DELETE /users/:id: Deleta um usuário.
