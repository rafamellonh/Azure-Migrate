# GUIA COMPLETO E DETALHADO --- MIGRAR VMs DO VMWARE PARA AZURE

------------------------------------------------------------------------

# FASE 1 --- PLANEJAMENTO TÉCNICO

## 1.1 Levantamento Completo do Ambiente VMware

Para cada VM, documente:

-   Nome
-   Sistema operacional (versão exata)
-   vCPU
-   RAM
-   Tamanho de cada disco
-   Tipo de storage
-   IP atual
-   VLAN
-   Gateway
-   DNS configurado
-   Aplicação instalada
-   Dependências
-   Criticidade
-   Janela de manutenção

⚠️ Dependências mal mapeadas são a principal causa de falhas.

------------------------------------------------------------------------

## 1.2 Validar Compatibilidade

Verifique:

-   SO suportado no Azure
-   Disco do SO não é dinâmico
-   Não há discos RDM
-   Não há discos independentes
-   `/boot` no mesmo disco (Linux)
-   Não usa NVMe

------------------------------------------------------------------------

# FASE 2 --- PLANEJAMENTO DE REDE

## 2.1 Conectividade

Definir:

-   VPN Site-to-Site
-   ExpressRoute
-   Conectividade temporária

## 2.2 Estrutura Azure

Planejar:

-   VNet principal
-   Subnets (Web/App/DB)
-   NSGs
-   Route Tables
-   Firewall Azure
-   Bastion
-   Private DNS

## 2.3 Estratégia de IP

-   Manter IP?
-   Novo IP?
-   Atualização DNS?
-   Reduzir TTL 48h antes do cutover

------------------------------------------------------------------------

# FASE 3 --- CRIAR PROJETO AZURE MIGRATE

1.  Portal Azure
2.  Azure Migrate
3.  Criar projeto (Subscription, RG, Região)

------------------------------------------------------------------------

# FASE 4 --- INSTALAR APPLIANCE

## 4.1 Deploy OVA

1.  Deploy OVF Template no vCenter
2.  Escolher datastore
3.  Configurar rede
4.  IP fixo recomendado

## 4.2 Requisitos

-   8 vCPU
-   16GB RAM
-   80GB disco
-   Porta 443 liberada

## 4.3 Registrar

1.  Acessar https://IP-do-appliance
2.  Login Azure
3.  Associar ao projeto

------------------------------------------------------------------------

# FASE 5 --- DESCOBERTA

O appliance:

-   Conecta ao vCenter
-   Descobre VMs
-   Coleta CPU, RAM, Disco, NIC
-   Coleta performance (se habilitado)

Aguardar alguns dias para coleta ideal.

------------------------------------------------------------------------

# FASE 6 --- AVALIAÇÃO

Criar avaliação Performance-Based:

-   Região destino
-   Tipo de disco
-   Percentil (95%)
-   Fator conforto (1.2)
-   Hybrid Benefit

Verificar:

-   Ready for Azure
-   VM Size recomendada
-   Custo estimado
-   Problemas detectados

------------------------------------------------------------------------

# FASE 7 --- INICIALIZAR INFRAESTRUTURA

``` powershell
Initialize-AzMigrateReplicationInfrastructure `
  -ResourceGroupName "RG" `
  -ProjectName "Projeto" `
  -Scenario agentlessVMware `
  -TargetRegion "eastus"
```

⚠️ Região não pode ser alterada depois.

------------------------------------------------------------------------

# FASE 8 --- INICIAR REPLICAÇÃO

1.  Azure Migrate → Migração e modernização
2.  Replicar
3.  Selecionar appliance e VMs
4.  Configurar destino:
    -   RG
    -   Região
    -   VNet
    -   Subnet
    -   VM Size
    -   Disk type
    -   Availability Zone
    -   Hybrid Benefit

Processo: 1. Snapshot 2. Initial replication 3. Delta replication

------------------------------------------------------------------------

# FASE 9 --- MONITORAMENTO

Verificar:

-   Initial sync %
-   Replication health
-   RPO
-   Erros

------------------------------------------------------------------------

# FASE 10 --- MIGRAÇÃO DE TESTE

1.  Selecionar VM
2.  Migrar teste
3.  Escolher VNet isolada

Validar:

-   Boot
-   Aplicação
-   Logs
-   Conectividade

Remover VM de teste após validação.

------------------------------------------------------------------------

# FASE 11 --- CUTOVER FINAL

1.  Avisar stakeholders
2.  Congelar mudanças
3.  Desligar VM on-prem
4.  Clicar em Migrar
5.  Validar VM Azure
6.  Atualizar DNS
7.  Liberar usuários

------------------------------------------------------------------------

# FASE 12 --- PÓS-MIGRAÇÃO

## Segurança

-   Defender for Cloud
-   JIT VM access
-   Disk encryption
-   NSGs restritivos

## Backup

-   Azure Backup

## Monitoramento

-   Log Analytics
-   Azure Monitor

## Otimização

Após 30 dias:

-   Reduzir SKU
-   Aplicar Reserved Instance
-   Ajustar tipo de disco

------------------------------------------------------------------------

# RISCOS COMUNS

-   Falta de mapeamento de dependências
-   Rede mal planejada
-   Não reduzir TTL DNS
-   Oversizing
-   Não desligar VM antes do cutover

------------------------------------------------------------------------

# RESUMO

1.  Planejamento
2.  Descoberta
3.  Avaliação
4.  Planejamento de rede
5.  Replicação
6.  Teste
7.  Cutover
8.  Hardening
9.  Otimização

------------------------------------------------------------------------
