# Azure Migrate – Estimativa de Custo de Avaliações

As avaliações do **Azure Migrate** estimam o **custo mensal de hospedagem** das cargas recomendadas no Azure com base nos destinos dimensionados adequadamente. Essas estimativas são calculadas considerando as tarifas da **região selecionada**, ofertas aplicáveis e o **programa de licenciamento** configurado na avaliação. :contentReference[oaicite:0]{index=0}

---

## 📌 Visão Geral

- O objetivo é **estimativa de custos** para os recursos recomendados com base na avaliação.  
- Os custos são relativos aos **recursos dimensionados adequadamente** no Azure.  
- As estimativas dependem de:
  - Taxas da **região** escolhida.  
  - **Ofertas e descontos** aplicáveis.  
  - **Programa de licenciamento** selecionado. :contentReference[oaicite:1]{index=1}

---

## ⚙️ Configurações de Preço

As seguintes configurações de avaliação afetam as estimativas de custo:

### 💡 Opções de Poupança (Computação)

- Permite especificar a opção de economia para otimizar o custo de computação no Azure.
- **Reservas do Azure** (1 ou 3 anos) — bom para cargas constantes.
- **Plano de Poupança do Azure** (1 ou 3 anos) — flexibilidade adicional e otimização automatizada.  
- Se “Nenhum” for selecionado, o custo é baseado na taxa **Pay-as-you-go** considerando 730 horas de uso mensais (ou conforme configurado). :contentReference[oaicite:2]{index=2}

### 📜 Programa de Oferta/Licenciamento

- Escolha entre:
  - **Pagamento conforme o uso**
  - **Contrato Enterprise Agreement (EA)**
  - **Pagamento conforme o uso para Desenvolvimento/Teste**
- Para usar **Instâncias Reservadas** ou **Plano de Poupança**, deve selecionar **Pay-as-you-go** como oferta/licenciamento. :contentReference[oaicite:3]{index=3}

### 💱 Moeda

- A estimativa é calculada na **moeda de cobrança** da sua assinatura Azure. :contentReference[oaicite:4]{index=4}

### 📊 Desconto (%)

- Qualquer desconto **específico da assinatura** é aplicado além da oferta selecionada.  
- Padrão é **0%** se não configurado. :contentReference[oaicite:5]{index=5}

### ⏱️ Tempo de Atividade da VM

- Define o número de **dias por mês e horas por dia** que as VMs estarão em execução.
- A estimativa é ajustada com base nesse tempo informado.  
- Padrão: **31 dias × 24 horas**. :contentReference[oaicite:6]{index=6}

### 🪪 Benefício Híbrido do Azure

- Se habilitado, permite usar **licenças existentes com Software Assurance** (por exemplo, Windows ou Linux).
- Nesse caso, os preços do sistema operacional não são considerados para o custo da VM. :contentReference[oaicite:7]{index=7}

---

## ▶️ Como os Cálculos Funcionam (Resumo)

1. A avaliação gera recomendações de **tamanho adequado** dos recursos Azure. :contentReference[oaicite:8]{index=8}  
2. Com base nesses destinos, o Azure Migrate calcula o **custo mensal**: soma de recursos, licenças e serviços auxiliares conforme as configurações de preço. :contentReference[oaicite:9]{index=9}  
3. O resultado dá uma visão do custo esperado para hospedar os recursos migrados no Azure. :contentReference[oaicite:10]{index=10}

---

## 📌 Observações

- As estimativas **não são valores finais** de faturamento, mas projeções com base nos parâmetros da avaliação. :contentReference[oaicite:11]{index=11}  
- Valores podem mudar conforme a região, descontos, licenciamento e opções de poupança escolhidas. :contentReference[oaicite:12]{index=12}

---

## 🧭 Próximos Passos

- Ajustar as configurações de preço conforme sua estratégia de migração.  
- Recalcular a avaliação para ver cenários diferentes (por exemplo, com/ou sem reservas ou planos de saving).  
- Usar a **Ferramenta de Cálculo de Preços Azure** para aprofundar estimativas independentemente da avaliação. :contentReference[oaicite:13]{index=13}