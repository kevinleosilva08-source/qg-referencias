# Ferramentas e Skills — Claude Code
## Versão atualizada em agosto 2026 — 66 skills + 5 MCPs

---

## BLOCO OBRIGATÓRIO — INÍCIO DE TODO PROMPT DE SITE

Copiar e colar no início de QUALQUER prompt de criação ou alteração de site:

```
ANTES DE COMEÇAR — leia as seguintes skills nesta ordem e aplique todas as diretrizes encontradas durante toda a execução:

1. cat "/c/Users/Kevin/.claude/Work/.claude/skills/design-taste-frontend"
2. cat "/c/Users/Kevin/.claude/Work/.claude/skills/ui-styling"
3. cat "/c/Users/Kevin/.claude/Work/.claude/skills/design"
4. cat "/c/Users/Kevin/.claude/Work/.claude/skills/design-system"
5. cat "/c/Users/Kevin/.claude/Work/.claude/skills/banner-design"
6. cat "/c/Users/Kevin/.claude/Work/.claude/skills/find-animation-opportunities"
7. cat "/c/Users/Kevin/.claude/Work/.claude/skills/animation-vocabulary"
8. cat "/c/Users/Kevin/.claude/Work/.claude/skills/ui-ux-pro-max"
9. cat "/c/Users/Kevin/.claude/Work/.claude/skills/theme-factory"
10. cat "/c/Users/Kevin/.claude/Work/.claude/skills/emil-design-eng"
```

Exceção: cardápios e portfólios puramente expositivos — omitir `ui-ux-pro-max`.

---

## BLOCO OBRIGATÓRIO — FINAL DE TODO PROMPT (antes do deploy)

```
ANTES DO DEPLOY — executar nesta ordem:

1. cat "/c/Users/Kevin/.claude/Work/.claude/skills/review-animations"
   Revisar criticamente todas as animações implementadas.

2. cat "/c/Users/Kevin/.claude/Work/.claude/skills/improve-animations"
   Refinar e melhorar as animações após a revisão.

3. cat "/c/Users/Kevin/.claude/Work/.claude/skills/modern-web-design"
   Verificar qualidade geral do design contra princípios modernos.

4. cat "/c/Users/Kevin/.claude/Work/.claude/skills/web-design-guidelines"
   Auditar HTML e CSS contra as diretrizes da Vercel.

5. cat "/c/Users/Kevin/.claude/Work/.claude/skills/webapp-testing"
   Testar o site no browser — responsividade (375px, 768px, 1280px),
   botões, links, animações e performance. Corrigir tudo antes do commit.
```

---

## REGRAS DE EXECUÇÃO — NÃO NEGOCIÁVEIS

- Nunca simplificar, substituir ou omitir animações descritas no prompt
- Se houver dificuldade técnica, PARAR e reportar antes de tomar decisão
- Nunca usar cor sólida lisa onde foi pedida textura ou animação
- Nunca criar hero com foto + overlay escuro + headline centralizada + dois botões genéricos
- Nunca usar preto puro (#000000) como cor principal
- Todas as animações devem funcionar em mobile — nunca depender de hover
- Reportar erros de build antes de fazer commit

---

## SKILLS CONDICIONAIS — QG decide durante o briefing

O QG identifica e inclui automaticamente as skills condicionais no prompt. Kevin não precisa lembrar.

### Animação e Scroll
| Skill | Quando incluir |
|-------|---------------|
| `gsap-scrolltrigger` | Todo site premium — scroll cinematográfico, elementos que aparecem ao rolar, seção de processo com linha SVG |
| `locomotive-scroll` | Junto com GSAP em todo site premium — scroll suave que eleva a qualidade percebida |
| `animejs` | Sempre que houver SVG animado — balança, linha de processo, ícones vetoriais |
| `lottie-animations` | Sempre que houver ícones animados ou ilustrações em loop — alternativa ao SVG manual |
| `rive-interactive` | Quando o elemento principal do hero for animado — balança, mascote, ícone interativo |
| `scroll-reveal-libraries` | Sites HTML/CSS/JS simples sem GSAP — AOS ou ScrollReveal para reveals básicos |
| `barba-js` | Sites com múltiplas páginas — transições suaves entre páginas |

### 3D e Efeitos Visuais
| Skill | Quando incluir |
|-------|---------------|
| `lightweight-3d-effects` | Sempre que o briefing pedir fundo diferente de cor sólida — Vanta.js, Vanilla Tilt, Zdog |
| `threejs-webgl` | Hero 3D ou portfólio com cena 3D interativa |
| `spline-interactive` | Cena 3D exportada do Spline — portfólio pessoal |
| `react-three-fiber` | Projetos React que precisam de 3D com física |
| `web3d-integration-patterns` | Combinar Three.js + GSAP + R3F no mesmo projeto |
| `algorithmic-art` | Fundo visual único gerado por código — arte generativa |

### React e Componentes
| Skill | Quando incluir |
|-------|---------------|
| `motion-framer` | Projetos React com animações de layout e gestos |
| `animated-component-libraries` | Projetos React — Magic UI e React Bits para componentes premium |
| `react-spring-physics` | Animações React com bounce e inércia natural — cards, modais |
| `web-artifacts-builder` | Componentes React complexos — carrosséis, modais avançados |
| `pick-ui-library` | Início de projetos React — escolher a biblioteca mais adequada |

### Identidade e Branding
| Skill | Quando incluir |
|-------|---------------|
| `brand` | Cliente tem identidade visual definida (logo, cores, tipografia) |
| `brand-guidelines` | Aplicar diretrizes de marca com consistência em todo o projeto |
| `apple-design` | Visual minimalista premium estilo Apple |

### Material Gráfico
| Skill | Quando incluir |
|-------|---------------|
| `canvas-design` | Banners, posters e material gráfico para Instagram ou cliente |
| `slack-gif-creator` | GIF animado de imagem — stories e posts leves |

### Vídeo (serviço separado)
| Skill | Quando incluir |
|-------|---------------|
| `website-to-video` | Gravar o site funcionando para apresentar ao cliente |
| `motion-graphics` | Criar animações de motion para posts e stories |
| `slideshow` | Slideshow animado de projetos para apresentação |
| `general-video` | Edição geral de vídeo |
| `motion-graphics` | Motion design para conteúdo do Instagram |
| `embedded-captions` | Legendas automáticas em vídeos |

---

## GRUPO 1 — UI/UX Pro Max (7 skills)
**Origem:** ui-ux-pro-max-cli

| Skill | Status | Quando usar |
|-------|--------|------------|
| `ui-ux-pro-max` | ✅ Obrigatória | Todo site de cliente com CTA — exceção: cardápios e portfólios expositivos |
| `design` | ✅ Obrigatória | Diretrizes gerais de design — ler no início de todo projeto |
| `design-system` | ✅ Obrigatória | Entra no bloco padrão — consistência visual em qualquer projeto |
| `brand` | ⚡ Condicional | Cliente com identidade visual definida |
| `banner-design` | ✅ Obrigatória | Entra no bloco padrão — hero, CTAs e banners |
| `ui-styling` | ✅ Obrigatória | Estilização de qualquer componente UI |
| `slides` | 📎 Específico | Apresentações e decks — não sites |

---

## GRUPO 2 — HyperFrames / Vídeo (20 skills)
**Origem:** heygen-com/hyperframes
**Não usar em criação de sites HTML/CSS/JS**

Skills ativas para o serviço de vídeo e conteúdo:
`general-video` · `motion-graphics` · `slideshow` · `website-to-video` · `embedded-captions` · `media-use` · `music-to-video` · `product-launch-video` · `faceless-explainer` · `talking-head-recut`

Skills de framework interno (não usar diretamente):
`hyperframes` · `hyperframes-animation` · `hyperframes-cli` · `hyperframes-core` · `hyperframes-creative` · `hyperframes-keyframes` · `hyperframes-registry` · `remotion-to-hyperframes` · `figma` · `pr-to-video`

---

## GRUPO 3 — Design Taste Frontend (1 skill)
| Skill | Status |
|-------|--------|
| `design-taste-frontend` | ✅ Obrigatória em todo projeto de site |

---

## GRUPO 4 — Emil Kowalski (7 skills)
| Skill | Status | Quando usar |
|-------|--------|------------|
| `emil-design-eng` | ✅ Obrigatória | Framework de animação profissional |
| `animation-vocabulary` | ✅ Obrigatória | Nomear animações antes de implementar |
| `find-animation-opportunities` | ✅ Obrigatória | Identificar onde animar |
| `improve-animations` | ✅ Final obrigatório | Refinar após gerar |
| `review-animations` | ✅ Final obrigatório | Revisão crítica antes do deploy |
| `apple-design` | ⚡ Condicional | Visual minimalista premium |
| `pick-ui-library` | ⚡ Condicional | Início de projetos React |

---

## GRUPO 5 — Claude Design Skills / 3D (23 skills)

### Core 3D
| Skill | Status | Quando usar |
|-------|--------|------------|
| `threejs-webgl` | ⚡ Condicional | Hero 3D, portfólio com cena 3D |
| `gsap-scrolltrigger` | ⚡ Condicional | Todo site premium com scroll cinematográfico |
| `react-three-fiber` | ⚡ Condicional | React + 3D com física |
| `motion-framer` | ⚡ Condicional | Animações React com Framer Motion |
| `babylonjs-engine` | ⚡ Condicional | Experiências 3D complexas |

### Scroll e Transições
| Skill | Status | Quando usar |
|-------|--------|------------|
| `locomotive-scroll` | ⚡ Condicional | Scroll suave premium — junto com GSAP |
| `barba-js` | ⚡ Condicional | Sites multi-página — transições de página |
| `lightweight-3d-effects` | ⚡ Condicional | Fundos animados sem Three.js — Vanta.js |
| `scroll-reveal-libraries` | ⚡ Condicional | Sites simples sem GSAP |

### Componentes e Animações
| Skill | Status | Quando usar |
|-------|--------|------------|
| `animated-component-libraries` | ⚡ Condicional | React com Magic UI / React Bits |
| `animejs` | ⚡ Condicional | SVG animado, ícones vetoriais |
| `lottie-animations` | ⚡ Condicional | Ícones e ilustrações animadas em loop |
| `react-spring-physics` | ⚡ Condicional | Física em animações React |
| `rive-interactive` | ⚡ Condicional | Elemento principal do hero animado |
| `pixijs-2d` | ⚡ Condicional | Partículas 2D e jogos |
| `aframe-webxr` | ⚡ Condicional | Experiências VR/AR |

### 3D Authoring
| Skill | Status | Quando usar |
|-------|--------|------------|
| `spline-interactive` | ⚡ Condicional | Cena 3D do Spline no portfólio |
| `rive-interactive` | ⚡ Condicional | Animações interativas vetoriais |
| `blender-web-pipeline` | ⚡ Condicional | Modelos 3D customizados GLTF/GLB |
| `substance-3d-texturing` | ⚡ Condicional | Texturas PBR realistas |

### Meta-Skills
| Skill | Status | Quando usar |
|-------|--------|------------|
| `web3d-integration-patterns` | ⚡ Condicional | Combinar Three.js + GSAP + R3F |
| `modern-web-design` | ✅ Final obrigatório | Revisão de qualidade antes do deploy |
| `algorithmic-art` | ⚡ Condicional | Fundo visual único gerado por código |

---

## GRUPO 6 — Anthropic Official (8 skills)
| Skill | Status | Quando usar |
|-------|--------|------------|
| `webapp-testing` | ✅ Final obrigatório | Testar o site antes de todo deploy |
| `theme-factory` | ✅ Obrigatória | Gerar sistema de design no início |
| `web-design-guidelines` | ✅ Final obrigatório | Auditar contra diretrizes da Vercel |
| `web-artifacts-builder` | ⚡ Condicional | Componentes React complexos |
| `canvas-design` | ⚡ Condicional | Banners e material gráfico |
| `slack-gif-creator` | ⚡ Condicional | GIF animado de imagem |
| `algorithmic-art` | ⚡ Condicional | Arte generativa como fundo |
| `brand-guidelines` | ⚡ Condicional | Cliente com identidade visual própria |

---

## MCPs ATIVOS

### Claude Desktop
| MCP | Status | O que faz |
|-----|--------|----------|
| `mcp-server-firecrawl` | ✅ Ativo | Scraping e pesquisa web |
| `shadcn-ui` | ✅ Ativo | Componentes shadcn prontos para React |
| `magic-mcp` (21st.dev) | ✅ Ativo | Componentes animados premium |
| `playwright` | ✅ Ativo | Testes automatizados de browser |
| `minimax` | ⏸ Pendente | Geração de imagem e vídeo |
| `google-search-console` | ⏸ Pendente | Monitoramento de SEO |

### Claude Code (global)
| MCP | Status | O que faz |
|-----|--------|----------|
| `chrome-devtools` | ✅ Ativo | Inspeciona console, rede e performance |

---

## FLUXO DE USO DAS SKILLS POR TIPO DE PROJETO

### Site HTML/CSS/JS de cliente (advocacia, estética, restaurante)
**Início:** design-taste-frontend + ui-styling + design + design-system + banner-design + find-animation-opportunities + animation-vocabulary + ui-ux-pro-max + theme-factory + emil-design-eng
**Condicionais comuns:** gsap-scrolltrigger + locomotive-scroll + animejs + lottie-animations + lightweight-3d-effects
**Final:** review-animations + improve-animations + modern-web-design + web-design-guidelines + webapp-testing

### Site React de cliente (arquitetura, loja virtual)
**Início:** bloco padrão completo + pick-ui-library
**Condicionais comuns:** motion-framer + animated-component-libraries + react-spring-physics + barba-js
**Final:** bloco final completo

### Portfólio pessoal kevinleonardo.ia (React + 3D)
**Início:** bloco padrão completo + pick-ui-library
**Condicionais:** threejs-webgl + spline-interactive + web3d-integration-patterns + gsap-scrolltrigger + locomotive-scroll + motion-framer + animated-component-libraries
**Final:** bloco final completo

### Cardápio digital
**Início:** design-taste-frontend + ui-styling + design + design-system + find-animation-opportunities + animation-vocabulary + theme-factory + emil-design-eng
*(sem ui-ux-pro-max — foco em informação, não conversão)*
**Final:** bloco final completo

### Material gráfico / banners
**Skills:** canvas-design + brand (se cliente tiver identidade)

### Vídeo e conteúdo
**Skills:** website-to-video + motion-graphics + slideshow + embedded-captions

---

## TOTAL DE SKILLS: 66
*Última atualização: agosto 2026*
