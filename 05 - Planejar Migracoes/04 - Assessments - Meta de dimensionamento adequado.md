# Azure Migrate – Meta de Dimensionamento Adequado (Right-Sizing)

O **dimensionamento adequado** no Azure Migrate ajuda a recomendar o **tamanho ideal das VMs e discos de destino no Azure** com base na análise da carga de trabalho avaliada.  
As recomendações de tamanho são geradas **depois de verificar a prontidão da carga para Azure** e influenciam também **estimativas de custos de hospedagem**.   

---

## 🎯 Objetivo

Fornecer recomendações de **tamanho de destino corretas para suas cargas de trabalho**, evitando:

- **Superprovisionamento** — o que pode aumentar custos sem ganhos de desempenho.  
- **Subdimensionamento** — que pode impactar a performance das aplicações no Azure.   

---

## 🔧 Critérios de Dimensionamento (Sizing Criteria)

O Azure Migrate oferece **2 métodos de dimensionamento**:

### 1. 📈 **Baseado em desempenho (Performance-Based)**

- Recomendação de tamanho baseada nos **dados de desempenho coletados** do workload local:
  - **CPU e memória** para cálculo da VM.  
  - **IOPS e throughput** para recomendação de discos.  
- Os dados de desempenho são coletados no ambiente local (ex.: VMware ou Hyper-V) ou importados via CSV.  
- Usar percentual (ex: percentil 95) e fator de conforto ajuda a ajustar a recomendação para picos de uso. :contentReference[oaicite:2]{index=2}

### 2. 🏠 **As-Is (Estado atual)**

- Não usa dados de desempenho — baseia-se apenas no **tamanho e configuração atuais no local**.  
- A recomendação de computação e armazenamento segue diretamente a configuração existente.  
- Útil quando não há dados de desempenho disponíveis ou quando se deseja manter o “tamanho atual”.   

---

## 🧠 Como funciona o Dimensionamento com Base em Desempenho

### 🔄 Coleta de Dados
Quando há um appliance de descoberta ativo:

- **VMware VMs:** amostras coletadas a cada 20s.  
- **Hyper-V VMs:** amostras a cada 30s.  
- **Servidores físicos:** amostras a cada 5 min.  
- Pontos de dados são agregados e enviados ao Azure para modelagem. :contentReference[oaicite:4]{index=4}

### 📊 Processamento de Dados

- O sistema identifica um **valor de utilização** (por exemplo, percentil 95) para cada métrica.  
- Exemplo: um servidor com 16 vCPUs pode usar apenas 20% das CPUs no percentil 95 → VM recomendada com **4 vCPUs**.  
- Um **fator de conforto** pode ampliar essa recomendação (ex.: 1.5x → 8 vCPUs).   

### 💽 Dimensionamento de Discos

- O recomendado é baseado em IOPS e throughput coletados.  
- Para vários discos, pode haver múltiplas opções recomendadas (com base em utilização e tamanhos disponíveis no Azure). :contentReference[oaicite:6]{index=6}

---

## 💡 Observações Importantes

- **Aplicações web** não coletam dados de desempenho pelo appliance → sempre avaliadas em modo **As-Is**.  
- **Servidores e bancos de dados** (SQL, MySQL, PostgreSQL) são elegíveis aos dois métodos.  
- Escolher **performance-based** normalmente resulta em recomendações mais precisas e custo otimizado. :contentReference[oaicite:7]{index=7}

---

## 📌 Quando Usar Cada Método

| Método | Quando usar |
|--------|--------------|
| **Performance-based** | Quando há coleta de dados de desempenho suficiente e você quer otimizar custo × performance. |
| **As-Is** | Quando não há histórico de performance ou quando quer manter a configuração atual. |

---

## 🚀 Próximos Passos

- Após definir o critério de dimensionamento, execute a **avaliação no Azure Migrate**.  
- Revise os resultados de right-sizing no **relatório de avaliação**.  
- Use as recomendações para fins de **planejamento de migração e estimativas de custo**.   