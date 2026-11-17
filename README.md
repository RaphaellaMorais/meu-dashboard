# 🌌 Morning Productivity Dashboard | Por onde começo hoje?

> Um dashboard diário minimalista e imersivo com tema dark/glassmorphism, integração em tempo real com o ecossistema Google (Gmail, Calendar e Tasks) e um ritual consciente de início de dia com tiragem interativa de Tarot.

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Google Cloud](https://img.shields.io/badge/Google_Cloud_OAuth2-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)](https://cloud.google.com/)
[![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?style=for-the-badge&logo=chartdotjs&logoColor=white)](https://www.chartjs.org/)

---

## 💡 Sobre o Projeto

O **"Por onde começo hoje?"** nasceu para resolver a sobrecarga cognitiva e a dispersão ao iniciar o dia de trabalho. Em vez de abrir múltiplas abas pesadas de e-mail, agenda e gerenciadores de tarefas, o usuário encontra em uma única tela focada:

1. **Contexto Operacional Real:** E-mails não lidos, reuniões do dia e tarefas pendentes integradas diretamente via APIs oficiais da Google.
2. **Contexto Histórico:** Gráfico semanal de volume de mensagens para dimensionar a intensidade da semana.
3. **Ritual de Atenção Plena:** Um insight motivacional diário e uma tiragem interativa do **Tarot do Dia** em 3D, unindo produtividade pragmática e introspecção.

---

## ✨ Principais Funcionalidades

### 🔐 Integração Oficial com o Google Workspace
- **Google Identity Services (GSI & GAPI):** Autenticação segura OAuth 2.0 baseada em tokens de escopo estrito de leitura (`.readonly`).
- **Gmail API:** Contagem em tempo real de e-mails não lidos na caixa de entrada principal.
- **Google Calendar API:** Próximo compromisso e listagem estruturada dos eventos do dia com horário e duração calculada.
- **Google Tasks API:** Lista de pendências com detecção de atraso e status visual.

### 🃏 Tarot do Dia com Animação 3D & Ilustrações Customizadas
- **Sorteio Determinístico Diário:** Algoritmo de hash baseado na data (`YYYY-MM-DD`). A mesma carta acompanha o usuário ao longo de todo o dia.
- **Efeito Flip 3D:** Animação suave com perspectiva CSS 3D ao clicar para desvirar a carta.
- **Ilustrações Exclusivas:** Artes ricas para Arcanos Maiores (*O Sol, A Lua, A Estrela, O Mago*) e bordas douradas clássicas.
- **Fundo Místico Dinâmico:** Partículas de estrelas e constelações flutuantes animadas em CSS e HTML5 Canvas.

### 📊 Gráfico de Volume Semanal (Chart.js)
- Gráfico de barras dark mode contextualizando a intensidade dos últimos 7 dias.

### 🎭 Modo Demonstração (Guest Mode)
- Permite que recrutadores, desenvolvedores e visitantes experimentem o dashboard e suas interações **instantaneamente**, sem a necessidade de vincular uma conta pessoal do Google.

---

## 🛠️ Stack Tecnológica & Decisões de Arquitetura

| Camada | Tecnologia | Motivação & Decisão Técnica |
| :--- | :--- | :--- |
| **Core** | Vanilla HTML5 & ES6+ | Zero dependências pesadas de build (sem Webpack/Vite), performance ultrarrápida e compatibilidade nativa com GitHub Pages. |
| **Estilização** | CSS Moderno & Glassmorphism | CSS Custom Properties, Flexbox, CSS Grid, `backdrop-filter: blur()`, transições CSS aceleradas por GPU. |
| **APIs Google** | GSI (Google Identity) + GAPI | Utilização do protocolo mais recente da Google para OAuth2 web, sem expor `client_secret`. |
| **Resiliência** | `Promise.allSettled` | Chamadas assíncronas isoladas: a indisponibilidade de uma API (ex: Tasks) não quebra a renderização das demais (Gmail/Calendar). |
| **Visualização** | Chart.js 4.x via CDN | Gráficos responsivos leves com paleta de cores harmonizada com o tema escuro. |
| **Ícones** | Lucide Icons (CDN) | Ícones SVG nítidos e consistentes em toda a interface. |

---

## 🚀 Como Executar Localmente

### Pré-requisitos
- Navegador web moderno (Chrome, Edge, Firefox, Safari).
- Python 3 instalado (para o servidor local de teste) ou a extensão *Live Server* do VS Code.

### Passo a Passo

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
   cd SEU-REPOSITORIO
   ```

2. **Inicie um servidor HTTP local:**
   ```bash
   # Com Python:
   python -m http.server 8000
   ```

3. **Abra no navegador:**
   Acesse: [`http://localhost:8000`](http://localhost:8000)

---

## ⚙️ Configuração da Google Cloud API (Para Novos Desenvolvedores)

Caso queira conectar seu próprio projeto do Google Cloud:

1. Acesse o [Google Cloud Console](https://console.cloud.google.com/).
2. Crie um projeto e ative as seguintes APIs na biblioteca:
   - **Gmail API**
   - **Google Calendar API**
   - **Google Tasks API**
3. Configure a **Tela de Consentimento OAuth** com os escopos:
   - `openid`, `profile`, `email`
   - `https://www.googleapis.com/auth/gmail.readonly`
   - `https://www.googleapis.com/auth/calendar.readonly`
   - `https://www.googleapis.com/auth/tasks.readonly`
4. Crie uma credencial de **ID do cliente OAuth 2.0 (Aplicativo Web)**:
   - **Origens JavaScript autorizadas:** `http://localhost:8000` (e a URL do seu GitHub Pages).
5. Substitua a constante `CLIENT_ID` no arquivo `index.html`.

---

## 🛡️ Segurança & Privacidade

- **Client-Side Only:** Nenhuma credencial ou dado pessoal (e-mails, reuniões) é armazenado em banco de dados externo ou servidor intermediário.
- **Escopo Estrito de Leitura:** O aplicativo solicita permissão única e exclusiva de **leitura** (`.readonly`). Não realiza envios, exclusões ou alterações na conta do usuário.

---

## 👩‍💻 Autora

Desenvolvido por **Raphaella** ✨  
- [LinkedIn](https://linkedin.com)
- [GitHub](https://github.com)

---
*Gostou do projeto? Deixe uma ⭐️ no repositório!*
