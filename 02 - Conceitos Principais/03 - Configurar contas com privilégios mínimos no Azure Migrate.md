# 🔐 Azure Migrate – Melhores Práticas: Conta com Menor Privilégio

## 📌 Objetivo

Este documento apresenta recomendações de como configurar **contas e permissões com o mínimo de privilégios necessários** ao trabalhar com o **Azure Migrate**.

A ideia principal é reduzir riscos de segurança limitando o que cada usuário pode fazer, seguindo o princípio **Least Privileged Account (Conta de Menor Privilégio)**.

---

## 🎯 Por que isso é importante?

- Reduz o risco de alterações acidentais ou mal-intencionadas
- Minimiza o impacto de contas comprometidas
- Ajuda a cumprir políticas de segurança corporativas
- Melhora o controle e auditoria de atividades

---

## 🛡 Princípios de Menor Privilégio

### 1️⃣ Separe funções com base em responsabilidades

Crie diferentes grupos e papéis de trabalho no Azure Migrate para cada etapa do processo:

| Função | Permissões necessárias |
|--------|------------------------|
| Planejar e avaliar migração | Acesso limitado às ações de descoberta e avaliação |
| Executar migração | Permissões para criar, configurar e testar migração |
| Administração do projeto | Permissões completas sobre o projeto |

Isso evita dar acesso excessivo para quem só precisa fazer tarefas específicas.

---

## 👥 Use Papéis Integrados (RBAC) do Azure

O Azure Migrate já oferece papéis internos que ajudam a controlar privilégios:

- **Azure Migrate Owner:** permissões completas no projeto
- **Azure Migrate Decide and Plan Expert:** permissões para descobrir e avaliar
- **Azure Migrate Execute Expert:** permissões para executar a migração

Atribua cada papel apenas para os usuários que realmente precisam dessas capacidades.

---

## 🔑 Dicas para Reduzir Privilégios

### ✔️ Evite papéis amplos
- Não dê `Owner` ou `Contributor` no nível da assinatura se não for necessário.
- Prefira papéis mais restritivos e específicos.

### ✔️ Use grupos do Azure AD
- Atribua papéis a **grupos**, não a usuários individuais.
- Isso facilita gestão quando membros mudam de função.

### ✔️ Faça revisões regulares
- Verifique periodicamente se os acessos ainda são necessários.
- Revogue permissões que não estão mais sendo usadas.

---

## 📊 Monitoramento e Auditoria

Mesmo com permissões limitadas, é importante registrar e monitorar todas as ações:

- Ative **logs de auditoria**
- Integre com **Azure Monitor**
- Revise atividades suspeitas

Isso ajuda a rastrear mudanças e identificar possíveis problemas.

---

## 📍 Boas práticas adicionais

### 🛠 Restrinja acesso apenas ao necessário

Apenas os usuários que precisam executar etapas da migração devem ter acesso ao projeto.

### 🔄 Aplicar o princípio em todas as fases

Desde a descoberta e avaliação até os testes e execução, mantenha as contas com o mínimo de privilégios.

### 🚀 Automatize a concessão de acesso

Use **scripts ou políticas** para conceder e revogar acessos de forma controlada.

---

## 🧠 Em resumo

Ao aplicar o princípio de **Conta com Menor Privilégio** no Azure Migrate:

✔️ Você limita permissões ao mínimo necessário  
✔️ Reduz riscos de alterações indesejadas  
✔️ Facilita auditoria e conformidade  
✔️ Mantém o projeto mais seguro

---

## 📌 Recomendações rápidas

1. Atribua papéis baseados em funções (RBAC) específicas.
2. Use grupos do Azure AD em vez de contas individuais.
3. Monitore e registre ações de usuários.
4. Revise e ajuste permissões regularmente.
