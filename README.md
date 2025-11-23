# Portfólio Profissional – Gabriel Menoncin

Aplicação web em **React** que apresenta meu portfólio profissional unindo **Suporte de TI, Infraestrutura e Design Gráfico** em uma Single Page Application (SPA) moderna, responsiva e com integrações em tempo real (GitHub, clima, música e envio de e‑mail).

---

## Índice

- [Visão Geral](#visão-geral)
- [Demo](#demo)
- [Funcionalidades Principais](#funcionalidades-principais)
- [Arquitetura & Tecnologias](#arquitetura--tecnologias)
- [Internacionalização (i18n)](#internacionalização-i18n)
- [Hooks Customizados](#hooks-customizados)
- [Componentes de UI](#componentes-de-ui)
- [Integrações Externas](#integrações-externas)
- [UX, Acessibilidade e Animações](#ux-acessibilidade-e-animações)
- [Estrutura do Código](#estrutura-do-código)
- [Como Rodar o Projeto](#como-rodar-o-projeto)
- [Configuração de Variáveis/API Keys](#configuração-de-variáveisapi-keys)
- [Boas Práticas e Decisões de Design](#boas-práticas-e-decisões-de-design)
- [Roadmap / Próximos Passos](#roadmap--próximos-passos)
- [Licença](#licença)

---

## Visão Geral

Este projeto é um **portfólio profissional** desenvolvido como uma **SPA (Single Page Application)** utilizando **React 18**.  
O foco é apresentar, de forma clara e visualmente agradável, minhas experiências com **Suporte Técnico**, **Infraestrutura de TI** e **Design Gráfico**, além de integrar informações em tempo real como clima, música atual e estatísticas do GitHub.

A aplicação foi pensada para ser:
- **Modular**: baseada em componentes reutilizáveis.
- **Escalável**: fácil de estender com novas seções e integrações.
- **Performática**: uso de Vite, Tailwind e hooks otimizados.
- **Acessível**: suporte a navegação por teclado, contraste e ARIA.

---

## Demo

- **Produção (Deploy)**: _adicione aqui a URL do deploy (Vercel, Netlify, etc.)_
- **Snapshot**: _adicione aqui uma imagem de preview da aplicação_

---

## Funcionalidades Principais

- **Hero / Apresentação**
  - Destaque de nome, status profissional e frase de efeito.
  - Texto dinâmico com áreas de atuação (Suporte de TI • Infraestrutura • Design Gráfico).
  - CTA principal para contato.

- **Sobre Mim**
  - Descrição em profundidade do perfil profissional.
  - Localização, foco atual (graduação em Ciência da Computação – UFFS) e mindset criativo.

- **Skills**
  - Separação entre:
    - **Infraestrutura & TI** (Hardware, Redes, Help Desk, Backup, Sistemas).
    - **Soft Skills & Sistemas** (Comunicação, Adaptabilidade, Multimídia).
  - Marquee infinito com ícones (Hardware, Redes, Segurança, Linux, Design, etc.).

- **Experiência Profissional**
  - Cards com empresas, período, localização e responsabilidades.
  - Foco em:
    - Suporte técnico (Service Desk / Help Desk).
    - Infraestrutura (hardware, redes, backup).
    - Educação digital e inclusão tecnológica.

- **Formação Acadêmica**
  - Curso, instituição, status e foco da graduação.

- **GitHub & Open Source**
  - Seção voltada para explorar perfil GitHub e estatísticas de código.

- **Portfólio Criativo (Design)**
  - Galeria com peças de:
    - Social Media (campanhas de Ano Novo, Natal, etc.).
    - Marketing corporativo.
    - Identidade visual (branding pessoal, logotipo).
    - Materiais impressos.

- **Contato**
  - Formulário integrado com **EmailJS** para envio serverless.
  - Links para redes sociais (GitHub, LinkedIn, Instagram, etc.).

- **Música Atual (Last.fm)**
  - Exibição da faixa mais recente tocada (via Last.fm).
  - Indicação se a música está tocando agora ou foi a última reprodução.

- **Clima Atual (Open-Meteo)**
  - Consumo da API do **Open-Meteo** combinado com **Geolocation API** do navegador.
  - Se permissão negada, usa cidade padrão (ex.: Quilombo, SC).

- **Comandos via Teclado (Command Palette)**
  - Atalho (ex.: `Ctrl + K`) para abrir uma paleta de comandos:
    - Navegar para seções (Início, Sobre, Skills, Experiência, Contato).
    - Alternar tema Dark/Light.
    - Baixar currículo.
    - Abrir GitHub.
    - Abrir documentação técnica interna.

- **Tema Escuro/Claro**
  - Persistência no `localStorage`.
  - Respeito à preferência do sistema (`prefers-color-scheme`).

- **Documentação Interna**
  - Modal de “Documentação” que mostra uma especificação técnica resumida do projeto, tanto em PT-BR quanto em EN.

---

## Arquitetura & Tecnologias

**Frontend / Core**
- [x] **React 18**
- [x] **Vite** (ferramenta de build e dev server)
- [x] **JavaScript (ES202x)**

**Estilização**
- [x] **Tailwind CSS v3** (utility-first)
- [x] **Tema Dark/Light** com classes utilitárias
- [x] **Google Fonts** (ex.: Inter, Roboto)

**Ícones & UI**
- [x] **lucide-react** para ícones em SVG
- [x] Componentes customizados de layout e animação

**Integrações externas**
- [x] **Last.fm API** – música atual
- [x] **Open-Meteo API** – clima/temperatura
- [x] **GitHub Stats** – estatísticas do perfil
- [x] **EmailJS** – envio do formulário de contato

---

## Internacionalização (i18n)

O projeto possui um sistema de internacionalização manual baseado em objetos de tradução:

- Idiomas suportados:
  - `pt` – Português (Brasil)
  - `en` – Inglês

- Estrutura:
  - Objeto `translations` organizado por seções:
    - `nav`, `hero`, `about`, `skills`, `experience`, `education`,
      `github`, `contact`, `spotify`, `gallery`, `docs`, `command`, etc.
  - Cada chave contém textos equivalentes em PT e EN.

A troca de idioma é feita alterando a linguagem atual em estado global/local, e todos os componentes consomem o objeto `t` (traduções) correspondente.

---

## Hooks Customizados

O projeto define diversos **hooks customizados** para encapsular lógica de negócio e de UI:

- `useSEO(lang)`
  - Atualiza `document.title`.
  - Gerencia meta tags de SEO e Open Graph (descrição, título, imagem, twitter card).
  - Mantém as informações atualizadas conforme o idioma.

- `useOnScreen(ref, rootMargin?)`
  - Usa **Intersection Observer API**.
  - Retorna `true` quando o elemento entra na área visível da tela.
  - Base para animações de entrada ao rolar a página.

- `useDelayUnmount(isMounted, delayTime)`
  - Mantém componente montado por um tempo após mudança de estado.
  - Ideal para animações de saída (fade-out em modais, por exemplo).

- `useKonamiCode()`
  - Escuta sequência de teclas do famoso “Konami Code”.
  - Ao detectar a sequência correta, retorna `success = true` para habilitar um Easter Egg.

- `useLastFm()`
  - Faz pooling periódico na **Last.fm API** (ex.: a cada 30 segundos).
  - Busca a faixa mais recente do usuário configurado.
  - Retorna objeto com:
    - `song`, `artist`, `albumCover`, `previewUrl`, `isPlaying`, `isError`.

- `useWeather()`
  - Tenta obter coordenadas via `navigator.geolocation`.
  - Se aprovado:
    - Busca clima atual na **Open-Meteo** usando latitude/longitude do usuário.
    - Define `locationName` como “Local”.
  - Se negado/falha:
    - Usa coordenadas e nome de cidade padrão (ex.: Quilombo).
  - Retorna `{ weather, locationName }`.

---

## Componentes de UI

Alguns componentes importantes:

- `InfiniteMarquee`
  - Faixa horizontal com ícones e textos rolando em loop.
  - Representa áreas de atuação (Hardware, Redes, Segurança, Design, etc.).

- `AnimatedSection`
  - Wrapper que aplica animações de entrada (fade-up, slide-right, scale-up).
  - Usa `useOnScreen` para só animar quando entra na viewport.
  - Recebe props como `delay` e `animationType`.

- `Documentation`
  - Modal de página inteira exibindo documentação técnica.
  - Usa `useDelayUnmount` para animação suave ao fechar.
  - Consome `t.docs.sections` para renderizar blocos de conteúdo.

- `CommandPalette`
  - Paleta de comandos estilo “command menu”.
  - Filtra ações conforme o texto digitado.
  - Permite navegação por teclado (setas, Enter, Escape).
  - Executa ações como scroll para seções, abrir links, alternar tema, abrir docs, etc.

> Obs.: Outros componentes (Header, Footer, Cards, Formulário de Contato, Widgets de GitHub/Spotify/Clima) seguem a mesma filosofia: componentes pequenos, focados e reutilizáveis.

---

## Integrações Externas

### Last.fm – Música Atual

- Endpoint: `user.getrecenttracks`
- Uso:
  - Consulta o usuário configurado.
  - Extrai a faixa mais recente e se está tocando agora.
- Tratamento:
  - Estados de erro, ausência de músicas, fallback de imagem de álbum.

### Open-Meteo – Clima

- Endpoint de forecast com `current_weather=true`.
- Usa latitude/longitude:
  - Via geolocalização do navegador ou coordenadas padrão.
- Exibe:
  - Temperatura atual, condições básicas.

### GitHub – Estatísticas

- Usa “wrappers visuais” (cards prontos) para:
  - Linguagens mais usadas.
  - Commits / streaks.
- Normalmente via imagens geradas por serviços externos (ex.: GitHub Readme Stats, etc.).

### EmailJS – Formulário de Contato

- Implementação **serverless**, sem backend próprio.
- Envio:
  - Serviço (`EMAILJS_SERVICE_ID`)
  - Template (`EMAILJS_TEMPLATE_ID`)
  - Chave pública (`EMAILJS_PUBLIC_KEY`)
- Vantagens:
  - Não expõe credenciais de SMTP no frontend.
  - Simples de integrar com formulários em React.

---

## UX, Acessibilidade e Animações

- **Acessibilidade (a11y)**
  - Uso de elementos semânticos (`header`, `main`, `section`, etc.).
  - Navegação por teclado em:
    - Paleta de Comandos.
    - Modais.
  - Feedback visual de foco.

- **Dark Mode**
  - Persistência de escolha no `localStorage`.
  - Respeito ao tema padrão do sistema.

- **Animações**
  - Keyframes customizados (ex.: `animate-marquee`, `fade-in`, `fade-out`).
  - Entrada suave das seções conforme scroll.

---

## Estrutura do Código

> Observação: todo o projeto pode estar em um único arquivo principal (ex.: `src/App.jsx` ou similar), mas internamente o código é organizado em blocos lógicos.

Estrutura lógica (dentro do arquivo principal):

1. **Constantes e Configurações Globais**
   - URLs de imagem de perfil.
   - Link para currículo.
   - IDs do EmailJS.
   - Usuário do GitHub.
   - Chaves/usuário do Last.fm.
   - Coordenadas padrão de clima.

2. **Sistema de Tradução (`translations`)**
   - Objetos `pt` e `en` com textos organizados por seção.

3. **Hooks Customizados**
   - `useSEO`, `useOnScreen`, `useDelayUnmount`, `useKonamiCode`, `useLastFm`, `useWeather`.

4. **Componentes de UI e Layout**
   - `InfiniteMarquee`, `AnimatedSection`, `Documentation`, `CommandPalette`, etc.

5. **Componente Principal**
   - Gerencia:
     - Idioma atual.
     - Tema (dark/light).
     - Estados de modais (docs, galeria, etc.).
     - Abertura/fechamento da Command Palette.
   - Renderiza seções na ordem:
     - Hero, Sobre, Skills, Experiência, Educação, GitHub, Portfólio, Contato, Footer.

---

## Configuração de Variáveis/API Keys

As seguintes configurações são necessárias (podem ser constantes no código ou variáveis de ambiente, conforme sua preferência):

- **EmailJS**
  - `EMAILJS_SERVICE_ID`
  - `EMAILJS_TEMPLATE_ID`
  - `EMAILJS_PUBLIC_KEY`

- **Last.fm**
  - `LASTFM_API_KEY`
  - `LASTFM_USERNAME`

- **Clima (Open-Meteo)**
  - Coordenadas padrão:
    - `DEFAULT_WEATHER_LAT`
    - `DEFAULT_WEATHER_LON`
    - `DEFAULT_CITY_NAME`

- **GitHub**
  - `GITHUB_USERNAME`

> Nunca exponha chaves sensíveis em repositórios públicos. Caso necessário, use variáveis de ambiente e ferramentas de build para injetá-las em tempo de compilação.

---

## Boas Práticas e Decisões de Design

- Uso de **hooks nativos do React** ao invés de bibliotecas externas de gerenciamento de estado, pois o escopo da aplicação não exige algo mais complexo.
- Arquitetura baseada em componentes pequenos e focados, facilitando manutenção e reuso.
- Separação clara entre:
  - Lógica (hooks).
  - Apresentação (componentes de UI).
  - Conteúdo de texto (traduções i18n).
- Integrações externas encapsuladas em hooks (`useLastFm`, `useWeather`) para evitar espalhar chamadas de API pela árvore de componentes.

---

## Roadmap / Próximos Passos

- [ ] Adicionar mais idiomas (ex.: ES).
- [ ] Criar sistema de blog/postagens dentro do portfólio.
- [ ] Exportar componentes para uma estrutura de pastas mais granular.
- [ ] Adicionar testes unitários (ex.: Vitest, Testing Library).
- [ ] Integrar analytics (ex.: Google Analytics, Plausible).

---

## Licença

Este projeto está sob a licença **MIT**.  
Sinta-se à vontade para utilizar como base, estudar o código e adaptar para o seu próprio portfólio.
