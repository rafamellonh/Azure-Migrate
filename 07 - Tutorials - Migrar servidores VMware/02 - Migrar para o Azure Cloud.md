7. Registre no Azure usando credenciais da assinatura.

---

# 🔍 Etapa 3 – Descoberta das VMs

O appliance:

- Conecta-se ao vCenter
- Descobre VMs automaticamente
- Coleta:
- CPU
- Memória
- Discos
- NICs
- Performance (se habilitado)

A coleta pode levar horas dependendo do ambiente.

---

# 🔁 Etapa 4 – Iniciar Replicação

No portal Azure:

1. Vá em:
> Migração e modernização > Replicar

2. Configure:
- Origem: VMware vSphere
- Appliance
- vCenter

3. Selecione VMs (até 10 por vez).

---

## 🔧 Configurações de Destino

Você deverá definir:

### Infraestrutura
- Assinatura
- Grupo de recursos
- Região (não pode ser alterada após replicação inicial)

### Rede
- VNet
- Sub-rede
- IP estático ou dinâmico

### Disponibilidade
- Zona de disponibilidade
- Availability Set

### Armazenamento
- Tipo de disco:
- Premium SSD
- Standard SSD
- Standard HDD
- Criptografia opcional

### Licenciamento
- Azure Hybrid Benefit (Windows / Linux)

---

# 🔄 Processo de Replicação

## Fase 1 – Replicação Inicial
- Snapshot da VM
- Upload completo do disco para Azure

## Fase 2 – Replicação Delta
- Apenas blocos alterados são enviados
- Baseado em Change Block Tracking (CBT)

---

# 📊 Monitoramento

No portal:

- Migração e modernização > Replicação
- Status:
- Initial sync
- Delta replication
- Protected

Você pode monitorar:
- Percentual concluído
- Taxa de transferência
- Alertas de falha

---

# 🧪 Etapa 5 – Migração de Teste

Fortemente recomendada antes do cutover.

## Procedimento:

1. Selecione VM replicada.
2. Clique em **Migração de teste**.
3. Escolha VNet isolada.
4. Valide:
- Boot
- Serviços
- Aplicações
- Conectividade

Após teste:
- Limpe recursos de teste.

---

# 🚀 Etapa 6 – Migração Final (Cutover)

1. Selecione VM replicada.
2. Clique em **Migrar**.
3. Recomenda-se:
- Desligar VM local antes da migração
4. O Azure:
- Finaliza replicação delta
- Cria Managed Disks
- Provisiona VM

Tempo depende do tamanho do disco.

---

# 🧹 Etapa 7 – Pós-Migração

Após validação:

- Clique em **Concluir migração**
- Interrompa replicação
- Desative VM local
- Atualize DNS se necessário

---

# 🔐 Boas Práticas Pós-Migração

## Segurança
- Ativar Microsoft Defender for Cloud
- Aplicar NSGs adequados

## Backup
- Habilitar Azure Backup

## Alta Disponibilidade
- Configurar Availability Zones
- Configurar Site Recovery

## Custos
- Revisar tamanho da VM
- Ajustar discos
- Avaliar uso de Reserved Instances

---

# 📈 Otimização Pós-Migração

Após algumas semanas:

- Reavaliar consumo de CPU
- Ajustar SKU da VM
- Mover discos para tipo mais adequado
- Aplicar autoscaling se aplicável

---

# ⚠️ Limitações Importantes

- Não suporta:
- Discos NVMe
- IPv6
- RDM
- iSCSI volumes
- Região não pode ser alterada após replicação iniciar.
- Até 300 VMs replicando simultaneamente por appliance.

---

# 🏁 Conclusão

A migração agentless via Azure Migrate:

✔ Reduz complexidade operacional  
✔ Evita instalação de agentes  
✔ Permite testes antes do corte  
✔ Minimiza downtime  
✔ Fornece integração nativa com Azure  

É o método recomendado para ambientes VMware compatíveis.

---
