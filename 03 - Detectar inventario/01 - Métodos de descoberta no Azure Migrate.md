# 🔍 Azure Migrate – Métodos e Modos de Descoberta (Resumo)

Este documento explica os **métodos e modos de descoberta** usados pelo **Azure Migrate** para identificar e coletar informações sobre servidores e VMs no seu ambiente local antes da migração.

---

## 📌 O que é Descoberta?

A descoberta é o processo em que o Azure Migrate **coleta inventário, configurações e dependências** das máquinas que serão migradas.

Isso é fundamental para que você possa:

- Avaliar compatibilidade
- Calcular tamanhos de destino no Azure
- Planejar a migração corretamente

---

## 🧠 Principais Métodos de Descoberta

Azure Migrate oferece dois **métodos** principais para coletar informações:

---

## 🧰 1️⃣ Descoberta *Agentless* (sem agente)

### Como funciona
- Não exige instalação de software dentro da máquina.
- Usa APIs do ambiente de virtualização (ex: VMware vCenter ou Hyper-V).
- O Azure Migrate acessa os dados diretamente.

### Vantagens
✔️ Sem impacto direto nas máquinas  
✔️ Mais simples de configurar  
✔️ Bom para ambientes VMware e Hyper-V  

### Quando usar
- Quando você não quer instalar agentes nas VMs.
- Ambientes grandes onde instalar agente seria difícil.  

---

## 🛠 2️⃣ Descoberta com Agente

### Como funciona
- Um **agente é instalado em cada máquina** que será descoberta.
- O agente coleta dados mais detalhados sobre o sistema.

### Vantagens
✔️ Visão mais profunda das dependências internas  
✔️ Mais dados sobre performance da máquina  

### Quando usar
- Quando você precisa de dependências detalhadas (como processos internos)
- Em servidores físicos ou quando o método *agentless* não é suficiente

---

## ⚙️ Modos de Descoberta

Além dos métodos, existem **modos** de descoberta que determinam como o inventário é coletado:

---

### 👉 1. **Descoberta Inicial**
- Primeiro passo para capturar informações da máquina.
- Coleta dados básicos como:
  - Nome da máquina
  - Sistema operacional
  - Configurações de hardware

---

### 👉 2. **Execução de Descoberta Contínua**
- Após a descoberta inicial, o sistema continua coletando informações ao longo do tempo.
- Isso garante que novas mudanças sejam capturadas antes da migração.

---

## 🧠 Comparação Rápida

| Característica | Agentless | Com Agente |
|----------------|-----------|------------|
| Instalação de software | ❌ Não | ✅ Sim |
| Impacto na máquina | 🔹 Baixo | 🔸 Moderado |
| Detalhamento de dados | 🔹 Básico | 🔸 Avançado |
| Adequado para VMware/Hyper-V | ✔️ | ✔️ |

---

## 📍 Considerações Importantes

✅ A escolha do método depende do seu ambiente  
✅ Em muitos casos, o *agentless* é suficiente  
✅ Se precisar de **detalhamento mais profundo**, use o modo com agente

---

## 📌 Resumo

- A **descoberta** é a etapa que coleta as informações das máquinas antes da migração.
- Pode ser feita de dois modos:
  - **Sem agente** (mais simples e sem instalação)
  - **Com agente** (mais detalhado)
- Escolha o método com base na **quantidade de detalhes que você precisa** e nas **restrições do seu ambiente**.

---

## 🎯 Objetivo Final

Garantir que:

✔️ Você saiba exatamente o que está migrando  
✔️ Planeje corretamente os recursos no Azure  
✔️ Evite surpresas durante a migração

