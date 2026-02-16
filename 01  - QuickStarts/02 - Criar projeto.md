# 📘 Criar um Projeto no Azure Migrate

Este guia mostra como **criar um projeto no Azure Migrate** por meio do Portal do Azure. Um projeto é usado para armazenar metadados de descoberta, avaliação e migração do seu ambiente. :contentReference[oaicite:0]{index=0}

---

## 🔐 1) Verificar Permissões

Antes de criar o projeto, verifique se sua conta tem as permissões necessárias:

1. No **Azure Portal**, abra a assinatura onde vai criar o projeto.  
2. Vá em **Controle de Acesso (IAM)** e clique em **Verificar acesso**.  
3. Confirme se você tem a função **Azure Migrate Owner** ou uma superior. :contentReference[oaicite:1]{index=1}

> ❗A partir de **novembro de 2025**, apenas usuários com a função *Azure Migrate Owner* ou superior poderão criar projetos de migração. :contentReference[oaicite:2]{index=2}

---

## 🚀 2) Criar o Projeto Passo a Passo

### 🟢 Passo 1 — Acessar o Azure Migrate

No Portal do Azure:

🔎 Pesquise por **Azure Migrate** e abra o serviço. :contentReference[oaicite:3]{index=3}

![Exemplo de busca por Azure Migrate no Azure Portal](https://learn.microsoft.com/azure/migrate/media/overview/azure-migrate-portal-search.png)

---

### 🟢 Passo 2 — Iniciar a Criação

Na página do Azure Migrate:

👉 Selecione **Descobrir, avaliar e migrar**. :contentReference[oaicite:4]{index=4}

---

### 🟢 Passo 3 — Selecionar Criar Projeto

Na seção **Servidores, bancos de dados e aplicativos Web**:

👉 Clique em **Criar projeto**. :contentReference[oaicite:5]{index=5}

![Exemplo de botão “Criar projeto”](https://learn.microsoft.com/azure/migrate/media/overview/azure-migrate-create-project.png)

---

### 🟢 Passo 4 — Configurar Projeto

Na tela de criação:

🔹 Selecione a **Assinatura Azure** onde o projeto será criado. :contentReference[oaicite:6]{index=6}  
🔹 Escolha ou crie um **Grupo de Recursos**. :contentReference[oaicite:7]{index=7}  
🔹 Informe o **Nome do projeto**. :contentReference[oaicite:8]{index=8}  
🔹 Selecione a **Geografia** (localização onde os metadados serão armazenados). :contentReference[oaicite:9]{index=9}

> 💡 A geografia determina apenas onde os metadados serão guardados. Você ainda pode migrar recursos para qualquer região de destino. :contentReference[oaicite:10]{index=10}

---

### 🟢 Passo 5 — Criar

Após informar os dados do projeto:

👉 Clique em **Criar** e aguarde alguns minutos até a conclusão. :contentReference[oaicite:11]{index=11}

---

## 🧠 3) Projetos Adicionais

Se você já tem um projeto e quiser criar outro:

1. No Portal do Azure, abra **Azure Migrate**. :contentReference[oaicite:12]{index=12}  
2. No painel do dashboard, selecione **Todos os projetos**. :contentReference[oaicite:13]{index=13}  
3. Clique novamente em **Criar projeto**. :contentReference[oaicite:14]{index=14}

---

## 🗑 4) Excluir um Projeto

Para excluir um projeto existente:

1. Abra o **Grupo de Recursos** onde ele foi criado. :contentReference[oaicite:15]{index=15}  
2. Selecione o projeto que deseja remover. :contentReference[oaicite:16]{index=16}  
3. Clique em **Excluir** e confirme. :contentReference[oaicite:17]{index=17}

> ❗Isso apagará todos os metadados associados do Azure Migrate. :contentReference[oaicite:18]{index=18}

---

## 📌 Observações

- O comando de API também permite criar o projeto em uma **região específica** usando o `PUT` com parâmetros. :contentReference[oaicite:19]{index=19}  
- Use **Configuração Avançada** se o projeto precisar de conectividade via *private endpoint*. :contentReference[oaicite:20]{index=20}

---

## 🚀 Próximos Passos

Depois de criar seu projeto, você pode:

- Adicionar ferramentas de **Avaliação** para coletar inventário e dependências.
- Adicionar ferramentas de **Migração** para começar mover workloads. :contentReference[oaicite:21]{index=21}
