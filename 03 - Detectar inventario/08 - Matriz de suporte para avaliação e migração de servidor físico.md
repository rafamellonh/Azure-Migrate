# 📊 Azure Migrate – Matriz de Suporte para Migração de Servidores Físicos (Resumo)

Este documento apresenta os **recursos, requisitos e limitações** para usar o **Azure Migrate** quando o cenário envolve **servidores físicos** (não virtualizados) que serão migrados para o Microsoft Azure.

A matriz ajuda a verificar se o seu ambiente físico está pronto para descoberta, avaliação e migração antes de começar o projeto.

---

## 📌 Suporte a Descoberta de Servidores Físicos

O Azure Migrate pode descobrir servidores físicos quando você instala um **agente** de descoberta diretamente na máquina física.

O agente permite:

✔️ Inventário de hardware e sistema operacional  
✔️ Coleta de dados de performance  
✔️ Envio de informações para avaliação e dimensionamento

---

## 🛠 Requisitos para Descoberta

### 🧑‍💻 Conta e Permissões

Para cada servidor físico:

- Você precisa instalar um **agente de descoberta**
- A conta usada deve ter **permissões de administrador local** na máquina
  - Isso permite coletar inventário e métricas

---

## 💻 Suporte a Sistemas Operacionais

### 🪟 Windows

O Azure Migrate pode descobrir servidores Windows físicos quando:

- Windows Server 2008 R2 ou superior
- Serviços internos disponíveis (ex: PowerShell)

---

### 🐧 Linux

Também é suportado a descoberta de servidores Linux físicos com o agente, em versões de Linux comuns usadas em servidores (como RHEL, SUSE, CentOS, Ubuntu, etc.).

O agente coleta inventário e performance mesmo em Linux.

---

## 📊 Coleta de Dados de Performance

O agente instalado no servidor físico permite coletar:

✔️ CPU (uso médio e pico)  
✔️ Memória  
✔️ I/O de disco  
✔️ Throughput de rede

Esses dados são essenciais para fazer uma **avaliação precisa e dimensionar corretamente** os servidores no Azure.

---

## 🧱 Inventário de Software

Em servidores físicos, quando o agente está corretamente instalado:

- Você pode coletar informações de software instalado
- Listas de aplicações e componentes importantes
- Dependências internas do sistema

---

## ⚠️ Itens não suportados / Restrições

### ❌ Não há suporte para descoberta sem agente
- Ao contrário de ambientes VMware (*agentless*), **não há descoberta sem agente** para servidores físicos.
- **O agente é obrigatório.**

### ❌ Limitações de escopo
- O inventário de software pode depender do tipo de sistema operacional e das ferramentas disponíveis no servidor (ex.: PowerShell em Windows).

---

## 📌 Resumo dos Pontos Suportados

| Aspecto | Suporte |
|---------|---------|
| Descoberta sem agente | ❌ Não suportado para servidores físicos |
| Descoberta com agente | ✔️ Suportado |
| Coleta de inventário | ✔️ Inclui hardware e SO |
| Coleta de performance | ✔️ CPU, memória, disco, rede |
| Software inventory | ✔️ Quando agente instalado |
| Sistema operacional Windows | ✔️ Suportado |
| Sistema operacional Linux | ✔️ Suportado |

---

## 🧠 Como Usar Essa Matriz

Antes de iniciar a migração:

1. Liste os servidores físicos que pretende migrar  
2. Verifique se cada um tem **SO suportado**
3. Confirme que você conseguirá instalar o **agente**
4. Garanta acesso de administrador local para instalar e rodar o agente
5. Planeje o período de coleta de dados (ideal >= 7 dias)

---

## 📌 Conclusão

A **matriz de suporte para servidores físicos** mostra que:

✔️ A migração de servidores físicos usando Azure Migrate **é suportada**  
✔️ É necessário instalar um **agente em cada servidor**  
✔️ O agente coleta inventário e métricas que permitem dimensionamento e avaliação  
✔️ A descoberta sem agente **não é possível para servidores físicos**

Essa matriz ajuda a **validar compatibilidade antes de iniciar o projeto** e evitar surpresas durante a migração.

