# 📦 Azure Migrate – Appliance de Migração (Resumo)

## 📌 O que é o Azure Migrate Appliance?

O **Azure Migrate Appliance** é uma máquina virtual (VM) Linux que funciona como um componente central para:

- Descobrir VMs em ambientes VMware
- Coletar inventário e dados de desempenho
- Enviar informações para o serviço Azure Migrate
- Suportar a replicação durante a migração

Ele atua como o ponto de comunicação entre seu ambiente local (on-premises) e o Azure.

---

## 🎯 Para que serve o Appliance?

O appliance é responsável por:

1️⃣ **Descobrir VMs no VMware (vCenter)**  
2️⃣ **Coletar métricas de desempenho (CPU, memória, disco)**  
3️⃣ **Enviar metadados para o Azure Migrate**  
4️⃣ **Apoiar o processo de migração agentless**

Sem o appliance, não é possível fazer descoberta e avaliação no modelo sem agente.

---

## 🧱 Como o Appliance Funciona?

### 🖥️ Implantação

- É importado no ambiente VMware como um arquivo **OVA**
- Roda como uma VM Linux dedicada
- Conecta-se ao **vCenter**

---

### 🔄 Fluxo de Operação

1. O appliance é implantado no VMware
2. Ele se conecta ao vCenter
3. Descobre as VMs e coleta informações
4. Envia os dados para o Azure Migrate
5. Permite avaliação e preparação para migração

---

## 📊 Dados Coletados

O appliance coleta:

- Nome da VM
- Sistema operacional
- CPU e memória configuradas
- Uso de CPU, memória e disco ao longo do tempo
- Informações de rede

Esses dados são usados para:

✔️ Avaliar compatibilidade  
✔️ Dimensionar corretamente a VM no Azure  
✔️ Estimar custos  

---

## 🔐 Requisitos Principais

### 🌐 Rede

- Conectividade de saída (HTTPS) para o Azure
- Ou uso de **Private Endpoint** para comunicação privada

### 🔑 Permissões no vCenter

- Conta com permissões de leitura
- Permissão para acessar informações das VMs

### 💻 Recursos do Appliance

- CPU e memória suficientes para o número de VMs descobertas
- Armazenamento adequado para coleta temporária de dados

---

## 🚀 Principais Etapas

### 1️⃣ Implantar o OVA no VMware

Importar o arquivo OVA no vCenter.

### 2️⃣ Configurar o Appliance

- Definir rede
- Registrar no projeto Azure Migrate

### 3️⃣ Conectar ao vCenter

Fornecer credenciais para permitir descoberta.

### 4️⃣ Iniciar Descoberta

O appliance começa a coletar inventário e métricas automaticamente.

---

## 🧠 Benefícios

✔️ Sem necessidade de instalar agentes nas VMs  
✔️ Processo centralizado  
✔️ Baixo impacto nas máquinas  
✔️ Ideal para migração VMware → Azure  
✔️ Permite avaliação precisa antes da migração  

---

## ⚠️ Pontos de Atenção

- O appliance precisa estar sempre ativo durante a coleta
- Permissões insuficientes no vCenter podem impedir descoberta
- Deve haver conectividade adequada com Azure

---

## 📌 Quando Usar

Use o Azure Migrate Appliance quando:

- Seu ambiente é baseado em **VMware**
- Você deseja fazer **descoberta e avaliação agentless**
- Precisa coletar métricas antes de migrar
- Quer planejar corretamente o dimensionamento no Azure

---

## 🧠 Conclusão

O **Azure Migrate Appliance** é o componente essencial para:

➡️ Descobrir VMs VMware  
➡️ Coletar dados de desempenho  
➡️ Enviar informações para o Azure  
➡️ Preparar o ambiente para migração  

Ele é a base do processo de avaliação e migração no modelo sem agente.

