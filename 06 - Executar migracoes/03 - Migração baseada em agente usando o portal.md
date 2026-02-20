# Migrar VMs VMware vSphere para Azure (Baseado em Agente)

Este tutorial mostra como migrar máquinas virtuais **VMware vSphere** para o **Azure** usando a ferramenta **Migração e modernização** com **migração baseada em agente** — indicada quando a migração sem agente não é possível ou suportada. :contentReference[oaicite:0]{index=0}

---

## 🎯 Objetivo

Você aprenderá como: :contentReference[oaicite:1]{index=1}

1. Preparar o **Azure** para migração baseada em agente.  
2. Preparar o ambiente VMware e contas necessárias.  
3. Configurar o **dispositivo de replicação**.  
4. Replicar as VMs.  
5. Fazer uma **migração de teste**.  
6. Executar a **migração final** para o Azure. :contentReference[oaicite:2]{index=2}

---

## 🧰 1. Pré-requisitos

Antes de começar: :contentReference[oaicite:3]{index=3}

- Revise a **arquitetura de migração baseada em agente** para VMware. :contentReference[oaicite:4]{index=4}  
- Permissões no Azure:
  - Permissão de **Colaborador (Contributor)** ou **Proprietário (Owner)**.  
  - Função de **Virtual Machine Contributor** para criar VMs e gravar em discos gerenciados. :contentReference[oaicite:5]{index=5}  
- Configurar **Rede Virtual (VNet)** no Azure onde VMs migradas serão ingressadas. :contentReference[oaicite:6]{index=6}  
- Preparar contas:
  - Conta no **vCenter Server** para permitir descoberta de VMs.  
  - Conta com permissões para instalar o **Mobility Service (agente)** nas VMs. :contentReference[oaicite:7]{index=7}

---

## ☁️ 2. Preparar o Azure

1. **Criar um projeto Azure Migrate** se ainda não existir.  
2. Verificar que sua conta Azure tem permissões para:
   - Criar VMs e discos no Azure.  
   - Acessar a população de recursos para criar grupos de recursos e redes.  
3. Configurar a **VNet/Sub-rede de destino** onde as VMs serão conectadas após migração. :contentReference[oaicite:8]{index=8}

---

## 🖥️ 3. Preparar o Ambiente VMware

1. Configure uma conta no **vCenter Server** com permissões suficientes para:
   - Descobrir VMs.  
   - Operações de inventário e gerenciamento de rede. :contentReference[oaicite:9]{index=9}  
2. Prepare uma conta que permita instalar o **Mobility Service** dentro de cada VM que será migrada.  
   - No Windows: conta com privilégios de administrador local/domínio.  
   - No Linux: conta de **root**. :contentReference[oaicite:10]{index=10}

---

## 🏗️ 4. Configurar o Dispositivo de Replicação

1. No projeto Azure Migrate, selecione **Servidores, bancos de dados e apps web > Migração e modernização > Descobrir**.  
2. Em *Como você deseja migrar?*, escolha **Replicação baseada em agente** e confirme a região.  
3. Crie os **recursos necessários** (Recovery Services vault).  
4. Baixe o **modelo OVA do dispositivo de replicação** e **importe no vSphere**.  
5. Inicie a VM do dispositivo e **registre-a no projeto Azure Migrate**.  
6. Configure NICs para:
   - Comunicação com o ambiente local (descoberta e push de agente).  
   - Conexão com o Azure. :contentReference[oaicite:11]{index=11}

---

## 🔄 5. Replicar VMs

1. No Azure Migrate, vá em **Replicar** sob *Migração e modernização*.  
2. Selecione:
   - Ambiente de origem (**VMware vSphere**).  
   - Dispositivo de replicação configurado.  
3. Insira:
   - Servidor vCenter/ESXi e credenciais de descoberta.  
   - Credenciais para instalação **push** do agente (Mobility Service).  
4. Selecione as **VMs a replicar**.  
5. Configure opções de destino:
   - **Assinatura**, **grupo de recursos** e **região**.  
   - **Redes** (VNet/sub-rede).  
   - **Disponibilidade** (Zonas/Availability Sets).  
   - **Criptografia de disco** e **Benefício Híbrido do Azure**.  
6. Reveja e inicie a **replicação inicial**. :contentReference[oaicite:12]{index=12}

---

## 🧪 6. Migração de Teste

Antes da migração final: :contentReference[oaicite:13]{index=13}

1. Selecione a VM replicada e clique em **Migração de teste**.  
2. Escolha uma **VNet de teste** (não produção).  
3. Monitore o progresso no portal Azure.  
4. Após a conclusão bem-sucedida, limpe os recursos de teste. :contentReference[oaicite:14]{index=14}

---

## 🚀 7. Migração Completa

1. Selecione a VM replicada novamente.  
2. Inicie **Migrar**.  
3. Opção: **Desligar VM local antes da migração** (para consistência de dados).  
4. Acompanhe a migração até a conclusão. :contentReference[oaicite:15]{index=15}

---

## 🧹 8. Pós-Migração

Após a migração: :contentReference[oaicite:16]{index=16}

- **Parar replicação** da VM local no Azure Migrate.  
- Verificar **ativação do Windows** e ajustar configurações de rede.  
- Atualizar nomes, conexões e validar serviços.  
- Implementar **backup** e monitoração no Azure. :contentReference[oaicite:17]{index=17}

---

## 📌 Notas Importantes

- O tutorial descreve o **caminho mais simples** — não cobre todas as opções avançadas. :contentReference[oaicite:18]{index=18}  
- Use a **experiência simplificada** (recomendada) em vez da clássica para migrações baseadas em agente; ela melhora compatibilidade e simplifica passos. :contentReference[oaicite:19]{index=19}

---

*Referências:*  
Documentação oficial do Azure Migrate – tutorial de migração baseada em agente. :contentReference[oaicite:20]{index=20}
