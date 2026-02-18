# 📊 Azure Migrate – **Metadados Descobertos** (Resumo)

Este documento explica o que são os **metadados descobertos** no Azure Migrate, por que eles são importantes e como eles ajudam a planejar e executar migrações para o Azure.

---

## 🧠 O que são Metadados Descobertos?

Os **metadados descobertos** consistem nas informações que o Azure Migrate coleta de servidores, máquinas virtuais e outros recursos durante a etapa de **descoberta**.

Eles representam dados técnicos e de configuração que serão usados nas fases seguintes:

- Avaliação (*Assessment*)  
- Planejamento de migração  
- Dimensionamento de VMs no Azure  
- Estimativa de custos  

---

## 📋 Que informações fazem parte dos Metadados?

Quando o Azure Migrate realiza a descoberta, ele coleta dados como:

### 🔹 Identificação do recurso

- Nome da máquina
- Identificador único (ID)
- Sistema operacional

---

### 🛠️ Configuração da máquina

- CPU configurada (número de vCPUs)
- Memória RAM
- Discos anexados
- Interfaces de rede

Esses dados orientam o **dimensionamento correto no Azure**.

---

### 📈 Métricas de Performance

Quando habilitado, o Azure Migrate coleta também:

- Uso de CPU ao longo do tempo
- Uso de memória
- I/O de disco
- Throughput de rede

Esses dados ajudam a determinar:

✔️ Qual tamanho de VM no Azure é mais adequado  
✔️ Se haverá sobre-provisionamento ou sub-provisionamento

---

## 📌 Onde você vê esses Metadados

Após a descoberta concluída, no Portal do Azure:

- Azure Migrate → **Servidores descobertos**
- Clicar em uma máquina para ver:
  - Inventário
  - Configuração
  - Performance histórica
  - Detalhes técnicos

Essas informações são os **metadados que foram coletados**.

---

## 📊 Como os Metadados são usados

### 🟣 👨‍💼 **Avaliação (Assessment)**

Os metadados alimentam relatórios de:

- Compatibilidade com o Azure
- Sizing recomendado de máquinas
- Estimativas de custo
- Mapeamento de dependências (se coletado)

📌 Exemplo:  
Uma VM com 2 vCPUs e 8 GB de RAM pode ser recomendada como **Standard_DS2_v2** no Azure.

---

### 🔧 🎯 **Planejamento da Migração**

Com base nos metadados você pode:

- Separar máquinas por “ondas” de migração
- Identificar dependências
- Ajustar grupos de servidores por aplicação
- Definir janelas de manutenção

---

### 📈 📉 **Estimativas e Decisões**

Os metadados permitem responder:

- Quanto vai custar rodar no Azure?
- Qual a melhor região?
- Qual o tamanho ideal da VM?
- Precisamos reduzir recursos antes de migrar?

---

## 🧩 O que pode faltar nos Metadados

Em alguns cenários, os metadados podem não incluir:

✔️ Dados de aplicativos internos  
✔️ Configurações específicas do sistema operacional  
✔️ Dados de logs ou performance mais detalhados (necessitam de agentes)

Nesses casos, você pode usar:

- Ferramentas adicionais
- Instalar agentes internos
- Ferramentas de monitoramento específicas

---

## 📌 Resumo

Os **metadados descobertos** no Azure Migrate são:

🟢 Inventário da VM  
🟢 Configuração de hardware  
🟢 Dados de uso/performance  
🟢 Informação técnica usada na avaliação e planejamento

---

## 🔍 Porque isso é essencial

Sem metadados:

❌ Não dá para dimensionar corretamente  
❌ Estimativa de custo fica imprecisa  
❌ Migração pode falhar por incompatibilidade  
❌ Planejamento de ondas fica difícil

---

## 📌 Conclusão

Os metadados descobertos pelo Azure Migrate:

✔️ São a base de toda avaliação e migração  
✔️ Permitem decisões técnicas precisas  
✔️ Ajudam a evitar surpresas no Azure após a migração  
✔️ Devem sempre ser revisados antes de agir

---

## 🎯 Dica prática

Depois da descoberta:

1. Confirme que cada VM tem os metadados completos  
2. Verifique que os valores de CPU/RAM/IO estão corretos  
3. Use os dados para montar grupos por aplicação  
4. Compare sizing recomendado com sua arquitetura atual

