# 💻 Azure Migrate – Migração Agentless com VMware (Resumo)

## 📌 O que é migração *agentless*?

A **migração agentless** é um método em que você **não instala agentes nas máquinas virtuais (VMs)** que serão migradas de um ambiente VMware para o Microsoft Azure.

No Azure Migrate, esse método usa o software de replicação do Azure Migrate e o vCenter para mover VMs, sem a necessidade de instalar software dentro das VMs.

---

## 🎯 Quando usar a migração agentless?

Use a migração agentless quando:

- Você **não quer instalar agentes** nas VMs
- Sua infraestrutura é baseada em **VMware vSphere**
- Quer uma maneira **simplificada** de migrar servidores

Esse método funciona bem para a maioria dos cenários de *lift-and-shift*.

---

## 🧠 Como funciona a migração sem agente

### 🛠 Componentes envolvidos

1. **Azure Migrate Server Migration**
   - Serviço responsável por gerenciar cópias e migração de VMs

2. **VMware vCenter**
   - Coleta metadados do ambiente e fornece acesso de leitura às VMs

---

## 🔄 Fluxo de replicação

O processo principal inclui:

1. **Registro do appliance de migração**
   - Um appliance criado no vSphere que se comunica com o Azure Migrate

2. **Conexão com o vCenter**
   - O appliance conecta ao vCenter para monitorar VMs

3. **Monitoramento do estado da VM**
   - O Azure Migrate verifica metadados e informações de snapshot

4. **Replicação dos dados**
   - Dados da VM são copiados diretamente para a conta de destino no Azure

5. **Teste e execução da migração**
   - Você pode testar antes de fazer o corte final
   - Depois que os testes estiverem ok, faz o *cut-over* para Azure

---

## 📦 Vantagens da migração agentless

✔️ **Sem instalação de agentes nas VMs**  
✔️ Menor impacto na performance das máquinas  
✔️ Processo mais simples e menos invasivo  
✔️ Funciona para a maioria das instalações VMware

---

## ⚠️ Limitações e cuidados

❗ Algumas situações podem exigir soluções híbridas ou ferramentas adicionais:

- **Aplicações muito sensíveis a performance**
  → Pode ser preferível um método com agente
- **Dependências complexas**
  → Aplicações com muitas dependências podem precisar de avaliação detalhada
- **Requisitos específicos de rede ou compliance**
  → Pode exigir configuração adicional (por exemplo, Private Endpoints ou VPN)

---

## 📊 O que você precisa para usar agentless

Antes de começar:

🔹 Ter acesso ao **vCenter** do ambiente VMware  
🔹 Permissões de leitura e operação para criar *snapshots*  
🔹 Azure Migrate configurado com permissões adequadas  

---

## 🧭 Diferença entre agentless e com agente

| Aspecto                     | Agentless                     | Com agente                    |
|----------------------------|-------------------------------|-------------------------------|
| Instalar agente na VM       | ❌ Não                       | ✅ Sim                        |
| Impacto na VM               | 🔸 Baixo                     | 🔹 Pode ser maior             |
| Simplicidade de setup       | 🔸 Mais simples              | 🔹 Mais complexo              |
| Controle dentro da VM       | ❌ Limitado                  | ✅ Maior                      |

---

## 🧠 Resumo rápido

- A migração *agentless* usa o **vCenter + appliance de migração** para mover VMs,
- Funciona **sem instalar agentes nas máquinas**,
- É ideal para *lift-and-shift* de ambientes VMware,
- Oferece **replicação, testes e execução da migração** com menos impacto.

---

## 📍 Conclusão

A migração sem agente com VMware no Azure Migrate é uma **opção eficiente, simples e de baixo impacto** para mover VMs para o Azure, especialmente quando você quer evitar instalar software nas máquinas.

É uma das abordagens mais usadas para migrações em larga escala, especialmente em ambientes corporativos com muitos servidores VMware.

