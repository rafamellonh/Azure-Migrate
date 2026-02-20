# Migrar VMs VMware para Azure (Sem Agente) – Azure Migrate

Este tutorial ensina como **migrar máquinas virtuais VMware on-premises para o Azure** usando o **Azure Migrate + Migração e Modernização** no modo **sem agente**, que é o método recomendado.   

---

## 🎯 Objetivo do Tutorial

Neste tutorial, você aprende a:   

1. Adicionar a ferramenta **Migração e Modernização** ao projeto Azure Migrate.  
2. Descobrir VMs VMware que serão migradas.  
3. Iniciar a **replicação** das VMs para o Azure.  
4. Executar uma **migração de teste** para verificar tudo.  
5. Realizar a **migração completa** das VMs para o Azure. :contentReference[oaicite:2]{index=2}

---

## 🧰 Pré-requisitos

Antes de começar:   

✔ Concluir o **tutorial de preparação do Azure e VMware**.  
✔ (Recomendado) concluir o **tutorial de avaliação** das VMs VMware antes da migração.  
✔ Já ter um **projeto Azure Migrate** criado.  
✔ Sua conta Azure deve ter permissões para criar VMs e gravar em discos gerenciados.  
✔ A conta deve ter as funções integradas do Azure Migrate necessárias. :contentReference[oaicite:4]{index=4}

---

## 🔧 1. Configurar o Dispositivo de Migração

A **Ferramenta de Migração e Modernização** executa um **appliance leve no VMware** (VM) que:   

- Faz *discovery* e *assessement*.  
- Permite **replicação sem agente** das VMs.  

Configure o appliance de uma das formas: :contentReference[oaicite:6]{index=6}

- **OVA Template**: Implante uma VM no vCenter usando o OVA baixado.  
- **Script PowerShell**: Use um script para instalar o appliance onde o OVA não for possível (ex.: Azure Gov). :contentReference[oaicite:7]{index=7}

Depois de criado, conecte e *registre* o appliance no **projeto Azure Migrate**.   

---

## ☁️ 2. Replicar as VMs

Com o appliance configurado e a descoberta concluída:   

1. No portal Azure, vá ao **projeto Azure Migrate > Migração e Modernização**.  
2. Selecione **Replicar**.  
3. Em *Origem*, selecione **VMware vSphere** e o appliance configurado.  
4. Selecione as **VMs que deseja migrar**.  
   - Pode escolher importar **configurações de avaliação**, se disponível.  
5. Configure:  
   - **Assinatura**, **Região**, **Conta de armazenamento**.  
   - **Rede Virtual** destino (VNet/sub-rede).  
   - **Opções de disponibilidade** (Zonas / Availability Sets).  
   - **Criptografia de disco**.  
   - **Benefício Híbrido do Azure** (se aplicável). :contentReference[oaicite:10]{index=10}

> Observação: após iniciar a primeira replicação de uma VM, não é possível alterar a região ou conta de armazenamento. :contentReference[oaicite:11]{index=11}

---

## 📈 3. Acompanhar e Monitorar

Monitore a replicação no portal Azure: :contentReference[oaicite:12]{index=12}

- Acompanhe o status geral nas **notificações**.  
- Veja detalhes de replicação por VM em **Migração e modernização > Replicação**.  
- Use PowerShell ou Azure Cloud Shell para exibir o status e tempo restante:  
  ```powershell
  Get-AzMigrateServerMigrationStatus -ProjectName "<nome-do-projeto>" -ResourceGroupName "<grupo-de-recursos>" -MachineName "<nome-da-VM>"