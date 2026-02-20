# Azure Migrate – Visão Geral de Migração de Servidores

Este artigo descreve os **métodos de migração de servidores** usando o Azure Migrate, explicando quando usar **migração sem agente (agentless)** ou **baseada em agente**, e como esses métodos se aplicam a diferentes tipos de servidores.   

---

## 🔄 Métodos de Migração para Servidores

O Azure Migrate utiliza a ferramenta **Migrações para Azure: Migração e Modernização** para mover servidores locais (on-premises) para o Azure.   

### 🧠 1. Migração **Sem Agente** (Recomendada)

- **Recomendado quando possível**, especialmente para ambientes VMware e Hyper-V.  
- **Não requer agentes instalados nos sistemas operacionais das VMs**.  
- Usa **replicação com snapshots e Change Block Tracking (CBT)** para mover dados.  
- Suporta **descoberta, replicação, teste e migração final** sem agentes em VMs.  
- Ideal quando:
  - Os requisitos de pré-requisitos são atendidos.
  - O acesso a vCenter ou recursos de instantâneo está disponível. :contentReference[oaicite:2]{index=2}

---

## 🧩 2. Migração **Baseada em Agente**

Use este método quando uma ou mais das seguintes condições se aplicarem:

- **Pré-requisitos sem agente não são atendidos** (ex.: snapshots indisponíveis, restrições de API).  
- O **sistema operacional convidado não é compatível** com a hidratação sem agente.  
- **Configurações de disco/boot exigem suporte baseado em agente**.  
- **Fonte não é VMware ou Hyper-V** (por exemplo, servidores físicos, AWS, GCP, Xen, KVM).  
- Neste caso, **um agente (Mobility Service)** é instalado em cada máquina para habilitar replicação e migração.   

---

## 🖥️ Cenários de Migração

### 🟦 VMware vSphere

- **Sem agente (recomendado):**  
  - Usa replicação sem agentes através do Azure Migrate appliance.  
  - Automatiza hidratação para boot no Azure.  
- **Baseado em agente:**  
  - Usado quando os requisitos sem agente não são atendidos.  
  - Instala agentes de Mobilidade por VM. :contentReference[oaicite:4]{index=4}

---

### 🟩 Hyper-V

- **Sem agente:**  
  - Provedor do Azure Site Recovery e agentes são instalados nos hosts/clusters, sem necessidade de agentes nas VMs.  
- **Baseado em agente:**  
  - Use quando acesso ao host não está disponível ou as condições sem agente falham.  
  - Trate a VM como servidor físico.   

---

### 🟨 Servidores Físicos & Plataformas Não-Tradicionais

- **Migração baseada em agente:**  
  - Inclui servidores físicos, VMs de outras nuvens (AWS, GCP), Xen, KVM ou nuvens privadas.  
  - Cada máquina precisa do agente de Mobilidade para habilitar replicação e migração. :contentReference[oaicite:6]{index=6}

---

## 📌 Quando Usar Cada Método

| Método | Quando Usar |
|--------|-------------|
| **Sem Agente** | Quando os requisitos de infraestrutura e acesso permitem replicação sem agentes. |
| **Baseado em Agente** | Quando o ambiente não atende critérios de agente-less, sistemas operacionais não são suportados, ou a origem é física/fora de VMware/Hyper-V. |

---

## 🚀 Próximos Passos

Após escolher o método de migração adequado:

- Consulte tutoriais específicos para **migrar VMware vSphere** ou **Hyper-V**.  
- Planeje e execute a migração com a ferramenta **Migração e Modernização** no Azure Migrate. :contentReference[oaicite:7]{index=7}