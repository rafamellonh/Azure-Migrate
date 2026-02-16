# 📘 Criar um Projeto no Azure Migrate – Resumo

## 📌 Objetivo

Este guia descreve como criar, gerenciar e excluir um projeto no **Azure Migrate** usando o Portal do Azure.

Um projeto do Azure Migrate armazena os metadados de descoberta, avaliação e migração de servidores, bancos de dados e aplicações.

---

## 🔐 Permissões Necessárias

Para criar um projeto, é necessário possuir:

- Função **Azure Migrate Owner**, ou  
- Permissão equivalente ou superior na assinatura ou grupo de recursos.

> A partir de novembro de 2025, apenas usuários com a função Azure Migrate Owner ou superior poderão criar projetos.

---

## 🚀 Como Criar um Projeto

### 1️⃣ Acessar o Azure Migrate

No Portal do Azure:

- Pesquise por **Azure Migrate**
- Abra o serviço

---

### 2️⃣ Iniciar a Criação

Na página inicial do serviço:

- Selecione **Descobrir, avaliar e migrar**
- Na seção de servidores, bancos de dados e aplicativos Web, clique em **Criar projeto**

---

### 3️⃣ Configurar o Projeto

Preencha as seguintes informações:

- **Assinatura**
- **Grupo de Recursos** (novo ou existente)
- **Nome do Projeto**
- **Geografia**

#### 📍 Importante sobre Geografia

A geografia define apenas onde os **metadados do projeto** serão armazenados.

Ela **não limita** a região de destino dos recursos que serão migrados.

---

### 4️⃣ Criar

Após revisar as configurações:

- Clique em **Criar**
- Aguarde a implantação do projeto

---

## ➕ Criar Projetos Adicionais

Se já existir um projeto:

1. Acesse **Azure Migrate**
2. Vá em **Todos os projetos**
3. Clique em **Criar projeto**

---

## 🗑️ Excluir um Projeto

Para excluir um projeto:

1. Acesse o **Grupo de Recursos**
2. Selecione o projeto
3. Clique em **Excluir**
4. Confirme a exclusão

> ⚠️ A exclusão remove todos os metadados associados ao projeto.

---

## 🛠 Observações Técnicas

- O projeto pode ser criado via API utilizando método `PUT`
- Existe opção de **Configuração Avançada** para cenários com Private Endpoint
- Os provedores de recursos devem estar registrados na assinatura

---

## 🎯 Próximos Passos

Após criar o projeto, você pode:

- Iniciar a descoberta do ambiente
- Criar avaliações
- Configurar ferramentas de migração
- Planejar execução por ondas

