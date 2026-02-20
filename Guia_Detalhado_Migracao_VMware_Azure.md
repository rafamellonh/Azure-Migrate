# Guia passo a passo detalhado --- Migrar VMs VMware → Azure

------------------------------------------------------------------------

# Fase 0 --- Planejamento e governança (obrigatório)

## Defina o escopo do projeto

-   Lista de VMs candidatas (nome, OS, vCPU, RAM, discos, apps críticos,
    owner).
-   Dependências (aplicações dependentes, bancos, LDAP, storage
    compartilhado).
-   Criticidade de negócio --- categorize (prod, preprod, dev).
-   Políticas de segurança e compliance que precisam ser mantidas.

## Defina a arquitetura alvo no Azure

-   Região(s) alvo.
-   Sub-redes, NSGs, peering/VPN/ExpressRoute, Azure Firewall, Azure
    Bastion se necessário.
-   Política de identidade: AAD, role assignments, managed identities.
-   Landing zones / RG naming, tags, naming conventions.
-   Estratégia de alta disponibilidade: Availability Zones vs
    Availability Sets.

## Defina política de custo e licenciamento

-   Use Azure Hybrid Benefit se aplicável.
-   Decida uso de Reserved Instances / Savings Plan.
-   Orçamento e responsáveis por aprovação.

## Defina critérios de sucesso e rollback

-   Checklists de validação pós-migração.
-   Procedimento de rollback (o que será feito se cutover falhar).
-   Comunicados para stakeholders.

------------------------------------------------------------------------

# Fase 1 --- Descoberta e inventário (importante)

## Recolha informações no vSphere

-   Exportar inventário: VM names, guest OS, CPUs, RAM, vDisk sizes,
    NICs, guest tools, snapshots, storage usage.
-   Coletar IPs, DNS, dependências.

## Habilitar / verificar performance metrics

-   Garantir coleta de CPU, memória, IOPS, throughput.
-   Aguardar alguns dias para melhor right-sizing.

## Verifique requisitos operacionais das VMs

-   Confirmar que /boot está no mesmo disco (Linux).
-   Remover discos independentes ou RDMs.
-   Identificar sistemas fora de suporte.

------------------------------------------------------------------------

# Fase 2 --- Azure Migrate: projeto e avaliação

## Criar projeto Azure Migrate

Portal Azure → Azure Migrate → Criar projeto.

## Implantar appliance Azure Migrate no vCenter

-   Baixar OVA.
-   Deploy OVF Template.
-   IP estática e DNS válido.
-   Liberar saída HTTPS (443).
-   Registrar appliance no projeto.

## Executar descoberta

-   Apontar para vCenter.
-   Validar VMs listadas e métricas coletadas.

## Criar avaliações (Assessments)

-   Criar grupos lógicos.
-   Criar avaliação Performance-Based:
    -   Percentil (95%)
    -   Fator conforto (1.2)
    -   Região e tipo de disco
-   Criar avaliação As-Is (opcional).
-   Revisar relatórios de prontidão e custo.

## Avaliar resultados

-   Corrigir VMs Not Ready.
-   Identificar workloads que devem ir para PaaS.

------------------------------------------------------------------------

# Fase 3 --- Planejamento de execução (ondas)

## Criar ondas

-   Agrupar por dependência e criticidade.
-   Definir data, owner, rede destino.

## Checklist pre-cutover

-   Rede Azure pronta.
-   Roles configuradas.
-   Backups validados.
-   Janela aprovada.

------------------------------------------------------------------------

# Fase 4 --- Preparação do ambiente Azure

## Infraestrutura

-   Criar RGs, VNets, subnets, NSGs, route tables.
-   Criar Storage accounts (se necessário).
-   Criar Key Vault, Log Analytics e Recovery Services vault.

## Permissions

-   Atribuir roles necessárias.

## Networking

-   Validar VPN/ExpressRoute.
-   Planejar IP addressing e DNS.

------------------------------------------------------------------------

# Fase 5 --- Preparação do appliance e replicação

## Inicializar infraestrutura (PowerShell)

``` powershell
Initialize-AzMigrateReplicationInfrastructure `
  -ResourceGroupName "MeuRG" `
  -ProjectName "MeuProjeto" `
  -Scenario agentlessVMware `
  -TargetRegion "eastus"
```

⚠ Região não alterável após execução.

## Validar appliance

-   Confirmar status saudável no portal.
-   Revisar logs.

------------------------------------------------------------------------

# Fase 6 --- Replicação inicial (agentless)

## Configurar replicação

Portal → Azure Migrate → Migração e modernização → Replicar.

Configurar:

-   Subscription e RG
-   Região
-   VNet/Subnet
-   VM Size
-   Disk Type
-   Availability options
-   Hybrid Benefit

## Fluxo técnico

-   Snapshot
-   Initial replication
-   Delta replication (CBT)

## Limitações

-   Não alterar região após primeira replicação.
-   Limite recomendado por appliance (300--500 VMs).

------------------------------------------------------------------------

# Fase 7 --- Monitoramento e troubleshooting

## Monitoramento

Portal → Migração e modernização → Replicação.

Verificar:

-   Initial sync
-   Delta replication
-   RPO/RTO
-   Throughput

## Problemas comuns

-   Authentication/network errors → revisar firewall/proxy.
-   Snapshot failures → revisar permissões e datastore.
-   Initial sync lento → verificar banda.

------------------------------------------------------------------------

# Fase 8 --- Migração de teste

-   Selecionar VM → Migração de teste.
-   Usar VNet isolada.
-   Validar:
    -   Boot
    -   Aplicações
    -   DNS
    -   Conectividade
-   Remover instância de teste após validação.

------------------------------------------------------------------------

# Fase 9 --- Cutover final

## Preparação

-   Validar janela.
-   Parar serviços críticos.
-   Comunicar stakeholders.

## Executar

Portal → Migrate

PowerShell:

``` powershell
Start-AzMigrateCommitMigration `
  -ProjectName "MeuProjeto" `
  -ResourceGroupName "MeuRG" `
  -MachineName "VM01"
```

## Validar

-   VM criada corretamente
-   Serviços funcionando
-   Firewall/NSG corretos

------------------------------------------------------------------------

# Fase 10 --- Pós-migração

## Finalizar

-   Concluir migração no portal.
-   Atualizar inventário.

## Segurança

-   Habilitar Defender for Cloud.
-   Revisar NSGs e Azure Policy.

## Backup e DR

-   Registrar no Azure Backup.
-   Configurar Site Recovery se necessário.

## Monitoramento

-   Habilitar Log Analytics.
-   Criar alertas.

## Otimização de custo

-   Revisar sizing após 30 dias.
-   Avaliar Reserved Instances.
-   Ajustar tipo de disco.

------------------------------------------------------------------------

# Boas práticas

-   Fazer dry-run com poucas VMs.
-   Testar rollback.
-   Usar IaC (ARM/Terraform).
-   Manter runbook atualizado.
-   Verificar sincronização NTP.

------------------------------------------------------------------------

# Comandos úteis

## Login

``` powershell
Connect-AzAccount
Set-AzContext -SubscriptionId "<SUB_ID>"
```

## Inicializar infra

``` powershell
Initialize-AzMigrateReplicationInfrastructure -ResourceGroupName "MeuRG" -ProjectName "MeuProjeto" -Scenario agentlessVMware -TargetRegion "eastus"
```

## Iniciar replicação

``` powershell
Start-AzMigrateServerReplication -ProjectName "MeuProjeto" -ResourceGroupName "MeuRG" -MachineId $Machine.Id -TargetVMSize "Standard_D4s_v3" -TargetDiskType "Premium_LRS"
```

## Test migration

``` powershell
Start-AzMigrateTestMigration -ProjectName "MeuProjeto" -MachineName "VM01" -TestVirtualNetworkId "<VNetID>"
```

## Commit migration

``` powershell
Start-AzMigrateCommitMigration -ProjectName "MeuProjeto" -ResourceGroupName "MeuRG" -MachineName "VM01"
```

------------------------------------------------------------------------

# Checklist Final

-   Inventário completo
-   Projeto Azure Migrate criado
-   Avaliações revisadas
-   Waves planejadas
-   Infra Azure pronta
-   Replicação OK
-   Teste validado
-   Cutover executado
-   Migração concluída
-   Backup e monitoramento ativos
-   Documentação atualizada

------------------------------------------------------------------------

# Riscos e mitigação

-   Rede insuficiente → testar throughput
-   Snapshots falhando → revisar permissões
-   SO incompatível → usar agent-based
-   Licenciamento incorreto → validar Hybrid Benefit
-   Dados divergentes → desligar origem antes do cutover
