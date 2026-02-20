# Azure Migrate Insights (Prévia) – Visão Geral

Azure Migrate Insights é um recurso (em versão prévia) que ajuda a **avaliar riscos de segurança** no seu datacenter enquanto você planeja a migração para o Azure. Ele utiliza os dados de inventário coletados durante a descoberta para destacar vulnerabilidades e sistemas em fim de suporte.   

---

## 🔎 Principais Benefícios

- Identificar **riscos de segurança** cedo no planejamento de migração.  
- Planejar mitigação de problemas antes da migração.  
- Detectar **sistemas operacionais e softwares em fim de suporte**.  
- Identificar **vulnerabilidades conhecidas (CVEs)**.  
- Detectar servidores sem soluções de **segurança ou gerenciamento de patches**.   

---

## 📊 Tipos de Insights Disponíveis

### 🖥️ Servidores com Riscos de Segurança
Um servidor é marcado com risco se tiver **qualquer** dos itens:

- Sistema operacional em fim de suporte  
- Software em fim de suporte  
- Vulnerabilidades conhecidas (CVEs)  
- Ausência de software de segurança  
- Ausência de software de patch management  
- Atualizações pendentes (críticas ou de segurança) :contentReference[oaicite:2]{index=2}

### 📦 Softwares com Riscos de Segurança

- Software em fim de suporte  
- Software com vulnerabilidades conhecidas (CVEs)   

---

## 📌 Como os Insights são Derivados

1. O **Azure Migrate** coleta inventário de software e SO via descoberta de appliance.  
2. Analisa o inventário com **base em bancos de dados públicos** (como endoflife.date e NVD).  
3. Identifica riscos como fim de suporte, CVEs e atualizações pendentes.  
4. Insights são atualizados quando o inventário é atualizado (nova descoberta ou refresh). :contentReference[oaicite:4]{index=4}

🚫 Não são instalados agentes adicionais nos servidores – usa apenas dados coletados durante a descoberta.   

---

## 📋 Pré-requisitos

- Usar **descoberta baseada em appliance** (não importação).  
- Projeto Azure Migrate ativo com inventário coletado recentemente.  
- Credenciais habilitadas para coletar dados de software nos servidores. :contentReference[oaicite:6]{index=6}

---

## 🧠 Onde Ver os Insights no Portal

1. Acesse seu projeto no **Azure Migrate**.  
2. No menu lateral: **Explorar inventário > Insights (prévia)**.  
3. Você verá um resumo de todos os riscos de segurança em servidores e softwares.  
4. Pode filtrar e exportar dados conforme necessário. :contentReference[oaicite:7]{index=7}

---

## 📌 Dicas de Uso

- Use esses insights para **planejar mitigação proativa** antes da migração.  
- Não substitui ferramentas de segurança dedicadas — combine com *Microsoft Defender para Nuvem* ou *Azure Update Manager* para proteção contínua.   