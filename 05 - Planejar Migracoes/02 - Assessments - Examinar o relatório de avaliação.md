# Azure Migrate – Relatório de Avaliação

O **relatório de avaliação** do Azure Migrate resume os principais resultados de uma avaliação criada para migrar workloads para o Azure.  
Cada avaliação produz **4 resultados principais**:  
1. **Prontidão para Azure**  
2. **Recomendações de dimensionamento adequado**  
3. **Detalhes de custo**  
4. **Diretrizes de migração** :contentReference[oaicite:0]{index=0}

---

## 🧠 1. Prontidão para Azure

Avalia se os workloads estão prontos para migrar para Azure, com categorias típicas:

- **Pronto para Azure** – Pode ser migrado “as-is”.  
- **Condicionalmente pronto** – Pode iniciar no Azure, mas pode ter suporte limitado.  
- **Não pronto** – Não poderá ser iniciado no Azure até que problemas sejam corrigidos.  
- **Preparação desconhecida** – Sem dados suficientes para determinar a prontidão. :contentReference[oaicite:1]{index=1}

---

## 📏 2. Recomendações de Dimensionamento Adequado

Depois de marcado como pronto, a avaliação gera recomendações de dimensionamento para o ambiente de destino no Azure:

### Tipos de dimensionamento

- **Baseado em desempenho**  
  Usa dados coletados de desempenho para calcular recomendações de CPU, memória e armazenamento.  
- **Estado atual no local (as-is)**  
  Baseia-se apenas nas configurações existentes.  

Os dados de desempenho e percentis configurados influenciam as recomendações finais. :contentReference[oaicite:2]{index=2}

---

## 💰 3. Cálculo de Custos Mensais

Após escolher os candidatos de destino com dimensionamento adequado:

- A avaliação calcula o **custo mensal estimado total**, incluindo recursos, licenças e serviços auxiliares (ex.: segurança).  
- Se houver múltiplos alvos possíveis, a estratégia de custo (por exemplo, *minimizar custo*) determina o recomendado. :contentReference[oaicite:3]{index=3}

---

## 📊 4. Cobertura de Desempenho (para avaliações baseadas em desempenho)

- A cobertura de desempenho varia de **0% a 100%** e representa a **qualidade dos dados de desempenho coletados** para dimensionamento.  
- Cobertura baixa pode indicar falta de dados suficientes (ex.: servidores desligados, tempo curto de coleta).  
- Azure recomenda esperar por dados adicionais ou ajustar a avaliação para melhorar a confiabilidade. :contentReference[oaicite:4]{index=4}

---

## 📌 Observações Importantes

- As avaliações são **instantâneos de dados num ponto no tempo** — resultados podem mudar conforme novos dados ou alterações no ambiente. :contentReference[oaicite:5]{index=5}  
- A cobertura de desempenho **não se aplica** quando os dados vêm de arquivo CSV importado ou em avaliações “as-is” sem performance. :contentReference[oaicite:6]{index=6}

---

## 👉 Próximos Passos Após o Relatório

- Revisar as **melhores práticas** para ajustes de avaliação.  
- Recriar ou recalcular avaliações para refletir novos dados.  
- Analisar dependências e preparar o plano de migração baseado no relatório. :contentReference[oaicite:7]{index=7}