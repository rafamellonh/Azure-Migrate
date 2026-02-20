# Azure Migrate – Planejar e Criar Ondas de Migração

A funcionalidade de **Planejamento de Ondas (Migration Waves)** no Azure Migrate permite agrupar workloads e aplicações em **lotes lógicos menores (ondas)** para planejar, sequenciar e migrar fases da migração com mais eficiência, visibilidade e menor risco. :contentReference[oaicite:0]{index=0}

---

## 🎯 Por que usar Planejamento de Ondas

- **Agrupar cargas de trabalho relacionadas:** Sistemas com dependências ou requisitos comuns podem ser migrados juntos para evitar interrupções. :contentReference[oaicite:1]{index=1}  
- **Sequenciar migrações:** Priorize ondas com base em criticidade de negócios, complexidade e impacto. :contentReference[oaicite:2]{index=2}  
- **Paralelizar quando seguro:** Execute ondas independentes simultaneamente para acelerar o processo. :contentReference[oaicite:3]{index=3}  
- **Gerenciar grandes projetos:** Divide migrações extensas em partes menores e gerenciáveis. :contentReference[oaicite:4]{index=4}

> O planeamento de ondas é opcional — você **não precisa dele para migrar**, mas ele ajuda a organizar migrações em grande escala. :contentReference[oaicite:5]{index=5}

---

## 📌 Pré-requisitos

Antes de planejar ondas efetivamente:

- Tenha um **projeto ativo no Azure Migrate** com descoberta completa de infraestrutura. :contentReference[oaicite:6]{index=6}  
- Garanta que o inventário e análise de dependências estejam completos, o que ajuda a agrupar workloads que precisam ser migrados juntos. :contentReference[oaicite:7]{index=7}  
- Realize **avaliações** para insights sobre prontidão e destinos de migração recomendados. :contentReference[oaicite:8]{index=8}  

---

## 🧠 Criar Ondas no Portal Azure Migrate

1. **Abra seu projeto** em *Todos os Projetos* no portal Azure. :contentReference[oaicite:9]{index=9}  
2. No painel **Visão Geral**, clique em **Criar Onda**. :contentReference[oaicite:10]{index=10}  
3. Defina um **nome único** para a onda e a **data de início planejada**. :contentReference[oaicite:11]{index=11}  
4. *Opcional:* selecione uma **Avaliação** para usar recomendações de destino e configuração. :contentReference[oaicite:12]{index=12}  
5. Escolha os **workloads e aplicações** a incluir na onda (use filtros para ajudar na seleção). :contentReference[oaicite:13]{index=13}  
6. Após revisar sua seleção, clique em **Criar Onda**. :contentReference[oaicite:14]{index=14}  
7. Visualize as ondas criadas com **Exibir Ondas** na visão geral do projeto. :contentReference[oaicite:15]{index=15}

> Se uma avaliação foi selecionada, as workloads e aplicações serão atribuídas por padrão aos destinos e configurações definidos nessa avaliação. :contentReference[oaicite:16]{index=16}

---

## 🗂️ Conceitos Importantes

### 📍 O que é uma Onda  
Uma **Onda de Migração** é um grupo lógico de workloads e aplicações planejadas para migração dentro de um mesmo intervalo de tempo ou fase de projeto. :contentReference[oaicite:17]{index=17}

### 🕒 Datas Planejadas  
Ao criar uma onda, você define datas de **início** e (opcionalmente) **término**, que ajudam a acompanhar o progresso da execução da migração. :contentReference[oaicite:18]{index=18}

### 📊 Status da Onda  
As ondas podem ter status que indicam progresso, como:
- **Não iniciado**
- **No caminho certo**
- **Em risco**
- **Concluído** :contentReference[oaicite:19]{index=19}

---

## ❓ Perguntas Comuns

- **O planejamento de ondas é obrigatório?**  
  Não — é uma opção guiada para organizar migrações em fases gerenciáveis. :contentReference[oaicite:20]{index=20}

- **Por que não consigo adicionar um app a uma onda?**  
  Se alguma workload do app já estiver em outra onda, você precisa ajustar seleções ou mover workloads individualmente. :contentReference[oaicite:21]{index=21}

- **Como garantir que as ondas mostrem dados recentes?**  
  Após criar, editar ou excluir uma onda, use *Refresh* para atualizar os dados exibidos. :contentReference[oaicite:22]{index=22}

---

## 🚀 Próximos Passos na Migração por Ondas

Após criar as ondas:

- Execute as migrações conforme os grupos planejados.  
- Monitore o progresso, identifique riscos e faça ajustes conforme necessário.  
- Use o planejamento de ondas para manter a migração organizada e alinhada com o calendário e prioridades de negócios.

> Para um plano ainda mais detalhado (ex.: adicionar tarefas de migração ou configurar targets), consulte o guia de execução de ondas no portal Azure Migration. :contentReference[oaicite:23]{index=23}