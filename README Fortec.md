# 🛡️ FORTEC – Fortaleza Tecnológica

> Sistema web *mobile-first* de **controle de acesso inteligente** para campus universitário, integrado a catracas automatizadas. Cartão de acesso digital com **QR Code dinâmico (TOTP)**, PIN alternativo, convites de visitantes, histórico de acessos e painel de gestão em tempo real.

![Status](https://img.shields.io/badge/status-demo%20%2F%20pitch-22d3ee)
![Stack](https://img.shields.io/badge/stack-HTML%20%7C%20Tailwind%20%7C%20JS-2563eb)
![Arquivo](https://img.shields.io/badge/arquivo-%C3%BAnico-0a1f55)

---

## 📋 Sobre o projeto

O FORTEC simula a experiência de um aplicativo móvel para identificação segura em um campus. O aluno, professor, servidor ou visitante apresenta um QR Code que **se renova a cada 30 segundos** (protegendo contra prints e compartilhamento), e a administração acompanha acessos, catracas e alertas em tempo real.

Esta versão é uma **demonstração funcional** (front-end only), pronta para apresentações, com dados simulados realistas de um ambiente universitário.

## ✨ Funcionalidades

| Tela | O que oferece |
|---|---|
| **Cadastramento** | Onboarding em 3 etapas: foto de perfil, dados cadastrais (nome, CPF, matrícula, e-mail institucional, tipo de usuário) e senha com aceite de privacidade |
| **Home / Cartão Digital** | QR Code dinâmico com barra de contagem regressiva, PIN de 6 dígitos com atualização manual, status de acesso, última entrada e ações rápidas |
| **Convite de Visitante** | Formulário rápido que gera passe temporário com QR, PIN `VIS-xxx-xxx`, validade com tempo restante, dados do visitante e regras de acesso |
| **Painel do Administrador** | Métricas ao vivo, status das catracas, feed de eventos em tempo real, gráfico de tráfego por horário e atalhos de gestão |
| **Histórico de Acessos** | Filtro por data e local; lista com horário, bloco/portaria, entrada ou saída, método (QR/PIN) e status |
| **Perfil e Configurações** | Edição de foto e dados, senha, biometria, 2FA, notificações, dispositivos conectados e logout |
| **Simulador de Catraca** | Modal que valida o QR/PIN atual ou o passe de visitante, com feedback visual, sonoro e vibração; registra a leitura no Histórico e no Painel Admin |

## 🔐 Segurança, privacidade e normas

O projeto foi estruturado com princípios inspirados em:

- **ISO/IEC 27001** – tokens com expiração real (TOTP, janela de 30 s) e bloqueio de reutilização (*anti-replay*).
- **ISO/IEC 27701 / LGPD** – mascaramento de dados sensíveis (CPF exibido como `***.456.789-**`), aviso de privacidade e coleta mínima.
- **ISO/IEC 25010** – usabilidade, interface responsiva e resposta rápida, otimizada para uso com uma mão.
- **ISO/IEC 18004** – QR Code com correção de erro nível **M** e zona silenciosa adequada, renderizado com pixels nítidos.

> ⚠️ **Importante:** nesta demo o segredo TOTP fica no código do navegador. Em produção, a geração e a validação dos tokens devem ocorrer **no servidor** (idealmente com o segredo em HSM/cofre), com HTTPS, rate limiting e auditoria.

## 🧰 Tecnologias

- HTML5, CSS3 e JavaScript puro (sem build, sem dependências locais)
- [Tailwind CSS](https://tailwindcss.com/) via CDN
- [Lucide Icons](https://lucide.dev/) via CDN
- [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) via CDN
- Web Crypto API (HMAC-SHA1) para o TOTP, com *fallback* para navegadores sem suporte
- Web Audio API e Vibration API para o feedback da catraca

## 🚀 Como executar

1. Clone o repositório:
   ```bash
   git clone https://github.com/<RayaneMaria418>/fortec.git
   cd fortec
   ```
2. Abra o `index.html` diretamente no navegador (é necessária conexão com a internet para carregar as bibliotecas via CDN).

   Opcionalmente, sirva localmente:
   ```bash
   python3 -m http.server 8000
   # acesse http://localhost:8000
   ```
3. Para a melhor experiência, use o modo de visualização mobile do navegador (F12 → ícone de dispositivo).

## 🎬 Roteiro de demonstração (pitch)

1. Abra o app e clique em **"Pular"** para entrar com a conta de demonstração (ou percorra o onboarding).
2. Na **Home**, mostre o QR renovando a cada 30 s e o PIN alternativo.
3. Clique em **"Simular catraca"** → **"Ler QR Code atual"** e veja o *Acesso Liberado*.
4. Leia o mesmo QR de novo para demonstrar o bloqueio *anti-replay*; use o botão de atualizar para gerar um novo token.
5. Abra o **Histórico** e veja a nova entrada registrada.
6. Acesse o **Painel Admin** pelo chip *ADMIN*: eventos chegando ao vivo, alertas e gráfico de tráfego.
7. Em **Meus QRs**, gere um **passe de visitante** e teste a leitura no simulador.

## 🗂️ Estrutura

```
fortec/
├── index.html   # aplicação completa (HTML + CSS + JS)
└── README.md
```

O código do `index.html` é organizado em seções comentadas: estado e dados mock, utilidades, navegação, onboarding, TOTP, home/perfil, visitante, histórico, admin e simulador.

## 🛣️ Próximos passos

- [ ] Backend para emissão e validação de tokens TOTP e persistência de dados
- [ ] Integração real com leitores/catracas (MQTT, REST ou WebSocket)
- [ ] Gestão completa de usuários, convites e relatórios (PDF/CSV)
- [ ] Autenticação real (SSO institucional, biometria nativa)
- [ ] Transformar em PWA instalável com modo offline para o cartão de acesso
- [ ] Testes automatizados e auditoria de acessibilidade (WCAG)


## 📄 Licença

.gitignore

---

<p align="center">Feito para o campus do futuro · <b>FORTEC – Fortaleza Tecnológica</b></p>
