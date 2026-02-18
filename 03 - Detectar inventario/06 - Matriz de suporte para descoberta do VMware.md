# 📊 Azure Migrate – Matriz de Suporte para VMware vSphere (Resumo)

Este documento apresenta os **requisitos e o suporte disponível** ao usar o **Azure Migrate** para avaliar e migrar máquinas virtuais VMware vSphere para o Microsoft Azure. :contentReference[oaicite:1]{index=1}

---

## 🎯 Visão Geral

A matriz de suporte descreve:

- Quais sistemas e recursos são suportados
- Requisitos para inventário e assessment
- Funcionalidades de software inventory
- Requisitos do appliance usado para descoberta e avaliação

Ela é útil para garantir que o ambiente VMware esteja pronto para uso com o Azure Migrate antes de iniciar a migração. :contentReference[oaicite:2]{index=2}

---

## 🖥️ 1. Suporte a Sistemas Operacionais

### 🪟 Windows e Linux

- Todas as versões de Windows e Linux podem ser **avaliadas para migração**.
- Não há limitação explícita do SO para assessment — basta que a VM esteja acessível via vCenter. :contentReference[oaicite:3]{index=3}

---

## 🗄️ 2. Suporte a Discos e Armazenamento

- Discos conectados via **SCSI, IDE e SATA** são suportados para avali acão e migração. :contentReference[oaicite:4]{index=4}

---

## 🛠 3. Azure Migrate Appliance – Requisitos

O **appliance do Azure Migrate** é usado para:

- Descoberta de servidores
- Coleta de inventário
- Software inventory
- Dados de performance

Esse appliance roda em seu ambiente VMware e envia dados para o Azure Migrate. :contentReference[oaicite:5]{index=5}

### 🌐 Funcionalidades habilitadas pelo appliance

- **Descoberta de VMs VMware**
- **Software Inventory** (listas de apps/roles/features)
- Suporte para até **10.000 servidores** para software inventory por appliance :contentReference[oaicite:6]{index=6}

---

## 📦 4. Software Inventory

Isso vai além de descobrir a VM física:

- Lista aplicativos, recursos e roles instalados nas VMs
- Suporta Windows e Linux :contentReference[oaicite:7]{index=7}

### 📌 Requisitos para Software Inventory

- **VMware Tools** deve estar instalado e em execução (versão 10.2.1 ou mais recente) :contentReference[oaicite:8]{index=8}  
- Para Windows, o **PowerShell 2.0 ou posterior** deve estar presente na VM :contentReference[oaicite:9]{index=9}

Sem essas condições, o software inventory pode não coletar corretamente os dados ou falhar.

---

## 🔍 5. Escopo de Inventário Suportado

- Você pode realizar software inventory em até **10.000 servidores** por appliance. :contentReference[oaicite:10]{index=10}

Isso permite coletar informações detalhadas de um grande número de VMs sem necessidade de ferramentas adicionais.

---

## 💡 Pontos Importantes

✅ A matriz de suporte **não limita o assessment de SO** — desde que o VMware e appliance estejam corretamente configurados. :contentReference[oaicite:11]{index=11}  
✅ O foco está mais em **recursos do ambiente (vCenter/VMs)** e **requisitos de software inventory**. :contentReference[oaicite:12]{index=12}  
✅ Para funcionalidades específicas como software inventory, **componentes adicionais** são necessários (por exemplo, VMware Tools). :contentReference[oaicite:13]{index=13}

---

## 📍 Conclusão

A **Support Matrix para VMware vSphere Migration** no Azure Migrate esclarece:

✔️ Quais recursos de inventário e avaliação são suportados  
✔️ Quais requisitos precisam estar presentes nas VMs e no ambiente VMware  
✔️ Limitações especificas para software inventory  
✔️ Como o appliance atua para coletar dados

Ela é essencial para verificar compatibilidade antes de iniciar a migração de seu ambiente VMware para o Azure.

---

