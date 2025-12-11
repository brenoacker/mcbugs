![Cover](./.github/cover.png)

<div align="center">

**Sistema de Totem Interativo para Restaurantes**

[![Vite](https://img.shields.io/badge/Vite-5.x-646CFF?style=flat-square&logo=vite)](https://vitejs.dev/)
[![React](https://img.shields.io/badge/React-18.x-61DAFB?style=flat-square&logo=react)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue?style=flat-square&logo=typescript)](https://www.typescriptlang.org/)
[![Supabase](https://img.shields.io/badge/Supabase-Latest-3ECF8E?style=flat-square&logo=supabase)](https://supabase.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)

[Reportar Bug](https://github.com/testbeyond/mc-bugs/issues) • [Solicitar Feature](https://github.com/testbeyond/mc-bugs/issues)

</div>

# 🍔🐞 McBugs

## 📖 Sobre o Projeto

O **McBugs** é um sistema completo de totem de autoatendimento desenvolvido exclusivamente para o curso **"Testando o Totem do Méqui com IA"**. O projeto simula a experiência real de um totem do McDonald's, oferecendo uma interface moderna e intuitiva para pedidos em restaurantes.

---

## 🛠️ Stack Tecnológica

### Core

- **[Vite](https://vitejs.dev/)** - Build tool ultrarrápido para desenvolvimento moderno
- **[React 18](https://react.dev/)** - Biblioteca UI com recursos modernos
- **[TypeScript](https://www.typescriptlang.org/)** - Type-safety e melhor DX

### Backend & Database

- **[Supabase](https://supabase.com/)** - Backend as a Service com PostgreSQL
- **[PostgreSQL](https://www.postgresql.org/)** - Banco de dados relacional robusto

---

## 📋 Pré-requisitos

Certifique-se de ter instalado:

- **Node.js** ≥ 18.0.0 ([Download](https://nodejs.org/))
- **Yarn** ≥ 1.22.0 ([Download](https://yarnpkg.com/))
- **Git** ([Download](https://git-scm.com/))
- Conta no **[Supabase](https://supabase.com)** (para banco de dados)

---

## 🚀 Guia de Instalação

### 1️⃣ Clone o Repositório

```bash
git clone <url-do-seu-repositorio>
cd mcbugs-order-hub
```

### 2️⃣ Instale as Dependências

```bash
yarn install
```

### 3️⃣ Configure as Variáveis de Ambiente

Crie um arquivo `.env.local` na raiz do projeto:

```env
VITE_SUPABASE_URL=https://seu-project-ref.supabase.co
VITE_SUPABASE_PUBLISHABLE_DEFAULT_KEY=sua-chave-publica-aqui
VITE_SUPABASE_PROJECT_ID=seu-project-ref
```

> 💡 **Dica:** Veja a seção [Configurar o Supabase](#️-configurar-o-supabase) para obter suas credenciais.

### 4️⃣ Inicie o Servidor de Desenvolvimento

```bash
yarn dev
```

🎉 **Pronto!** Acesse [http://localhost:8080](http://localhost:8080)

---

## ☁️ Configurar o Supabase

### Criar Projeto no Supabase

1. Acesse [https://supabase.com](https://supabase.com) e faça login
2. Clique em **"New Project"**
3. Preencha os dados:
   - **Name**: Nome do seu projeto (ex: `mcbugs-order-hub`)
   - **Database Password**: Crie uma senha forte e **anote-a**
   - **Region**: Escolha a região mais próxima
4. Clique em **"Create new project"** e aguarde a criação

### Obter Credenciais

1. No dashboard do Supabase, vá em **Settings** → **API**
2. Anote as seguintes informações:
   - **Project URL** (ex: `https://xxxxx.supabase.co`)
   - **anon/public key** (chave pública, começa com `eyJ...`)
   - **Project ID** (encontrado na URL: `https://supabase.com/dashboard/project/seu-project-id`)

### 🗄️ Executar Migrations

Você tem duas opções:

#### Opção A: Usando a CLI do Supabase (Recomendado)

```bash
# Instale a CLI do Supabase
yarn add supabase -D

# Faça login
yarn supabase login

# Link seu projeto (project-ref está na URL do dashboard)
yarn supabase link --project-ref seu-project-ref

# Execute as migrations
yarn supabase db push
```

#### Opção B: Usando o SQL Editor no Dashboard

1. No dashboard do Supabase, vá em **SQL Editor**
2. Clique em **"New query"**
3. Execute as migrations na ordem:
   - `supabase/migrations/20251209002507_9a9f0129-cc6b-4721-bcbc-5f53568415f9.sql`
   - `supabase/migrations/20251209010000_add_sequential_order_number.sql`

### ✅ Verificar Instalação

1. No **Table Editor**, verifique se a tabela `orders` foi criada
2. No **SQL Editor**, execute: `SELECT get_next_order_number();`

---

## 🔧 Comandos Úteis

```bash
# Desenvolvimento local
yarn dev

# Build local
yarn build

# Preview do build
yarn preview

# Executar migrations (com Supabase CLI)
yarn supabase db push

# Ver status do Supabase
yarn supabase status
```

---

## 📚 Documentação Útil

- [Documentação do Supabase](https://supabase.com/docs)
- [Documentação do Vite](https://vitejs.dev)

---

## 🐛 Encontrou um Bug?

Ajude a melhorar o projeto! [Reporte aqui](https://github.com/testbeyond/mc-bugs/issues/new)

---

## 👨‍💻 Autor

<div align="center">

**Fernando Papito**

[![Website](https://img.shields.io/badge/Website-testbeyond.com-blue?style=flat-square&logo=google-chrome)](https://testbeyond.com)
[![GitHub](https://img.shields.io/badge/GitHub-@testbeyond-181717?style=flat-square&logo=github)](https://github.com/testbeyond)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin)](https://linkedin.com/in/papitoio)

</div>

---

## 🎓 Sobre o Curso

Este projeto foi desenvolvido exclusivamente para o curso:

**"Testando o Totem do Méqui com IA"**

Um curso prático sobre testes automatizados em sistemas de autoatendimento utilizando ferramentas modernas e Inteligência Artificial.

---

<div align="center">

**Desenvolvido com ❤️ e ☕ por [Fernando Papito](https://testbeyond.com)**

⭐ Se este projeto te ajudou, considere dar uma estrela!

</div>