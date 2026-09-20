# Gerenciador de Tarefas (EJS) - Desenvolvimento Web III

Projeto desenvolvido para a disciplina de **Desenvolvimento Web III**, evoluído para a **Unidade 3: Autenticação, Controle de Acesso e Tratamento de Erros**.

---

## 🚀 Tecnologias Utilizadas

- **Node.js** com **Express.js**
- **EJS** (Embedded JavaScript Templating)
- **Sequelize ORM** com **SQLite**
- **express-session** para gerenciamento de sessões do usuário

---

## 👥 Usuários de Teste para Avaliação

O sistema cria automaticamente os seguintes usuários no banco SQLite ao ser iniciado:

| Perfil | E-mail | Senha | Permissões |
| :--- | :--- | :--- | :--- |
| **Administrador** | `admin@teste.com` | `admin123` | Acesso total, incluindo `/admin` e gerenciamento global |
| **Usuário Comum** | `user@teste.com` | `user123` | Acesso a `/` e às suas próprias tarefas (bloqueado em `/admin` - 403) |

---

## 🛠️ Instruções de Execução

1. **Instalar dependências:**
   ```bash
   npm install
   ```

2. **Iniciar o servidor:**
   ```bash
   npm start
   ```

   Ou em modo de desenvolvimento (com reinício automático):
   ```bash
   npm run dev
   ```

3. **Acessar a aplicação no navegador:**
   [http://localhost:3000](http://localhost:3000)

---

## 🛡️ Rotas e Tratamento de Erros

- **Autenticação:**
  - `GET /login` - Tela de login.
  - `POST /login` - Autenticação direta de credenciais.
  - `GET /logout` - Encerramento de sessão.
- **Rotas Protegidas:**
  - `GET /` - Listagem e cadastro de tarefas do usuário conectado.
  - `POST /tarefas` - Adiciona nova tarefa.
  - `POST /tarefas/:id/toggle` - Alterna status de conclusão.
  - `POST /tarefas/:id/delete` - Exclui a tarefa.
- **Rota de Administrador:**
  - `GET /admin` - Painel de métricas e listagem global de usuários e tarefas (retorna **403 Forbidden** para usuários comuns).
- **Tratamento de Erros HTTP:**
  - **400 Bad Request:** Formulário com dados incompletos ou rota `/erro-400`.
  - **403 Forbidden:** Acesso não autorizado (ex: usuário comum acessando `/admin`).
  - **404 Not Found:** Rotas ou recursos inexistentes.
  - **500 Internal Server Error:** Falha interna capturada pelo middleware global ou rota `/erro-500`.
