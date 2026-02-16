# 📊 Matriz de Suporte do Azure Migrate – Resumo

Este documento apresenta uma visão geral das **capacidades de suporte do Azure Migrate**, ou seja, quais tipos de servidores, sistemas operacionais, hipervisores e cenários de migração podem ser utilizados com as ferramentas do Azure Migrate.

---

## 🚀 1. Plataformas Suportadas

### 🖥️ Servidores Físicos

- Suportados para descoberta e migração com agentes.
- Suporte para Windows e distribuições populares de Linux.

### 🟦 VMware

- Suportado para descoberta, avaliação e migração de VMs.
- Inclui VMs gerenciadas via vCenter.

### 🟪 Hyper-V

- Suportado para descoberta e migração de VMs Hyper-V.
- Ferramentas permitem replicação e transferência.

---

## 🔐 2. Sistemas Operacionais Compatíveis

### 🪟 Windows

Suporte para várias versões, incluindo:

- Windows Server 2008 R2 e superiores
- Versões mais recentes com suporte estendido

### 🐧 Linux

Compatível com distribuições como:

- Red Hat Enterprise Linux (RHEL)
- CentOS
- Ubuntu
- SUSE
- Outras versões populares suportadas pela Microsoft

---

## 🧠 3. Tipos de Migração

### 🔄 Lift-and-Shift (“levantar e mover”)

- Migração “sem alterações” da arquitetura
- Replica servidores e VMs para Azure

### 🧩 Modernização

- Movimentar para Azure com adaptação de apps
- Refatorar serviços para aproveitar PaaS

---

## 🛠 4. Funcionalidades por Cenário

A matriz detalha, por cenário, o que cada ferramenta do Azure Migrate consegue fazer:

| Cenário | Descoberta | Avaliação | Migração |
|---------|------------|-----------|----------|
| VMware | ✔️ | ✔️ | ✔️ |
| Hyper-V | ✔️ | ✔️ | ✔️ |
| Servidores Físicos | ✔️ | ✔️ | ✔️ |
| SQL Server | ✔️ | ✔️ | ✔️ |
| Aplicações Web | ✔️ | ✔️ | ✔️ |

> Cada ferramenta dentro do Azure Migrate (descoberta, avaliação e migração) oferece diferentes níveis de suporte para cada tipo de servidor.

---

## 📦 5. Ferramentas e Tecnologias Envolvidas

### 🧰 Azure Migrate Discovery and Assessment

- Coleta inventário de máquinas
- Avalia compatibilidade para migração
- Mostra dependências entre servidores

### 📦 Azure Migrate Server Migration

- Replica servidores e VMs para Azure
- Pode usar agentes ou serviços sem agente

### 🧾 Database Assessment

- Avalia bancos de dados para migrar para serviços SQL no Azure

### 🔌 Migração de Aplicações Web

- Ajuda a mover aplicações web para Azure App Service ou VMs

---

## 📍 6. Considerações Importantes

- Nem todos os recursos são suportados para todos os tipos de servidor.
- Algumas funcionalidades estão disponíveis apenas para versões específicas de SO ou hipervisores.
- A matriz ajuda a determinar se o seu ambiente atual é compatível com Azure Migrate e qual ferramenta usar.

---

## 🧠 Como Usar essa Matriz

1. **Identifique o tipo de máquina/servidor** que você quer migrar.
2. **Verifique o sistema operacional e versão**.
3. **Consulte a matriz de suporte** para confirmar se a descoberta, avaliação e migração são possíveis.
4. **Escolha a ferramenta Azure Migrate adequada** para o cenário.
5. **Planeje a estratégia (lift-and-shift ou modernização)** com base no suporte disponível.

---

## ✅ Conclusão

A **Matriz de Suporte do Azure Migrate** é uma referência essencial para:

- Saber o que pode ser migrado
- Quais ferramentas usar em cada caso
- Evitar surpresas durante a migração

Use-a no planejamento para garantir que seus sistemas sejam compatíveis e que você escolha a abordagem certa para sua migração ao Azure.
