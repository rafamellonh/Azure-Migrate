# Tutorial: Avaliar VMs do VMware para Migração para Azure VMs  
*Usando o Azure Migrate: Discovery and assessment tool*   

Este tutorial mostra como **criar uma avaliação** para máquinas virtuais em um ambiente **VMware vSphere** com o objetivo de medir a **prontidão para migração**, identificar **riscos** e gerar **estimativas de custo e tamanho** para execução das VMs no Azure.   

---

## 📌 Objetivos do Tutorial

Você aprenderá a: 

- Executar uma **avaliação baseada em metadados/configuração** dos servidores.  
- Executar uma **avaliação baseada em dados de desempenho** coletados.  
- Analisar os resultados para preparar o plano de migração.   

---

## ✅ Pré-requisitos

Antes de começar: :contentReference

✔ Os servidores que serão avaliados já devem estar **descobertos** no Azure Migrate.   https://learn.microsoft.com/pt-br/azure/migrate/tutorial-discover-vmware?view=migrate
- Isso pode ser feito com um **appliance de descoberta** no VMware.  
- Ou através de um **arquivo CSV importado** contendo metadata dos servidores.   

---

## 📌 Passo a Passo da Avaliação

### 1. Acessar a ferramenta de Avaliação

1. No portal Azure, vá em:  
   **Servidores, bancos de dados e aplicativos Web > Descobrir, avaliar e migrar**.   
2. Selecione **Azure Migrate: Discovery and assessment**.   
3. Clique em **Avaliar** e escolha **VM do Azure** como destino.   

---

## 🧠 2. Escolher o Tipo de Avaliação

Você precisa escolher entre **dois critérios de dimensionamento** para a avaliação:   

### ➤ Avaliação *As-Is* (Metadados/Configuração)

- Baseada nos **dados estáticos/metadados** coletados do servidor.  
- **Tamanho recomendado da Azure VM** é baseado no tamanho atual da VM local.  
- O **tipo de disco no Azure** pode ser escolhido com base no tipo de armazenamento selecionado.  
- Útil quando não há dados de desempenho suficientes coletados. 

### ➤ Avaliação *Performance-Based*

- Baseada em **dados reais de desempenho** da VM (CPU, memória, I/O).  
- O dimensionamento sugerido de VMs no Azure considera:
  - Utilização de CPU e memória
  - IOPS e throughput dos discos  
- Fornece recomendações de tamanho mais precisas e estimativas de custo mais realistas. 

---

## ⚙️ 3. Configuração da Avaliação

Ao configurar a avaliação, você pode ajustar várias propriedades:

### 📍 Propriedades de Destino

- **Região de destino** no Azure (impacta custo e disponibilidade).  
- **Tipo de armazenamento** (p. ex., SSD Premium, HDD Standard).  
- **Ofertas de economia** (Reservas Azure, Plano de economia).  
- **Benefício Híbrido do Azure** (para licenças que você já possui). 

### 📍 Critério de Dimensionamento

Se usar **baseado em desempenho**:
- Defina período de **histórico de desempenho** a considerar (ex: 7 dias).  
- Defina **percentil de utilização** (ex: 95%).  
- Configure **fator de conforto** para suportar picos e crescimento. 

### 📍 Configurações de Preço

- **Oferta/licenciamento** (Pay-as-you-go, EA, etc.).  
- **Moeda de cobrança**.  
- **Tempo ativo da VM** (dias/hora de operação por mês).  
- **Descontos adicionais** da assinatura Azure.

---

## 🧩 4. Criar e Executar a Avaliação

1. **Salvar as propriedades da avaliação** após revisão. 
2. **Criar um nome para a avaliação**. 
3. **Criar um grupo de servidores** para avaliação (adicionando os VMs). 
4. Selecione o **dispositivo de descoberta** (appliance ou importação). 
5. **Avançar e criar a avaliação**.

---

## 📊 5. Revisar os Resultados

Após a avaliação ser criada e executada, você pode revisar: 

### 🧠 Prontidão para Azure

- **Pronto para Azure** — pode migrar sem alterações.  
- **Pronto com condições** — pode necessitar ajustes antes da migração.  
- **Não pronto para Azure** — bloqueadores detectados.  
- **Prontidão desconhecida** — falta de dados ou erros. 

### 💰 Estimativas de Custo

- **Custo mensal de computação** no Azure estimado.  
- **Estimativa de armazenamento** baseado nos discos migrados. 

### 🔍 Visualização de Detalhes da Avaliação

- Você pode **explorar cada VM** para ver:
  - Tamanho recomendado
  - Custos por VM
  - Estatísticas de desempenho utilizadas
  - Problemas ou alertas detalhados :

---

## 🛠️ Solução de Problemas e Detalhes Extras

- Na seção de problemas, você pode visualizar **erros específicos** de avaliação e agir conforme necessário.
- Para **dados de desempenho melhores**, recomenda-se aguardar coleta de dados por um período (ex.: vários dias).

---

## 📌 Próximas Etapas

- Exportar a avaliação para **Excel para compartilhamento**.   
- Mapear dependências entre servidores para planejar ondas de migração.   
- Usar os resultados para **planejar migração efetiva** com as ferramentas de migração apropriadas.   