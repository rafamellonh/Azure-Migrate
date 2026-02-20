# Azure Migrate – Como Completar um Plano de Onda (High-Fidelity Wave Plan)

Este guia mostra como **completar e preparar um plano de onda de migração de alta fidelidade** no Azure Migrate — definindo destinos, tarefas, ferramentas, pré-requisitos e configuração para que a onda esteja **pronta para execução**.   

---

## 🎯 Objetivo

Criar um **plano de migração detalhado e previsível** para cada onda, incluindo:

- Destinos e caminhos de migração
- Ferramentas e atividades a executar
- Pré-requisitos e tarefas pendentes
- Cronogramas e datas planejadas

Tudo isso ajuda a garantir que a migração ou modernização ocorra sem surpresas e com acompanhamento claro. :contentReference[oaicite:2]{index=2}

---

## 1) Identificar Destinos de Migração no Azure

Antes de iniciar a migração de workloads e aplicações:

- **Determine os destinos no Azure** apropriados para cada workload.  
- Utilize os **resultados da avaliação** (assessments) para saber qual destino o Azure Migrate recomenda.     
- Atenção: em alguns casos (ex.: configurações de SKU detalhadas), apenas migrações integradas oferecem recomendações completas. :contentReference[oaicite:4]{index=4}

---

## 2) Configurar **Targets** e Tarefas por Aplicação

No planejamento de onda, você pode:

### 📌 Aplicação

- **Linkar uma avaliação** existente para obter destinos e caminhos recomendados.  
- **Adicionar tarefas gerais da aplicação** além das migrações (manuais, revisões, dependências, testes).  
- Essas tarefas ficam visíveis e rastreáveis no plano.   

---

## 3) Configurar **Workload Targets** e Tarefas por Workload

Para cada workload da onda:

- **Revisar e configurar destino de Azure** (VM, banco de dados, app service, etc.).  
- Selecionar **ferramenta de migração** apropriada (ex.: Azure Migrate Server Migration, DMS, ou outro).  
- Adicionar tarefas específicas de migração (testes, validações, automações).  
- Marcar workloads que **não serão migrados** (por exemplo, planos de descomissionamento). :contentReference[oaicite:6]{index=6}

---

## 4) Preparar a Onda para Execução

Antes de iniciar a migração da onda:

- Acesse as **configurações da onda** para rever o status e itens pendentes.  
- **Adicionar tarefas de pré-requisito** que precisam ser concluídas antes da execução (ex.: configuração de rede, aprovações de segurança, backups).  
- Salve e verifique que todas as tarefas necessárias estejam registradas.  
- O Azure Migrate exibirá essas tarefas no estágio de **configuração** da onda. :contentReference[oaicite:7]{index=7}

---

## 5) Transição para “Pronto para Execução”

Depois de:

- Configurar destinos e ferramentas,
- Definir tasks (tarefas),
- Preencher pré-requisitos,
- Ajustar datas planejadas,

o estado da onda muda para **Ready for Execution** (*Pronto para Execução*).  
Isso indica que a migração pode ser iniciada conforme o cronograma.   

---

## 🗓 Datas e Planejamento

- Você pode **ajustar datas planejadas de início e término** diretamente nas configurações da onda, conforme necessário.  
- Datas bem definidas ajudam no acompanhamento e nas metas de migração.   

---

## 🚀 Próximos Passos

Após completar o plano de onda:

1. Iniciar a **execução da onda** usando o Azure Migrate ou ferramentas suportadas.  
2. **Monitorar o progresso** e atualizar tarefas à medida que são concluídas.  
3. Usar o status da onda para comunicar estado e etapas para stakeholders. :contentReference[oaicite:10]{index=10}