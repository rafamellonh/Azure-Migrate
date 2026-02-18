# 🧠 Mapa mental — Implantação do Azure Migrate para VMware (baseado no repo Azure-Migrate)

## 🌟 Visão geral (repo)
- Estrutura do repositório
  - 01 - QuickStarts :contentReference[oaicite:1]{index=1}
  - 02 - Conceitos Principais :contentReference[oaicite:2]{index=2}
  - 03 - Detectar inventario :contentReference[oaicite:3]{index=3}
- Fases do Azure Migrate (visão macro)
  - Descoberta → Avaliação → Migração :contentReference[oaicite:4]{index=4}

---

## 0) ✅ Pré-requisitos (antes de começar)
- Azure
  - Assinatura ativa
  - Permissões (RBAC) no resource group do projeto
  - Provedores de recursos registrados (ex.: Microsoft.Migrate, Compute, Storage) *(inferido)*
- VMware
  - vCenter acessível via rede
  - Conta no vCenter com permissões mínimas (inventário/performance; e snapshot se for usar migração agentless) *(inferido)*
- Rede
  - Appliance precisa:
    - Acessar vCenter (porta e DNS internos)
    - Sair para Azure via HTTPS 443 (ou Private Endpoint, se o ambiente exigir) *(inferido)*
- Segurança
  - Usar “least privilege” (contas e RBAC mínimos) *(inferido, mas alinhado ao tema do repo e docs)*

---

## 1) 🧭 QuickStart (01 - QuickStarts) — “ligar o ambiente”
- 1.1 Criar o projeto no Azure Migrate *(inferido)*
  - Definir assinatura + resource group
  - Definir “geografia” do projeto (metadados)
- 1.2 Escolher o cenário
  - VMware (descoberta e avaliação)
  - Preparar para migração “lift-and-shift” (VMs para Azure) *(inferido)*
- 1.3 Definir estratégia por ondas *(inferido)*
  - Piloto → 1ª onda → ondas seguintes
  - Critérios: criticidade, dependências, janelas

---

## 2) 📚 Conceitos principais (02 - Conceitos Principais)
- 2.1 Azure Migrate “hub”
  - Centraliza descoberta, avaliação e migração :contentReference[oaicite:5]{index=5}
- 2.2 Appliance
  - VM dedicada (no VMware) para coletar inventário/performance e enviar ao Azure *(inferido)*
- 2.3 Descoberta vs Avaliação vs Migração
  - Descoberta: inventário + (opcional) dependências :contentReference[oaicite:6]{index=6}
  - Avaliação: sizing + custo :contentReference[oaicite:7]{index=7}
  - Migração: replicação + teste + cutover :contentReference[oaicite:8]{index=8}
- 2.4 Modelos de migração *(inferido)*
  - Agentless (sem agente nas VMs)
  - Com agente (para dependências mais profundas, quando necessário)

---

## 3) 🔎 Detectar inventário (03 - Detectar inventario) — VMware Discovery
- 3.1 Implantar o Appliance no VMware *(inferido)*
  - Baixar OVA / template do Azure Migrate
  - Deploy no vCenter (cluster/datastore/rede)
  - Definir IP/DNS/NTP (muito importante)
- 3.2 Registrar o Appliance no Azure Migrate *(inferido)*
  - Associar ao projeto do Azure Migrate
  - Garantir autenticação (conta ou app do Entra, se exigido)
- 3.3 Conectar o Appliance ao vCenter *(inferido)*
  - Informar FQDN/IP do vCenter + credenciais
  - Validar conectividade
- 3.4 Executar Descoberta
  - Coletar:
    - Nome, SO, CPU, memória, disco, NICs
    - Métricas de performance (janela de coleta) *(inferido)*
- 3.5 Validar resultados
  - Conferir se todas as VMs aparecem
  - Verificar erros (permissão, DNS, conectividade)
  - Ajustar e rodar novamente se preciso

---

## 4) 📊 Avaliação (Assess) — sizing e custo
- 4.1 Criar grupos (por aplicação/onda) *(inferido)*
- 4.2 Rodar assessment
  - Dimensionamento recomendado (VM size)
  - Estimativa de custo mensal
  - Dependências/alertas (se habilitado) *(inferido)*
- 4.3 Decisão
  - Lift-and-shift (VM no Azure)
  - Replatform/modernizar (se fizer sentido) :contentReference[oaicite:9]{index=9}

---

## 5) 🚚 Migração (Migrate) — replicar, testar, cortar
- 5.1 Preparar destino no Azure *(inferido)*
  - VNet/Subnet
  - NSG/Firewall
  - Regras de rota/DNS
- 5.2 Habilitar replicação para as VMs selecionadas *(inferido)*
- 5.3 Test migration (teste)
  - Validar boot, rede, apps, portas, dependências
- 5.4 Cutover (migração final)
  - Janela de parada
  - Sincronização final
  - Ligar VM no Azure e validar
- 5.5 Pós-migração *(inferido)*
  - Ajustes de performance
  - Backup/monitoramento (Azure Backup/Monitor)
  - Descomissionar no VMware (quando aprovado)

---

## 6) 🔐 Segurança (transversal)
- Menor privilégio (RBAC + vCenter) *(inferido)*
- Preferir rede privada (Private Endpoints) quando exigido *(inferido)*
- Logs e auditoria
  - Ativar logs/monitoramento para rastrear atividades *(inferido)*

---

## ✅ Checklist rápido (para você “seguir o mapa”)
- [ ] Criar projeto Azure Migrate
- [ ] Preparar RBAC no resource group
- [ ] Confirmar acesso ao vCenter e rede
- [ ] Deploy do Appliance no VMware
- [ ] Registrar Appliance no Azure Migrate
- [ ] Conectar Appliance ao vCenter
- [ ] Rodar discovery e validar inventário
- [ ] Coletar performance (dias suficientes)
- [ ] Criar assessments (sizing/custo)
- [ ] Planejar ondas e executar migração (teste → cutover)
