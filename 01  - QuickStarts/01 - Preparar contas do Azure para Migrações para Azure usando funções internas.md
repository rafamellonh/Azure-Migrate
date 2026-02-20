# 📘 Azure Migrate — Preparar Contas do Azure

## 📌 Objetivo

Este guia descreve como **preparar contas no Azure** para usar o serviço **Azure Migrate**, configurando o **Controle de Acesso Baseado em Função (RBAC)** com funções internas apropriadas.

Isso garante que os usuários tenham apenas as permissões necessárias para as diferentes fases da migração, seguindo o princípio de **privilégio mínimo**.   

---

## 🛠 Funções Internas do Azure Migrate

O Azure Migrate define três funções internas (built-in roles) que você pode atribuir para controlar o acesso:

| Função | Permissões principais | Escopo |
|--------|----------------------|--------|
| **Azure Migrate Owner** | Permite criar e gerenciar projetos, descoberta, avaliação e migração completa. Também pode atribuir outras funções internas. | Grupo de Recursos ou Assinatura onde o projeto é criado.    |
| **Azure Migrate Decide and Plan Expert** | Permite operações de planejamento: descoberta, inventário, dependências, criação de caso de negócios e relatórios. | Grupo de Recursos ou Assinatura onde o projeto é criado. :contentReference[oaicite:2]{index=2} |
| **Azure Migrate Execute Expert** | Permite operações de execução da migração: replicação, testes e monitoramento. | Grupo de Recursos ou Assinatura de origem e destino (se for diferente).    |

---

## 📌 Descrição das Funções

### 🧑‍💼 Azure Migrate Owner

- Acesso completo para gerir o projeto Azure Migrate.
- Pode atribuir funções internas a outros usuários ou grupos. :contentReference[oaicite:4]{index=4}

---

### 📊 Azure Migrate Decide and Plan Expert

- Permissões limitadas apenas para tarefas de **planejamento** da migração.
- Não pode criar o projeto nem atribuir funções.   

---

### 🚀 Azure Migrate Execute Expert

- Permissões específicas para executar migrações, como replicação e testes.
- Não pode criar projetos nem atribuir funções. :contentReference[oaicite:6]{index=6}

---

## 🔐 Atribuindo Funções (RBAC)

Para configurar o acesso:

1. No Azure Portal, vá até o **Grupo de Recursos ou Assinatura** onde o projeto Azure Migrate será criado.
2. Acesse **Controle de Acesso (IAM)**.
3. Escolha **Adicionar → Atribuir Função**.
4. Selecione a função que deseja atribuir (p.ex., Azure Migrate Owner).
5. Selecione o usuário ou grupo.
6. Reveja e confirme a atribuição. :contentReference[oaicite:7]{index=7}

---

## ✅ Verificar e Remover Acesso

- Verifique permissões em **Controle de Acesso (IAM) → Verificar Acesso**.     
- Os proprietários da assinatura ou do grupo de recursos podem remover funções atribuídas quando necessário.   

---

## 📌 Registrar Provedores de Recursos

Para que todas as funcionalidades do Azure Migrate funcionem, os **provedores de recursos do Azure** devem estar registrados na assinatura onde o projeto é criado (por exemplo, `Microsoft.Migrate`, `Microsoft.Compute`, `Microsoft.Storage`, etc.) :contentReference[oaicite:10]{index=10}

---

## 🧭 Próximo Passo

After preparing accounts and roles, you can proceed to **create an Azure Migrate project** in the Azure Portal. :contentReference[oaicite:11]{index=11}

