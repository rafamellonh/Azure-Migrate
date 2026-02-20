# Azure Migrate -- Guia Completo VMware vSphere → Azure

Este documento consolida avaliação, migração (agentless, agent-based e
PowerShell), right-sizing, estimativa de custos, planejamento por ondas
e boas práticas.

------------------------------------------------------------------------

# 1️⃣ Visão Geral da Arquitetura

## Componentes

-   Azure Migrate Project
-   Appliance Azure Migrate (OVA)
-   Migração e Modernização
-   Recovery Services Vault
-   Managed Disks
-   Azure Virtual Network

## Métodos de Migração

  Método        Quando usar
  ------------- ---------------------------------------------------
  Agentless     VMware compatível com snapshots/CBT (Recomendado)
  Agent-Based   Quando agentless não é suportado
  PowerShell    Automação e escala

------------------------------------------------------------------------

# 2️⃣ Avaliação de VMs VMware

## Tipos

### As-Is

Baseado apenas na configuração atual.

### Performance-Based (Recomendado)

Baseado em: - CPU - Memória - IOPS - Throughput

## Configurações

-   Região de destino
-   Tipo de armazenamento
-   Percentil (ex: 95%)
-   Fator de conforto
-   Azure Hybrid Benefit
-   Reservas / Savings Plan

------------------------------------------------------------------------

# 3️⃣ Migração Agentless (Portal)

## Etapas

1.  Criar Projeto Azure Migrate
2.  Implantar Appliance (OVA)
3.  Descoberta automática
4.  Configurar Replicação
5.  Teste de migração
6.  Cutover final

------------------------------------------------------------------------

# 4️⃣ Migração Baseada em Agente

## Quando usar

-   Agentless não suportado
-   Servidores físicos
-   Configurações especiais de disco

Processo: 1. Criar Recovery Services Vault 2. Deploy appliance 3.
Instalar Mobility Service 4. Replicação 5. Teste 6. Cutover

------------------------------------------------------------------------

# 5️⃣ Migração via PowerShell

## Conectar

``` powershell
Connect-AzAccount
Set-AzContext -SubscriptionId "<SUB_ID>"
```

## Inicializar Infraestrutura

``` powershell
Initialize-AzMigrateReplicationInfrastructure `
  -ResourceGroupName "MeuRG" `
  -ProjectName "MeuProjeto" `
  -Scenario agentlessVMware `
  -TargetRegion "eastus"
```

## Iniciar Replicação

``` powershell
Start-AzMigrateServerReplication `
  -ProjectName "MeuProjeto" `
  -ResourceGroupName "MeuRG" `
  -MachineId $Machine.Id `
  -TargetVMSize "Standard_D4s_v3" `
  -TargetDiskType "Premium_LRS"
```

## Teste de Migração

``` powershell
Start-AzMigrateTestMigration `
  -ProjectName "MeuProjeto" `
  -MachineName "VM01" `
  -TestVirtualNetworkId "<VNetID>"
```

## Commit Final

``` powershell
Start-AzMigrateCommitMigration `
  -ProjectName "MeuProjeto" `
  -MachineName "VM01"
```

------------------------------------------------------------------------

# 6️⃣ Right-Sizing

  Método              Base
  ------------------- --------------------
  As-Is               Configuração atual
  Performance-Based   Dados coletados

Ajustes: - Percentil - Fator de conforto - Histórico analisado

------------------------------------------------------------------------

# 7️⃣ Estimativa de Custos

Influenciada por: - Região - VM SKU - Tipo de disco - Horas/mês (730
padrão) - Hybrid Benefit - Reservas

------------------------------------------------------------------------

# 8️⃣ Planejamento por Ondas

Permite agrupar migração por fases.

Status: - Not Started - On Track - At Risk - Completed

------------------------------------------------------------------------

# 9️⃣ Matriz de Suporte VMware

## Suportado

-   vCenter 6.5+
-   ESXi compatível

## Não suportado

-   NVMe
-   RDM
-   IPv6
-   Discos independentes

------------------------------------------------------------------------

# 🔟 Pós-Migração

## Segurança

-   Defender for Cloud
-   NSGs

## Backup

-   Azure Backup

## Alta Disponibilidade

-   Availability Zones
-   Site Recovery

## Custos

-   Revisar tamanho após 30 dias
-   Aplicar Reserved Instances

------------------------------------------------------------------------

# Conclusão

Azure Migrate oferece avaliação, planejamento, migração e otimização
para workloads VMware com governança enterprise.
