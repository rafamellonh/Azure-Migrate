# 🔍 Azure Migrate – Escopo de Descoberta (Guia Detalhado)

Esse guia explica o que significa definir o **escopo de descoberta** no Azure Migrate, por que isso importa e como configurar corretamente para ter dados válidos de inventário e performance de VMs VMware antes da migração.

---

## 🎯 O que é “escopo de descoberta”?

O *escopo de descoberta* define **o que e como** o Azure Migrate vai coletar dados no seu ambiente:

- **Onde procurar** as máquinas (ex: vCenter)
- **Quais máquinas** serão incluídas
- **Como coletar métricas de performance**
- **Quais filtros** são aplicados (clusters, pastas, resource pools)

---

## 📌 Por que o escopo importa?

Definir corretamente o escopo:

✔️ Reduz tempo de coleta  
✔️ Evita inventário desnecessário  
✔️ Garante dados mais precisos para avaliação  
✔️ Permite dimensionamento correto das máquinas no Azure

Se o escopo estiver errado:
❌ Algumas VMs podem não ser descobertas  
❌ Métricas podem ser imprecisas  
❌ Cálculo de custo pode ficar incorreto

---

## 🧱 Onde você define o escopo

O escopo é definido quando você configura a **descoberta** para um endpoint, por exemplo:

1. **VMware vCenter**
2. **Credenciais de acesso**
3. **Filtros de escopo**
4. **Configurações de coleta de dados de performance**

---

## 🔐 1) Origem da descoberta

Você começa escolhendo:

- **Qual sistema será usado como fonte de descoberta**
  - Tipicamente: **VMware vCenter**

Essa origem define o ambiente que o Azure Migrate vai “ler”.

---

## 👤 2) Credenciais que determinam o escopo real

A conta usada para conectar ao vCenter determina o que pode ser visto.

Se a conta tem acesso só a alguns data centers ou clusters:
- O escopo ficará limitado a esses objetos

**Exemplo de problema real:**

Conta com acesso apenas ao Datacenter A → Azure Migrate só verá VMs desse datacenter

👉 Então sempre use uma conta que tenha visibilidade completa das VMs que você quer descobrir

---

## 📂 3) Filtros de escopo (o principal)

Aqui você define **quais partes do ambiente serão descobertas**:

Você pode filtrar por:

- **Datacenter**
- **Cluster**
- **Resource Pool**
- **Pasta de máquinas**
- **Tag ou grupo específico**

### 🧠 Quando usar filtros?

✔️ Ambiente grande (500+ VMs)  
✔️ Separar por aplicações  
✔️ Separar por ondas de migração  
✔️ Focar apenas nas VMs que você quer migrar

---

## 📊 4) Filtro do que será coletado

Além de “onde procurar VMs”, você também define **o que coletar**:

### 🗂 Inventário

- Nome da VM
- Sistema operacional
- CPU configurada
- Memória
- Discos
- Interfaces de rede

Esse inventário básico é obrigatório.

### 📈 Performance

Você escolhe **quantos dias de métricas** serão coletados:

- CPU (média, pico)
- Uso de memória
- IOPS de disco
- Throughput de rede

---

## ⏳ 5) Quantidade de coleta de performance

Isso é muito importante:

### 📌 Opções comuns

| Opção | Indicada quando |
|-------|------------------|
| **7 dias** | Projeto piloto, rápido |
| **14 dias** | Médio, root cause de uso |
| **30 dias** | Melhor precisão, variações |

---

## 🧠 Por que coletar mais dias?

Porque as métricas variam com:

- Pico de carga em determinados dias
- Workloads que ocorrem só em dias específicos
- Padrões diferentes (ex: fim de mês, backup, batch)

Coleta curta pode gerar **dimensionamento errado**

---

## 🧾 Exemplo prático de escopo

**Cenário:**
Você tem um cluster com 200 VMs, mas quer migrar só as VMs do time de ERP.

Passos:

1. Conectar appliance ao vCenter
2. Criar um filtro que inclua:
   - Cluster = ‘ERP-Cluster’
   - OU tag = ‘ERP-123’
3. Coletar 14 dias de performance
4. Revisar inventário antes de avaliação

---

## ⚠️ Situações em que o escopo pode causar problemas

### ❌ VM não aparece
Causas:
- Credenciais com acesso limitado
- Filtro errado (ex: nome de pasta errado)
- VM está desligada

---

### ❌ Métricas vazias ou imprecisas
Causas:
- Agente não coletou
- Tempo de coleta muito curto
- Appliance não foi registrado corretamente

---

## 🔄 6) Ajustando o escopo posteriormente

Se o escopo estiver errado ou incompleto, você pode:

1. Ajustar os filtros no appliance
2. Reexecutar a descoberta
3. Incluir novos clusters ou resource pools
4. Reiniciar coleta de métricas

---

## 🧰 Estratégias de descoberta recomendadas

### 🟡 Ambiente pequeno (até 50 VMs)

- Sem filtro  
- 7–14 dias de métricas

---

### 🟠 Ambiente médio (50–300 VMs)

- Filtrar por cluster ou aplicação
- 14–21 dias de métricas

---

### 🔵 Ambiente grande (300+ VMs)

- Divide por ondas
- Uso de filtros por tag/aplicação
- 21–30 dias de métricas

---

## 📍 Resumo dos principais pontos

✔️ Escopo define *onde* e *como* o Azure Migrate coleta dados  
✔️ Credenciais podem limitar o escopo real  
✔️ Filtros ajudam a reduzir ruído e tempo  
✔️ Métricas de performance só são úteis se coletadas por dias suficientes

---

## 📌 Conclusão

Definir corretamente o **escopo de descoberta** é um dos passos mais importantes antes de criar avaliações ou migrar VMs.  
Um escopo bem configurado garante:

🟢 Inventário completo  
🟢 Dados de performance reais  
🟢 Sizing confiável  
🟢 Planejamento de migração mais preciso

---

## 📌 Checklist prático

- [ ] Confirme credenciais com acesso completo
- [ ] Defina filtros de cluster/resource pool corretamente
- [ ] Escolha período de coleta adequado (ideal 14–30 dias)
- [ ] Verifique inventário antes de avaliação
- [ ] Ajuste escopo se necessário

