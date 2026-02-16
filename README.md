# 📦 Resumo – Azure Migrate

## 📌 O que é o Azure Migrate?

O **Azure Migrate** é um serviço da Microsoft que ajuda organizações a **descobrir, avaliar e migrar** cargas de trabalho locais para o **Microsoft Azure**.

Ele fornece um **hub centralizado** no portal do Azure para gerenciar todo o processo de migração, desde a análise inicial até a execução.

---

## 🎯 Objetivos do Azure Migrate

- Identificar recursos no ambiente local (on-premises)
- Avaliar prontidão para migração
- Dimensionar corretamente recursos no Azure
- Estimar custos
- Migrar workloads com mínimo downtime
- Apoiar modernização de aplicações

---

## 🔄 Fases da Migração

### 1️⃣ Descoberta (Discover)
- Detecta servidores físicos e VMs (VMware, Hyper-V)
- Identifica dependências entre aplicações
- Coleta dados de desempenho

### 2️⃣ Avaliação (Assess)
- Verifica compatibilidade com Azure
- Recomenda tamanho adequado de VMs
- Estima custo mensal no Azure
- Analisa dependências de rede e aplicações

### 3️⃣ Migração (Migrate)
- Replica servidores para Azure
- Executa testes antes do cutover
- Realiza migração com mínima interrupção
- Suporta migração de:
  - Servidores físicos
  - VMs VMware
  - VMs Hyper-V
  - Bancos de dados
  - Aplicações Web

---

## 🧰 Ferramentas Integradas

### 🔹 Azure Migrate: Discovery and Assessment
Coleta inventário e gera relatórios de avaliação.

### 🔹 Azure Migrate: Server Migration
Permite replicação e migração de servidores para Azure.

### 🔹 Database Migration
Avalia e migra bancos de dados para:
- Azure SQL Database
- SQL Managed Instance
- SQL Server em VM no Azure

### 🔹 Azure Data Box
Migração offline para grandes volumes de dados.

---

## 💡 Benefícios

- Plataforma unificada
- Integração nativa com Azure
- Avaliação gratuita
- Redução de riscos na migração
- Suporte a estratégias:
  - Lift-and-Shift
  - Replatform
  - Modernização

---

## 🏗 Cenários Suportados

- Migração de datacenter completo
- Migração híbrida
- Modernização de aplicações
- Consolidação de servidores
- Avaliação de custos antes da decisão

---

## 📊 Estratégia Recomendada

1. Executar descoberta por pelo menos 7 a 30 dias
2. Analisar relatórios de dimensionamento
3. Validar custos estimados
4. Planejar rede (VNet, NSG, VPN/ExpressRoute)
5. Criar ambiente piloto
6. Executar migração por ondas

---

## 🚀 Conclusão

O Azure Migrate é a principal ferramenta da Microsoft para apoiar projetos de migração para nuvem, oferecendo visibilidade, planejamento estruturado e execução controlada, reduzindo riscos e melhorando previsibilidade de custos.

