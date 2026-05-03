# 🍪 Cookie Consent Manager

Um sistema simples, modular e compatível com a **LGPD** (Lei Geral de Proteção de Dados) para exibir o aviso de consentimento de cookies em qualquer site.

Este projeto permite que o visitante **aceite, rejeite ou personalize** o uso de cookies e scripts opcionais (como Google Analytics e ferramentas de marketing).

---

## 🧱 Estrutura do Projeto

```
/cookie-consent/
├── cookie-consent.js      # Script principal (lógica e controle)
├── cookie-consent.css     # Estilos do banner e do modal
└── exemplo.html           # Página de exemplo para testes
```

---

## 🚀 Recursos

✅ Banner de consentimento com três opções: **Aceitar**, **Rejeitar**, **Customizar**  
✅ Modal de preferências com categorias (necessários, analíticos, marketing)  
✅ Armazenamento das escolhas do usuário em `localStorage`  
✅ Bloqueio de scripts até que o usuário aceite  
✅ Compatível com qualquer site HTML (sem dependências externas)  
✅ 100% personalizável via CSS  

---

## ⚙️ Instalação

1. Baixe ou clone este repositório para o seu projeto:
   ```bash
   git clone https://github.com/seuusuario/cookie-consent.git
   ```

2. Copie os arquivos `cookie-consent.js` e `cookie-consent.css` para o diretório do seu site (por exemplo: `/assets/`).

3. Adicione as linhas abaixo **antes do fechamento da tag `<body>`** em seu HTML:

   ```html
   <link rel="stylesheet" href="/assets/cookie-consent.css">
   <script src="/assets/cookie-consent.js"></script>
   ```

Nome do fluxo
TiagoRogato.github.io
URL do fluxo
https://tiagorogato.github.io/landingpage/
Código do fluxo
12958408243
ID da métrica
G-WGCPGRYVN5


4. Crie (ou configure) as páginas de políticas mencionadas no banner:
   - `/privacidade` → Aviso de Privacidade  
   - `/termos` → Termos de Uso  

---

## 🧩 Exemplo de Uso

O arquivo `exemplo.html` já vem pronto para testes:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Exemplo - Sistema de Cookies</title>
  <link rel="stylesheet" href="cookie-consent.css">
</head>
<body>
  <h1>Bem-vindo!</h1>
  <p>Exemplo de uso do sistema de consentimento de cookies.</p>

  <!-- Sistema de cookies -->
  <script src="cookie-consent.js"></script>
</body>
</html>
```

---

## 🔍 Funcionamento Interno

1. **Primeiro acesso:**  
   O script verifica se existe um registro de consentimento no `localStorage`.  
   - Se **não existir**, o banner é exibido.  
   - Se já houver consentimento, os scripts autorizados são ativados automaticamente.

2. **Usuário escolhe uma opção:**
   - **Aceitar:** ativa todos os cookies (analytics e marketing).  
   - **Rejeitar:** mantém apenas cookies essenciais.  
   - **Customizar:** abre um painel para o usuário escolher categorias específicas.

3. **Armazenamento:**  
   As preferências são salvas no navegador do usuário:
   ```json
   {
     "necessary": true,
     "analytics": false,
     "marketing": true
   }
   ```

4. **Execução condicional:**  
   Scripts externos (como Google Analytics, Meta Pixel etc.) só são carregados se o consentimento permitir.

---

## ⚙️ Configuração de Scripts (Google Analytics, etc.)

Dentro do arquivo `cookie-consent.js`, localize o trecho:

```javascript
if (consent.analytics) {
  const s = document.createElement("script");
  s.src = "https://www.googletagmanager.com/gtag/js?id=G-XXXXXXX";
  document.head.appendChild(s);
  window.dataLayer = window.dataLayer || [];
  function gtag() { dataLayer.push(arguments); }
  gtag("js", new Date());
  gtag("config", "G-XXXXXXX");
}
```

Substitua `G-XXXXXXX` pelo seu **ID do Google Analytics**.

Você também pode adicionar scripts de **marketing**, **remarketing** ou qualquer outro SDK dentro do bloco `if (consent.marketing)`.

---

## 🎨 Personalização

Edite o arquivo `cookie-consent.css` para alterar:

- Cores dos botões (`#btn-aceitar`, `#btn-rejeitar`, `#btn-customizar`);
- Fontes e espaçamento;
- Posição do banner (`bottom/right` → pode ser `top/center`, por exemplo);
- Textos do banner ou do modal (alterando diretamente no JS, se desejar).

---

## 🧰 Funções Úteis

### 🔁 Resetar o consentimento
Para testar o comportamento do banner novamente, execute no console do navegador:

```js
localStorage.removeItem("cookie_consent_preferences");
```

### 📄 Obter o consentimento atual
```js
JSON.parse(localStorage.getItem("cookie_consent_preferences"));
```

---

## 🧑‍💻 Compatibilidade

- ✅ HTML5, CSS3, JavaScript ES5+  
- ✅ Compatível com todos os navegadores modernos  
- ✅ Não depende de frameworks ou bibliotecas externas  

---

## 🔒 Conformidade Legal

Este sistema auxilia na conformidade com a **LGPD (Lei 13.709/2018)** e com princípios semelhantes do **GDPR europeu**, mas é responsabilidade do controlador do site:

- Disponibilizar políticas claras de privacidade;  
- Manter registros de consentimento adequados;  
- Permitir a revogação do consentimento a qualquer momento.

---

## 🧠 Licença

Este projeto é de uso **livre e aberto** sob a licença MIT.

Você pode usar, modificar e distribuir à vontade, desde que mantenha os créditos originais.

---

## ✨ Autor

Desenvolvido por [Seu Nome ou Empresa]  
💼 Contato: [seu-email@dominio.com]  
🌐 Site: [https://seudominio.com](https://seudominio.com)

---

**Pronto!** 🎉  
Agora seu site possui um sistema de consentimento de cookies completo, modular e dentro das boas práticas da LGPD.
