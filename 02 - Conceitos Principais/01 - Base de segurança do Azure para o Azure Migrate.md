# 🔐 Azure Migrate – Security Baseline (Resumo)

## 📌 O que é a Security Baseline?

A **Azure Migrate Security Baseline** é um conjunto de recomendações de segurança baseado no **Microsoft Cloud Security Benchmark**.

Ela mostra como aplicar controles e boas práticas de segurança especificamente ao serviço **Azure Migrate**.

O objetivo é garantir que os projetos de migração estejam protegidos seguindo padrões oficiais da Microsoft.

---

## 🎯 Objetivo da Baseline

A baseline ajuda você a:

- Implementar controles de segurança recomendados
- Proteger dados e identidades
- Reduzir riscos durante a migração
- Manter conformidade com padrões de segurança da Microsoft

---

## 🛡 Principais Áreas de Segurança

A baseline organiza as recomendações em categorias:

---

### 🌐 1. Segurança de Rede

- Suporte a **Azure Private Link** para conexões privadas
- Possibilidade de **desabilitar acesso público**
- Comunicação segura entre serviços

Objetivo: evitar exposição desnecessária à internet pública.

---

### 👤 2. Gerenciamento de Identidade

- Integração com **Microsoft Entra ID (Azure AD)**
- Uso de **RBAC (Role-Based Access Control)**
- Suporte a **Identidades Gerenciadas**

Objetivo: garantir que apenas usuários autorizados tenham acesso ao projeto.

---

### 🔒 3. Proteção de Dados

- **Criptografia em trânsito** (TLS)
- **Criptografia em repouso** (armazenamento protegido por padrão)
- Proteção automática dos metadados do projeto

Objetivo: garantir confidencialidade e integridade dos dados.

---

### 📊 4. Monitoramento e Registro

- Integração com **Microsoft Defender for Cloud**
- Suporte a **logs e auditoria**
- Monitoramento de conformidade com o benchmark

Objetivo: detectar ameaças e manter governança.

---

### 🏢 5. Governança e Conformidade

- Suporte a **Azure Policy**
- Aplicação de políticas organizacionais
- Avaliação contínua de segurança

Objetivo: manter padrão de segurança consistente em toda a assinatura.

---

## 🧠 O que é o Microsoft Cloud Security Benchmark?

É um conjunto de boas práticas da Microsoft que define padrões de segurança para serviços no Azure.

A Security Baseline do Azure Migrate é baseada nesse benchmark.

---

## ✅ Conclusão

A Azure Migrate Security Baseline:

- Não adiciona novos recursos
- Define como usar os recursos existentes de forma segura
- Ajuda a proteger identidades, rede e dados
- Permite monitoramento contínuo via Defender for Cloud

Ela funciona como um guia oficial para garantir que seu projeto de migração siga boas práticas de segurança no Azure.

