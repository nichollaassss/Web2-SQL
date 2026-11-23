# Web2 Loja — CRUD com Node.js, Express e MySQL

## Como rodar

1. No MySQL Workbench, execute o script `web2_loja.sql` para criar o banco, as tabelas e o usuário `app_web2`.
2. Copie o arquivo `.env.example` para `.env`:
   ```bash
   cp .env.example .env
   ```
3. Instale as dependências e inicie o servidor:
   ```bash
   npm install
   npm start
   ```
4. Acesse `http://localhost:3000`.

## Resposta do Desafio (SQL Injection)

Concatenar a entrada do usuário diretamente na consulta SQL permite ataques de **SQL Injection**. Se alguém digitar `' OR '1'='1`, o texto deixa de ser apenas um filtro e altera a estrutura do comando SQL, permitindo listar todos os registros, acessar dados de outras tabelas ou modificar informações no banco.

Usando placeholders (`?`) com `pool.execute('... WHERE nome LIKE ?', [`%${busca}%`])`, o MySQL compila o comando antes de receber o parâmetro e trata o valor digitado estritamente como dado literal, nunca como código SQL.
