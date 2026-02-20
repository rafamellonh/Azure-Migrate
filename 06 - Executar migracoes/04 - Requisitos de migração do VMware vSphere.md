# Azure Migrate – Matriz de Suporte para Migração VMware vSphere

Este guia lista os **requisitos, limitações e suporte** para migrar máquinas virtuais **VMware vSphere** para o Azure usando o serviço **Azure Migrate + Migração e Modernização**.   

---

## ⚙️ Opções de Migração

Você pode migrar VMs VMware vSphere ao Azure de duas maneiras: :contentReference[oaicite:2]{index=2}

- **Migração sem agente (Agentless)**  
  Não requer instalação de software nas VMs; usa um *appliance* para replicar.   

- **Migração baseada em agente (Agent-Based)**  
  Instala um agente (Mobility Service) dentro das VMs para habilitar a replicação. :contentReference[oaicite:4]{index=4}

---

## 🛠️ Migração **Sem Agente** – Requisitos

### 🔹 Requisitos do Ambiente VMware

- **vCenter Server:** versões 8.0, 7.0, 6.7 ou 6.5.  
- **Hosts ESXi:** versões 8.0, 7.0, 6.7 ou 6.5.  
- O *appliance* pode conectar até **10 vCenter Servers**.  
- A conta VMware precisa de **permissões completas** em datacenter, clusters, hosts, VMs e datastores.   

### 🔹 Requisitos da VM

- **Sistemas operacionais Windows e Linux suportados** — versões com suporte no Azure.  
- Para Linux, algumas versões podem precisar de ajustes; certas configurações (ex.: SELinux *Enforced*) não são totalmente suportadas.  
- Requisitos especiais de boot:
  - `/boot` precisa estar no **mesmo disco do sistema operacional**.  
  - VMs UEFI podem usar **Geração 2** no Azure (sem Secure Boot). :contentReference[oaicite:6]{index=6}

### 🔹 Armazenamento e Discos

- **Discos de sistema operacional até 2 TB (Gen1) / até 4 TB (Gen2)** e até **32 TB para discos de dados**.  
- **Disco dinâmico de SO não é suportado** sem conversão para básico.  
- **Discos Ultra e alguns recursos de armazenamento** (RDM, discos independentes, iSCSI volumes) **não são suportados diretamente**. :contentReference[oaicite:7]{index=7}

### 🔹 Outros Limites

- **Sem suporte a IPv6**.  
- **Discos NVMe** não são suportados.  
- **Clusters de disco compartilhado e NFS volumes** não serão replicados.  
- Até **300 replicações simultâneas** por vCenter com um dispositivo, ou **500** com um dispositivo de expansão.   

---

## 🔁 Migração **Baseada em Agente**

- Requer instalação do **Mobility Service** nas VMs para habilitar a replicação.  
- Deve ser usada quando a migração sem agente **não é possível**, por exemplo:
  - VMs com requisitos específicos ou limitações do ambiente.  
  - Hipervisores/versões que não atendem aos requisitos sem agente.   

---

## ⚠️ Observações Importantes

- O artigo pode referenciar **distribuições ou versões em fim de vida** (como CentOS EOL). Avalie a compatibilidade de acordo com seus requisitos de suporte.  
- Várias versões antigas de **Windows Server estão no fim de suporte** — resultados não são garantidos para essas versões. :contentReference[oaicite:10]{index=10}

---

## 📌 Próximas Etapas

- Use estas diretrizes para **planejar a migração** e escolher o método mais adequado (agentless ou agent-based).  
- Combine com a **matriz de avaliação** para verificar compatibilidade antes de migrar. :contentReference[oaicite:11]{index=11}