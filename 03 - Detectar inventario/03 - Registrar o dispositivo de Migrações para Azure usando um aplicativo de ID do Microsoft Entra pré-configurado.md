# 🔌 Registrar o Azure Migrate Appliance Usando um App do Microsoft Entra (Azure AD) – Resumo

Este guia mostra como **registrar o Azure Migrate appliance usando um aplicativo no Microsoft Entra ID (anteriormente Azure AD)**.  
Esse tipo de registro é necessário especialmente em ambientes que usam **Private Endpoints** ou cenários onde você precisa que o Appliance se autentique de forma segura com privilégios mínimos.

---

## 📌 Por que usar um Aplicativo do Microsoft Entra?

Ao registrar um **app no Microsoft Entra ID**, você:

- Tem controle preciso de permissões
- Pode aplicar princípio de menor privilégio
- Evita uso de contas pessoais
- Suporta cenários com controle de rede (como Private Endpoints)

---

## 🧠 O que você precisa antes de começar

Antes de registrar o appliance:

1. Acesso ao **Azure Portal**
2. Permissões para criar aplicativos no Microsoft Entra ID
3. Grupo de recursos onde o *appliance* será registrado
4. Projeto Azure Migrate criado

---

## 🚶‍♂️ Etapas para Registrar o Appliance

### 1️⃣ Criar um Aplicativo no Microsoft Entra ID

1. No Azure Portal, vá para **Microsoft Entra ID → Registros de aplicativos**
2. Clique em **Novo registro**
3. Informe:
   - Nome
   - Tipo de conta compatível
4. Crie a aplicação

---

### 2️⃣ Criar um Segredo de Cliente (Client Secret)

1. No app criado, vá em **Certificados e segredos**
2. Adicione um novo **segredo de cliente**
3. Copie o **valor do segredo** para usar no appliance

---

### 3️⃣ Anotar IDs Importantes

Durante o processo, anote:

- **Application (client) ID**
- **Directory (tenant) ID**
- **Client Secret**

Você vai usar essas informações para registrar o appliance.

---

### 4️⃣ Atribuir Permissões ao Aplicativo

No mesmo app:

1. Vá em **Permissões de API**
2. Adicione permissões para:
   - Microsoft Graph
   - Azure Service Management
3. Conceda permissão de **leitura e gravação** conforme necessário

---

### 5️⃣ Criar Papel (Role) no Azure

No escopo do **Grupo de Recursos** onde o appliance será registrado:

1. Vá em **Controle de Acesso (IAM)**
2. Adicione **funções necessárias**
   - Ex.: **Contribuidor**
3. Atribua ao App criado

Isso dá ao app permissão de ler/registrar o appliance.

---

### 6️⃣ Registrar o Appliance Usando App

No processo de registro do appliance:

1. Escolha **Registrar usando um aplicativo**
2. Insira:
   - **Tenant ID**
   - **Client ID**
   - **Client Secret**
3. Complete o registro

---

## 🔐 Verificação e Validação

Após registrar:

✔️ Verifique se o appliance aparece no projeto Azure Migrate  
✔️ Confira se a autenticação foi concluída  
✔️ Garanta que dados estão sendo enviados corretamente  

---

## 🛡 Vantagens dessa abordagem

✔️ Permite aplicar **menor privilégio**  
✔️ Funciona em ambientes com **Private Endpoints**  
✔️ Melhora segurança e controle de acesso  
✔️ Evita uso de credenciais de usuário

---

## 📌 Quando usar essa forma de registro

Use o registro via app quando:

- Você tem **regras de segurança de rede rígidas**
- Está usando **Azure Private Endpoints**
- Quer aplicar **princípio least-privilege**
- Prefere usar identidades de aplicação em vez de credenciais pessoais

---

## 🧠 Em resumo

Registrar o appliance usando um **aplicativo do Microsoft Entra ID**:

- Envolve criar um app e segredo
- Requer atribuir papéis adequados
- Permite registrar o appliance de forma segura
- É indicado em ambientes corporativos com controle de acesso rigoroso

