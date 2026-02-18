# 🔍 Azure Migrate – Tutorial: Descoberta de Servidores Físicos

Este tutorial mostra como usar o **Azure Migrate** para **descobrir servidores físicos** (não virtualizados) no seu ambiente antes de migrá-los para o Azure.

A descoberta de servidores físicos coleta inventário e métricas importantes que serão usadas nas etapas de avaliação e migração.

---

## 🎯 Objetivo

A descoberta de servidores físicos com Azure Migrate permite:

- Identificar servidores físicos existentes
- Coletar inventário (SO, CPU, memória, discos)
- Reunir métricas de performance
- Preparar dados para avaliação e planejamento de migração

---

## 📌 Pré-Requisitos

Antes de começar você precisa:

1. Projeto criado no **Azure Migrate**
2. Conectividade de rede entre:
   - Servidores físicos
   - Máquina onde agente será instalado
3. Conta com permissões adequadas nos servidores físicos
4. Azure Migrate appliance já implantado e registrado

---

## 🧠 Como funciona a descoberta

Ao contrário do método *agentless* usado em VMware, a descoberta de servidores físicos **usa um agente** instalado em cada servidor que você quer descobrir. Esse agente coleta dados locais e os envia ao Azure Migrate.

---

## 🔧 Passos para descobrir servidores físicos

---

### 🪄 1. Preparar o servidor físico

No servidor físico que você quer descobrir:

- Verifique conectividade de rede
- Verifique as portas necessárias (geralmente HTTPS 443)
- Confirme que o SO é compatível

---

### 🛠 2. Baixar o agente de descoberta

No Portal do Azure:

1. Abrir o projeto Azure Migrate
2. Ir em “Descobrir servidores”
3. Selecionar **Windows ou Linux**
4. Baixar o agente correspondente

---

### 📦 3. Instalar o agente no servidor

No servidor físico:

- Execute o instalador do agente
- Aceite permissões para instalar
- Conecte-o ao Azure Migrate:
  - Informe o **nome do projeto**
  - Informe a **chave de registro**

---

### 🔗 4. Registrar o agente no Azure

Após instalação:

- O agente se conecta ao Azure Migrate
- Começa a coletar inventário e métricas
- Você verá esse servidor listado no portal

---

### 📈 5. Coletar dados de performance

O agente captura:

- Uso de CPU
- Uso de memória
- I/O de disco
- Uso de rede

Esses dados ajudam a estimar o tamanho correto no Azure.

---

## 🧠 Importante sobre a coleta

- É recomendável coletar dados por pelo menos **7 dias**
- Coletar por mais tempo melhora precisão
- O Azure Migrate usa esses dados para recomendar tamanhos de VM no Azure

---

## 📊 Verificar resultados

No Portal do Azure:

1. Acesse **Servidores descobertos**
2. Confirme se cada servidor físico aparece
3. Verifique inventário e métricas coletadas
4. Se faltar algum servidor, verifique:
   - Conectividade
   - Permissões
   - Firewall

---

## 🛡 Boas práticas

✔️ Use contas com permissões mínimas necessárias  
✔️ Verifique conectividade antes de instalar agente  
✔️ Mantenha o agente ativo durante todo o período de coleta  
✔️ Reúna dados suficientes antes de passar para avaliação

---

## 📍 Próximos passos

Depois que todos os servidores físicos forem descobertos:

1. Crie **grupos lógicos** de servidores
2. Execute **assessments**
3. Avalie dimensionamento e estimativa de custos
4. Planeje estratégia de migração (ondas)

---

## 🧠 Conclusão

A descoberta de servidores físicos com Azure Migrate:

- Exige um agente em cada servidor
- Coleta inventário e dados de performance
- Gera base para avaliação e dimensionamento
- É requisito obrigatório para migrar servidores físicos ao Azure
