# 🔍 Azure Migrate – Descoberta Detalhada de VMs VMware

Este documento detalha o processo completo de **descoberta de máquinas virtuais VMware usando Azure Migrate**, etapa fundamental antes da avaliação e migração para o Azure.

---

# 🎯 Objetivo da Descoberta

A descoberta serve para:

- Identificar todas as VMs no ambiente VMware
- Coletar inventário técnico (CPU, memória, disco, SO)
- Coletar dados de desempenho ao longo do tempo
- Identificar dependências entre servidores
- Preparar dados para avaliação de tamanho e custo no Azure

Sem essa etapa, não há dimensionamento confiável.

---

# 🏗 Arquitetura Envolvida

Componentes principais:

1. **Azure Migrate (Portal Azure)**
   - Onde você visualiza inventário, avaliações e relatórios.

2. **Azure Migrate Appliance**
   - VM Linux implantada no VMware.
   - Faz coleta e envio de dados.

3. **VMware vCenter**
   - Fonte de inventário das VMs.

Fluxo:

VMware → Appliance → Azure Migrate (Azure)

---

# ⚙️ Pré-Requisitos Técnicos

## 📌 No Azure

- Projeto criado no Azure Migrate
- Permissões RBAC adequadas
- Resource providers registrados:
  - Microsoft.Migrate
  - Microsoft.Compute
  - Microsoft.Storage

---

## 📌 No VMware

- vCenter acessível
- Conta com permissões mínimas:
  - Leitura de inventário
  - Acesso a dados de performance
- Permissão para criar snapshots (se for usar migração agentless depois)

---

## 📌 Rede

O appliance precisa de:

- Saída HTTPS (porta 443) para Azure
- Conectividade com vCenter
- DNS funcionando corretamente
- Ou Private Endpoint configurado (ambientes restritos)

---

# 🚀 Etapas Detalhadas

---

# 🪄 ETAPA 1 – Criar e Baixar o Appliance

1. No Azure Portal:
   Azure Migrate → Descobrir servidores → VMware

2. Selecione:
   - Tipo de descoberta: Agentless
   - Gere a chave de registro do appliance

3. Baixe o arquivo OVA fornecido pelo portal

---

# 🖥 ETAPA 2 – Implantar o Appliance no VMware

No vCenter:

1. Deploy OVF Template
2. Selecione o arquivo OVA
3. Escolha:
   - Datastore
   - Network
4. Ligue a VM

---

# 🔧 ETAPA 3 – Configurar o Appliance

Acesse via navegador:

https://<IP-do-appliance>:44368

Configuração inclui:

- Verificação de conectividade
- Inserção da chave de registro
- Registro no projeto Azure Migrate

Após isso, o appliance aparece no portal como "Conectado".

---

# 🔗 ETAPA 4 – Conectar ao vCenter

Dentro do appliance:

1. Adicionar servidor vCenter
2. Informar:
   - FQDN ou IP do vCenter
   - Credenciais
3. Validar conexão

Se tudo estiver correto, a descoberta começa.

---

# 📊 ETAPA 5 – Coleta de Inventário

Inicialmente são coletados:

- Nome da VM
- Sistema Operacional
- vCPU configuradas
- Memória alocada
- Discos anexados
- NICs
- Cluster e datastore

Esses dados aparecem no Azure Portal em algumas horas.

---

# 📈 ETAPA 6 – Coleta de Performance

O appliance coleta métricas por padrão por:

- 7 dias (mínimo recomendado)
- Pode coletar até 30 dias ou mais para maior precisão

Coleta:

- Uso médio e pico de CPU
- Uso de memória
- IOPS de disco
- Throughput de rede

Esses dados permitem:

✔️ Dimensionamento correto no Azure  
✔️ Evitar superdimensionamento  
✔️ Estimar custo real  

---

# 🔎 ETAPA 7 – Mapear Dependências (Opcional)

Se habilitar análise de dependências:

- Instala agente (opcional)
- Mapeia conexões entre servidores
- Ajuda a migrar aplicações completas juntas

---

# 📊 O Que Você Verá no Portal

Após a descoberta:

Azure Migrate → Servidores

Você verá:

- Lista de VMs
- Status de descoberta
- Sistema operacional detectado
- Alertas de compatibilidade
- Dados de performance

---

# 🧠 Agentless vs Com Agente

| Critério | Agentless |
|----------|-----------|
| Instalação na VM | ❌ Não |
| Impacto | Baixo |
| Dados coletados | Inventário + performance |
| Recomendado para VMware | ✅ Sim |

---

# 🔐 Segurança e Boas Práticas

- Use conta com menor privilégio no vCenter
- Monitore logs do appliance
- Use Private Endpoint se ambiente restrito
- Garanta que appliance esteja sempre ligado

---

# ⚠️ Problemas Comuns

1. VM não aparece
   → Permissão insuficiente no vCenter

2. Performance não coleta
   → Appliance desligado ou firewall bloqueando

3. Erro de registro
   → Tenant ID ou chave incorreta

---

# 🎯 Resultado Final da Descoberta

Após concluir:

✔️ Ambiente completamente inventariado  
✔️ Dados reais de uso coletados  
✔️ Pronto para criar avaliação  
✔️ Pronto para estimar custos  
✔️ Base pronta para migração  

---

# 🏁 Conclusão

A descoberta VMware no Azure Migrate:

- É a base do planejamento
- Permite decisões baseadas em dados reais
- Reduz risco na migração
- Evita superdimensionamento no Azure

Nunca pule essa etapa.

