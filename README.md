# 🟡 Brunel Cockpit — Guia de Configuração

> App interno de gestão de contas, calendário, tickets e documentos da equipe Brunel.

---

## 📁 Estrutura do Projeto

```
brunel-cockpit/
├── index.html   ← toda a aplicação (HTML + CSS + JS)
└── README.md    ← este guia
```

---

## 🔥 Configurando o Firebase (passo a passo)

O Brunel Cockpit usa o **Firebase Realtime Database** para que todos da equipe compartilhem os mesmos dados em tempo real, sem precisar de servidor.

### Passo 1 — Criar conta no Firebase

1. Acesse [https://console.firebase.google.com](https://console.firebase.google.com)
2. Faça login com uma conta Google (pode ser pessoal ou corporativa)

---

### Passo 2 — Criar o projeto

1. Clique em **"Adicionar projeto"**
2. Nome do projeto: `brunel-cockpit` (ou qualquer nome)
3. Desmarque o Google Analytics (opcional, não é necessário)
4. Clique em **"Criar projeto"**
5. Aguarde alguns segundos e clique em **"Continuar"**

---

### Passo 3 — Criar o Realtime Database

1. No menu lateral, clique em **"Build" → "Realtime Database"**
2. Clique em **"Criar banco de dados"**
3. Escolha a região: **United States (us-central1)** é recomendado
4. Em "Regras de segurança", selecione **"Iniciar no modo de teste"**
   > ⚠ Isso permite acesso livre por 30 dias. Depois configure as regras abaixo.
5. Clique em **"Ativar"**

---

### Passo 4 — Registrar o app Web

1. Na página inicial do projeto Firebase, clique no ícone **`</>`** (Web)
2. Apelido do app: `brunel-cockpit-web`
3. **Não** marque "Firebase Hosting"
4. Clique em **"Registrar app"**
5. Vai aparecer um bloco de código assim:

```js
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "brunel-cockpit.firebaseapp.com",
  databaseURL: "https://brunel-cockpit-default-rtdb.firebaseio.com",
  projectId: "brunel-cockpit",
  storageBucket: "brunel-cockpit.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

6. **Copie esses valores** — você vai precisar deles no próximo passo.
7. Clique em **"Continuar no console"**

---

### Passo 5 — Colar as credenciais no app

1. Abra o arquivo `index.html` em qualquer editor de texto
   (Notepad, VS Code, Sublime, etc.)
2. Localize o bloco marcado com `🔧 CONFIGURE FIREBASE AQUI` (busque por essa frase)
3. Substitua os placeholders pelos valores do passo anterior:

```js
// ANTES (placeholders):
const FIREBASE_CONFIG = {
  apiKey:            "COLE_SEU_API_KEY_AQUI",
  authDomain:        "COLE_SEU_AUTH_DOMAIN_AQUI",
  databaseURL:       "COLE_SUA_DATABASE_URL_AQUI",
  projectId:         "COLE_SEU_PROJECT_ID_AQUI",
  storageBucket:     "COLE_SEU_STORAGE_BUCKET_AQUI",
  messagingSenderId: "COLE_SEU_MESSAGING_SENDER_ID_AQUI",
  appId:             "COLE_SEU_APP_ID_AQUI"
};

// DEPOIS (com seus dados reais):
const FIREBASE_CONFIG = {
  apiKey:            "AIzaSy...",
  authDomain:        "brunel-cockpit.firebaseapp.com",
  databaseURL:       "https://brunel-cockpit-default-rtdb.firebaseio.com",
  projectId:         "brunel-cockpit",
  storageBucket:     "brunel-cockpit.appspot.com",
  messagingSenderId: "123456789",
  appId:             "1:123456789:web:abc123"
};
```

4. Salve o arquivo.

---

### Passo 6 — Publicar no GitHub Pages

Para que todos da equipe acessem o app pelo navegador:

1. Crie um repositório no GitHub (pode ser privado)
2. Suba o arquivo `index.html` (e este README)
3. Vá em **Settings → Pages**
4. Em "Source", selecione **"Deploy from a branch"**
5. Branch: `main`, pasta: `/ (root)`
6. Clique em **"Save"**
7. Aguarde ~2 minutos e o link do app aparecerá no topo da página

> O link será algo como: `https://SEU_USUARIO.github.io/brunel-cockpit`

---

### Passo 7 — Configurar regras do Firebase (segurança)

Após os 30 dias de modo teste, configure as regras para exigir autenticação básica. No console Firebase, vá em **Realtime Database → Regras** e cole:

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

> Para produção com mais segurança, consulte a documentação do Firebase Auth.

---

## 👥 Usuários do sistema

| Usuário     | Senha padrão       | Observação                    |
|-------------|-------------------|-------------------------------|
| ADMIN       | `Casaca`           | Pode resetar senhas de outros |
| D.DINIZ     | (define no 1º acesso) | —                         |
| J.TROTTE    | (define no 1º acesso) | —                         |
| C.BALDOTTO  | (define no 1º acesso) | —                         |
| C.LAGOA     | (define no 1º acesso) | —                         |
| LUIZ.O      | (define no 1º acesso) | —                         |
| LIVIA.O     | (define no 1º acesso) | —                         |
| R.ALMEIDA   | (define no 1º acesso) | —                         |
| S.BRAGA     | (define no 1º acesso) | —                         |

---

## 📋 Funcionalidades

| Aba               | O que faz                                                        |
|-------------------|------------------------------------------------------------------|
| **Contas**        | Cadastra clientes com CNPJ, endereço, benefícios e organograma  |
| **Calendário**    | Eventos de visitação/onboarding por área de atuação             |
| **Freshdesk**     | Tickets internos com fluxo de 3 etapas e categorias coloridas   |
| **Ativos**        | Import de planilhas Excel com agenda de desligamentos            |
| **Documentos**    | Repositório de documentos com upload drag & drop                 |

---

## 🔧 Suporte

Em caso de dúvidas sobre a configuração do Firebase, consulte a [documentação oficial](https://firebase.google.com/docs/database/web/start).
