# Azure Migrate – Visão Geral de Avaliação

Uma **avaliação no Azure Migrate** é usada para analisar cargas de trabalho locais (on-premises) ou em outras nuvens públicas e determinar a preparação para migrar para o Azure. :contentReference[oaicite:0]{index=0}

---

## 🔍 O que uma Avaliação Faz

Cada avaliação do Azure Migrate examina:

- **Estratégia de migração**  
  Um plano para migrar todas as cargas de trabalho que compõem um aplicativo. :contentReference[oaicite:1]{index=1}

- **Preparação (Readiness)**  
  Verifica se as cargas de trabalho são adequadas para destinos válidos no Azure. :contentReference[oaicite:2]{index=2}

- **Tamanho certo (Right-sizing)**  
  Recomenda o dimensionamento ideal de recursos com base em desempenho e custo. :contentReference[oaicite:3]{index=3}

- **Custo de recursos no Azure**  
  Estima o custo mensal de hospedar as cargas migradas no Azure. :contentReference[oaicite:4]{index=4}

- **Ferramenta de migração recomendada**  
  Indica qual ferramenta deve ser usada para a migração. :contentReference[oaicite:5]{index=5}

---

## 📊 Tipos de Avaliações

O Azure Migrate oferece dois tipos principais de avaliação:

- **Avaliações de Aplicativos**  
  Incluem cargas de trabalho combinadas (como servidores, web apps e bancos de dados) que fazem parte de um aplicativo. :contentReference[oaicite:6]{index=6}

- **Avaliações de Carga de Trabalho**  
  Avaliam cargas específicas para identificar destino de tamanho certo e custo de recurso no Azure. :contentReference[oaicite:7]{index=7}

### Workloads Suportados

| Tipo de Carga de Trabalho | Destino/Ação |
|---------------------------|--------------|
| **Servidores** | VM no Azure |
| **AVS (Azure VMware Solution)** | Migração para AVS |
| **Servidores e bancos de dados SQL** | Azure SQL (DB, Managed Instance ou SQL em VM) |
| **Aplicativos Web** | Azure App Service / Azure Spring Apps / AKS | :contentReference[oaicite:8]{index=8}

---

## 📌 Pré-requisitos para Avaliações

Antes de criar uma avaliação:

- **Inventário deve estar preenchido** (descoberta concluída). :contentReference[oaicite:9]{index=9}
- É recomendado ter acesso às assinaturas necessárias (especialmente clientes com EA). :contentReference[oaicite:10]{index=10}
- Para descobertas baseadas em appliance, os dispositivos devem estar conectados com dados de desempenho fluindo. :contentReference[oaicite:11]{index=11}

---

## 📥 Fontes de Descoberta

As cargas de trabalho podem ser descobertas por:

- **Appliance leve do Azure Migrate** (sem agentes) – recomendado. :contentReference[oaicite:12]{index=12}
- **Descoberta baseada em importação** usando arquivos com informações de inventário. :contentReference[oaicite:13]{index=13}

---

## 📊 Como os Cálculos da Avaliação Funcionam

Uma avaliação geralmente calcula:

1. **Preparação para Azure**
2. **Recomendações de Tamanho Certo**
3. **Estimativa de Custo Mensal**

> Apenas cargas que passam na etapa de preparação seguem para as etapas de dimensionamento e custo. :contentReference[oaicite:14]{index=14}

---

## ⚙️ Configurações da Avaliação

Você pode definir:

- **Configurações de destino**  
  (ex: região, tipo de ambiente, família de instância) :contentReference[oaicite:15]{index=15}
  
- **Configurações de preço**  
  (ex: contrato EA, economia com reservas) :contentReference[oaicite:16]{index=16}

- **Fatores de dimensionamento e performance**  
  (como percentil de utilização e buffers para estimativas) :contentReference[oaicite:17]{index=17}

---

## 🧠 Observações

- Os resultados de avaliação são um **instantâneo** baseado nos dados coletados até o momento. :contentReference[oaicite:18]{index=18}

---

## 🛠 Próximas Etapas

Depois de criar o inventário e a avaliação:

- Agrupe cargas de trabalho relevantes. :contentReference[oaicite:19]{index=19}
- Execute a avaliação com o tipo apropriado. :contentReference[oaicite:20]{index=20}
- Use os resultados para planejar migração e estimar custos. :contentReference[oaicite:21]{index=21}