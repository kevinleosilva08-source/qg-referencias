# Registro de Animações, Tipografias e Elementos Visuais por Projeto

Este arquivo documenta o que foi usado em cada site criado no QG.
Objetivo: evitar repetição entre projetos e servir como material de aprendizado sobre nomenclatura técnica de animações e tipografia.

---

## GLOSSÁRIO RÁPIDO DE TERMOS

| Termo | O que é |
|-------|---------|
| **Scroll Reveal** | Elemento aparece quando entra na viewport ao rolar a página |
| **Fade In** | Elemento aparece gradualmente do invisível ao visível (opacity 0 → 1) |
| **Translate Y** | Elemento sobe ou desce enquanto aparece |
| **Clip-path Reveal** | Uma "cortina" recorta o elemento, revelando-o progressivamente |
| **Split Reveal** | Texto parte do centro para os lados ao aparecer |
| **Shimmer** | Faixa de luz atravessa o elemento continuamente da esquerda para a direita |
| **Pulse** | Elemento expande e contrai suavemente em loop (usado em botões e ícones) |
| **Aurora** | Blobs de cor com blur que flutuam lentamente no fundo |
| **Grain / Noise** | Textura granulada aplicada sobre o fundo para dar profundidade |
| **Parallax** | Elemento se move em velocidade diferente do scroll da página |
| **Counter Animation** | Número sobe de zero até o valor final ao entrar na viewport |
| **Stroke Animation** | Borda desenhada progressivamente ao redor de um elemento no hover |
| **Fill Reveal** | Preenchimento de cor sobe de baixo para cima (ou de qualquer direção) no hover |
| **Radial Ripple** | Luz nasce do centro e se expande para fora no hover |
| **Easing** | Curva de velocidade da animação (ex: cubic-bezier — começa lento, acelera, desacelera) |
| **Cubic-bezier** | Fórmula matemática que define o ritmo da animação. (.22,1,.36,1) = entrada suave, saída rápida |
| **Typeface / Fonte Display** | Fonte usada nos títulos grandes, com personalidade visual forte |
| **Typeface / Fonte Body** | Fonte usada no corpo do texto, priorizando leitura fluida |
| **Grainient** | Gradiente com grain fotográfico sobreposto — textura que parece pele ou papel envelhecido |
| **Soft Aurora** | Versão suave do efeito aurora, com blobs de baixa opacidade flutuando no fundo |
| **Marquee** | Elemento desliza horizontalmente em loop contínuo (como letreiro) |
| **Masonry Grid** | Grade com itens de alturas variadas, como uma colagem |

---

## PROJETOS REGISTRADOS

---

### SITE 01 — Everest Marmoraria

**Nicho:** Marmoraria — Anápolis-GO
**Stack:** HTML/CSS/JS puro

#### Tipografia
| Papel | Fonte | Peso | Observação |
|-------|-------|------|------------|
| Display (títulos) | Cormorant Garamond | 300, 600 | Serifada elegante. Escolhida para o modelo original, substituída por Bebas Neue na v2 |
| Display v2 (títulos) | Bebas Neue | 400 (única) | Geométrica display, toda em caixa alta. Sem serifa, mais técnica e masculina |
| Corpo / UI | DM Sans | 400, 500, 600 | Geométrica limpa, excelente legibilidade |

#### Animações de entrada (Scroll Reveal)
| Seção | Animação | Técnica |
|-------|----------|---------|
| Todos os elementos | Scroll Reveal com Fade In + Translate Y | `opacity 0→1` + `translateY(30px→0)`, `cubic-bezier(.22,1,.36,1)` |
| Navbar ao carregar | Slide Down | `translateY(-100%→0)`, 0.6s |
| Hero — conteúdo | Fade In escalonado | Delay progressivo: label 0.3s, título 0.5s, subtítulo 0.7s, botões 0.9s |
| Footer — colunas | Fade In escalonado | Delay 0s, 0.15s, 0.3s por coluna |
| Linha divisória footer | Width Reveal | `width: 0%→100%`, 1s |
| Números de credibilidade | Counter Animation | Número sobe de 0 ao valor final via requestAnimationFrame |

#### Animações de botão
| Botão | Animação | Técnica |
|-------|----------|---------|
| CTA principal | Shimmer Dourado | `linear-gradient` com `background-position` animado, loop 2.5s |
| CTA secundário ("Ver Portfólio") | Fill Hover | Preenchimento dourado da esquerda para direita via `background-position` |
| Botão WhatsApp fixo | Pulse | `box-shadow` expandindo e sumindo em loop, 2.5s |

#### Animações de hover
| Elemento | Animação |
|----------|---------|
| Cards de serviço | `translateY(-4px)` + sombra dourada + borda --stone-gold |
| Fotos do portfólio | `scale(1.08)` + overlay escuro + ícone lupa |
| Card localização (footer) | `translateY(-2px)` + borda dourada + glow suave |
| Links do footer | `translateX(4px)` + cor dourada |
| Ícones sociais | Cor --stone-gold |

#### Fundo e textura
| Seção | Elemento visual |
|-------|----------------|
| Fundos claros | Noise grain em SVG inline (granulado fino) |
| Fundos escuros | Veios diagonais via `repeating-linear-gradient` em pseudo-elemento `::before` |
| Hero | Imagem Pexels full-bleed + overlay gradiente diagonal |

#### Lightbox (portfólio)
- Fade In ao abrir (opacity 0→1, 0.25s)
- Transição entre fotos: Fade (opacity 0→1, 0.2s)
- Navegação: setas ← →, swipe touch, ESC

---

### SITE 02 — Dra. Laryssa Valente

**Nicho:** Biomédica Esteta — Tratamento de Estrias — Anápolis-GO
**Stack:** HTML/CSS/JS puro

#### Tipografia
| Papel | Fonte | Peso | Observação |
|-------|-------|------|------------|
| Display (títulos) | Cormorant | 300, 400, 600 + italic | Serifada italiana com calor. Itálico nos títulos de seção |
| Corpo / UI | Jost | 300, 400, 500, 600 | Geométrica moderna, feminina sem ser infantil |
| Labels | Jost 500 | uppercase, letter-spacing 0.18em | |

#### Animações de entrada (Scroll Reveal)
| Seção | Animação | Técnica |
|-------|----------|---------|
| Todos os elementos | Scroll Reveal com Fade In + Translate Y | `opacity 0→1` + `translateY(24px→0)`, `cubic-bezier(.22,1,.36,1)`, 0.8s |
| Hero — conteúdo | Fade In escalonado | Delay progressivo por elemento |
| Grupos de elementos | Delay escalonado | `transition-delay: calc(var(--i, 0) * 0.1s)` via atributo inline |

#### Animações de botão
| Botão | Animação | Nome técnico | Técnica |
|-------|----------|-------------|---------|
| CTA principal `.btn-lv` | Radial Ripple | Luz do centro para fora | `::after` com `width/height 0→300px`, `border-radius: 50%`, `opacity 0→1` no hover |
| CTA secundário | Fill Hover | Preenchimento da esquerda | `background: #C9A47E` via transição |
| Botão WhatsApp fixo | Pulse cobre | Box-shadow em loop | `@keyframes lvPulse`, 3s ease infinite |

#### Animações de hover
| Elemento | Animação |
|----------|---------|
| Cards de serviço | `translateY(-6px)` + sombra + borda --lv-rose |
| Fotos da galeria | `scale(1.04)` + overlay + ícone expansão |
| Links do footer | `translateX(4px)` + cor --lv-rose |
| Card localização footer | `translateY(-3px)` + borda --lv-rose |

#### Fundo e textura
| Seção | Elemento visual |
|-------|----------------|
| Fundos claros | Padrão orgânico de círculos imperfeitos em SVG — remete à estrutura da pele em microscópio |
| Fundos escuros | Gradiente sólido sem textura |

#### Lightbox (galeria antes/depois)
- Fade In ao abrir (opacity 0→1, 0.3s)
- Swipe touch com threshold 50px
- Setas laterais + contador "2/6" + fechar com ESC

---

### SITE 03 — Dra. Carol Coelho

**Nicho:** Fisioterapeuta Dermatofuncional — Harmonização Facial e Corporal — Anápolis-GO
**Stack:** HTML/CSS/JS puro

#### Tipografia
| Papel | Fonte | Peso | Observação |
|-------|-------|------|------------|
| Display (títulos) | Libre Baskerville | 400, 700 + italic | Serifada editorial robusta. Mais técnica e clínica que Cormorant |
| Corpo / UI | Inter | 300, 400, 500, 600 | Mais clínica e neutra que Jost. Leitura precisa |
| Labels | Inter 600 | uppercase, letter-spacing 0.2em | |

#### Animações de entrada (Scroll Reveal)
| Seção | Animação | Técnica |
|-------|----------|---------|
| Imagens e blocos | Clip-path Reveal | `clip-path: inset(0 0 100% 0 → 0 0 0% 0)`, 0.9s — "cortina" que desce |
| Textos e UI | Fade In + Translate Y | `opacity 0→1` + `translateY(20px→0)`, 0.7s |
| Grupos | Delay escalonado | `transition-delay: calc(var(--i,0) * 0.12s)` |

#### Animações de botão
| Botão | Animação | Nome técnico | Técnica |
|-------|----------|-------------|---------|
| CTA principal `.btn-cc` | Stroke Animation | Borda desenhada no hover | `::before` e `::after` com `scaleX(0→1)` nas bordas top/bottom |
| CTA sólido `.btn-cc-light` | Fill Reveal diagonal | Preenchimento da esquerda | `::before` com `scaleX(0→1)` via `transform-origin: left` |
| Botão WhatsApp fixo | Pulse bordô | Box-shadow bordô em loop | `@keyframes ccPulse`, 3s ease infinite |

#### Animações de hover
| Elemento | Animação |
|----------|---------|
| Cards de serviço | Linha dourada crescendo na base (`width 0→100%`, 2px) + `translateY(-4px)` |
| Fotos | `scale(1.05)` + overlay + ícone expansão |
| Slider comparativo | Drag interativo com `clip-path` atualizado via JS |
| Card localização footer | Barra vertical bordô crescendo na lateral esquerda (`scaleY(0→1)`) + `translateX(4px)` |
| Carrossel depoimentos | Pause no hover via `mouseenter/mouseleave` |

#### Animações contínuas
| Elemento | Animação |
|----------|---------|
| Botão WhatsApp | Pulse contínuo |
| Carrossel depoimentos | Auto-play — avança 1 card a cada 4s |

#### Fundo e textura
| Seção | Elemento visual |
|-------|----------------|
| Fundos claros | Padrão de losangos geométricos em SVG — premium e sofisticado |
| Fundos escuros | Gradiente sólido sem textura adicional |

#### Componentes especiais
| Componente | Técnica |
|-----------|---------|
| Slider antes/depois | Clip-path drag com JS — `clip-path: inset(0 X% 0 0)` atualizado por mousemove/touchmove |
| Tabs de serviços | JS toggle de classe `active` com fade entre painéis |
| FAQ | Tabs laterais no desktop, accordion no mobile |

---

### SITE 04 — Dra. Renata Camapum Jorge

**Nicho:** Harmonização Facial — Goiânia-GO
**Stack:** HTML/CSS/JS puro

#### Tipografia
| Papel | Fonte | Peso | Observação |
|-------|-------|------|------------|
| Display (títulos) | Bodoni Moda | 400, 700 + italic | Serifada italiana de alto glamour. A mais sofisticada dos 4 projetos |
| Corpo / UI | DM Sans | 300, 400, 500, 600 | Geométrica limpa — a mesma da Everest mas com pesos diferentes e contexto premium |
| Labels | DM Sans 600 | uppercase, letter-spacing 0.2em | |

**Nota:** DM Sans aparece também na Everest, mas com Bodoni Moda como display o resultado visual é completamente diferente. Os pares de fontes definem a personalidade — não a fonte isolada.

#### Animações de entrada (Scroll Reveal)
| Seção | Animação | Nome técnico | Técnica |
|-------|----------|-------------|---------|
| Títulos | Split Reveal | Texto sobe de baixo do container | `translateY(100%→0)` dentro de `overflow: hidden` — o texto "nasce" de baixo |
| Blocos e imagens | Fade In + Translate Y | Mesma base, menos dramática | `opacity 0→1` + `translateY(16px→0)`, 0.8s |
| Grupos | Delay escalonado | `transition-delay: calc(var(--i,0) * 0.1s)` | |

#### Animações de botão
| Botão | Animação | Nome técnico | Técnica |
|-------|----------|-------------|---------|
| CTA principal `.btn-rc` | Fill Reveal vertical | Preenchimento cobre da base para cima | `::before` com `height: 0%→100%` via `cubic-bezier(.22,1,.36,1)` |
| CTA sólido `.btn-rc-solid` | Sheen / Glint | Reflexo diagonal passando | `::after` com `translateX(-100%→150%) skewX(-15deg)` |
| Botão WhatsApp fixo | Pulse + Rotate | Pulse + leve rotação no hover | `@keyframes rcPulse` 3.5s + `rotate(5deg)` no hover |

#### Animações de hover
| Elemento | Animação |
|----------|---------|
| Cards de serviço | Linha cobre crescendo na base + `translateY(-6px)` + borda sutil |
| Número ordinal nos cards | Aumenta opacity de 0.06 para 0.12 |
| Etapas do processo (timeline) | Círculo do número fica cobre sólido + `scale(1.1)` |
| Slider antes/depois | Drag interativo — igual ao da Carol mas com estilo cobre |
| Card localização footer | Barra cobre crescendo na lateral (`scaleY(0→1)`) + `translateX(4px)` |
| Links footer | `translateX(3px)` + cor --rc-copper |

#### Animações contínuas
| Elemento | Animação | Nome técnico |
|----------|---------|-------------|
| Fundo do hero | Soft Aurora | 3 blobs com `border-radius: 50%`, `filter: blur(80px)`, `@keyframes auroraFloat` em loop alternado — cada blob com duração diferente (14s, 18s, 16s) |
| Fundo do CTA final | Soft Aurora suave | Mesmos blobs com `opacity: 0.06` |
| Botão WhatsApp | Pulse cobre | Box-shadow em loop |

#### Fundo e textura
| Seção | Elemento visual |
|-------|----------------|
| Fundos claros | Grainient — grain fotográfico + gradiente linear sobreposto. Remete à textura da pele |
| Fundos escuros | Gradiente direcional com leve variação de tom (não completamente sólido) |
| Hero | Soft Aurora animada (3 blobs cobre/prata flutuando) |
| CTA final | Soft Aurora suave reutilizada |

#### Componentes especiais
| Componente | Técnica |
|-----------|---------|
| Slider antes/depois | Grid 2×2 simétrico com drag JS + clip-path |
| Timeline "Da consulta ao resultado" | Grid 4 colunas com linha conectora CSS + hover nos círculos |
| FAQ accordion | max-height animado + ícone que rotaciona 45° ao abrir |

---

### SITE 05 — Dr. Pedro Almeida

**Nicho:** Advocacia — Pensão alimentícia
**URL:** advogadopedroalmeida.com.br
**Stack:** HTML/CSS/JS puro

#### Tipografia
| Papel | Fonte | Observação |
|-------|-------|------------|
| Display (títulos) | Playfair Display | Serifada editorial clássica |
| Corpo / UI | Vesper Libre | Serifada de leitura, corpo e UI |

#### Paleta
`--slate: #1C2B3A` · `--amber: #B45309` · `--warm: #F8F5F0` · `--ink: #0F172A` · `--accent-on-dark: #E0A458`

#### Scripts ativos
| Biblioteca | Versão | Função |
|-----------|--------|--------|
| locomotive-scroll | 4.1.4 | Scroll suave (legado) |
| gsap | 3.12.5 | Animações de scroll |
| ScrollTrigger | 3.12.5 | Plugin GSAP |
| animejs | 3.2.2 | Elementos SVG |
| aos | 2.3.1 | Reveal adicional ⚠️ Redundante com GSAP |

⚠️ **Atenção:** AOS e GSAP usados simultaneamente — dois sistemas de scroll-reveal competindo. Ver aprendizado no SITE 07.

#### Animações de entrada
| Elemento | Animação | Técnica |
|----------|----------|---------|
| Elementos gerais | Scroll Reveal Fade In + Translate Y | `data-aos="fade-up"` |
| Hero — conteúdo | Fade In escalonado | Delay progressivo por elemento |

#### Fundo e textura
| Seção | Elemento visual |
|-------|----------------|
| Hero | Slate escuro com gradiente diagonal suave |
| Seções claras | Warm (`#F8F5F0`) com variações warm-alt e warm-deep |

---

### SITE 06 — Espaço Alfa

**Nicho:** Salão de Eventos
**URL:** espaco-alfa-two.vercel.app
**Stack:** HTML/CSS/JS puro

#### Tipografia
| Papel | Fonte | Observação |
|-------|-------|------------|
| Display (títulos) | Fraunces | Serifada orgânica, cálida — combina com o tom acolhedor do salão |
| Corpo / UI | Manrope | Geométrica moderna, legível |

#### Paleta
Verde Starbucks `#006241`, `#00754A`, `#1E3932` + creme `#f2f0eb`

#### Scripts ativos
| Biblioteca | Versão | Função |
|-----------|--------|--------|
| gsap | 3.12.5 | Animações de scroll |
| ScrollTrigger | 3.12.5 | Plugin GSAP |
| lenis | 1.1.14 | Scroll suave (Lenis — não legado) |

#### Animações de entrada
| Elemento | Animação |
|----------|---------|
| Elementos gerais | Scroll Reveal via GSAP ScrollTrigger + Fade In |
| Hero | Slideshow fullscreen automático de fotos do salão |
| Cards de diferenciais | Fade In escalonado com ícone verde centralizado |

#### Fundo e textura
| Seção | Elemento visual |
|-------|----------------|
| Seções claras | Creme `#f2f0eb` |
| Seções escuras | Verde Starbucks profundo |

---

### SITE 07 — Marmoraria Flinstones

**Nicho:** Marmoraria
**URL:** marmoraria-flinstones.vercel.app
**Stack:** HTML/CSS/JS puro

#### Tipografia
| Papel | Fonte | Observação |
|-------|-------|------------|
| Display (títulos) | Bebas Neue | Geométrica display, toda caixa alta — técnica e masculina (2º uso — ver Everest v2) |
| Corpo / UI | DM Sans | Geométrica limpa, excelente legibilidade |

#### Paleta
Grafite escuro `#1A1A1A` aprox + dourado `#B8962E` aprox + fundo mármore branco como textura

#### Scripts ativos
| Biblioteca | Versão | Função |
|-----------|--------|--------|
| lenis | 1.1.14 | Scroll suave |

**⚠️ GSAP removido em produção** — estava no prompt, mas bloqueado silenciosamente por ad-blocker via CDN. Solução aplicada: CSS transitions + IntersectionObserver nativo como base completa.

#### Animações de entrada
| Elemento | Animação |
|----------|---------|
| Elementos gerais | CSS transitions + IntersectionObserver (sem GSAP) |
| Cards de serviço | Fundo com textura real da pedra (Blue Bahia, Ônix Âmbar, etc.) |

#### Fundo e textura
| Seção | Elemento visual |
|-------|----------------|
| Fundo do site | Textura de mármore branco como background geral |
| Cards de serviço | Foto real da pedra como fundo do card (Quartzito Verde, Blue Bahia, Ônix Âmbar, Travertino) |

#### Aprendizado crítico — GSAP CDN
> GSAP carregado via CDN foi bloqueado silenciosamente por ad-blocker do cliente em produção — sem erro no console, sem fallback. Todas as animações falharam sem qualquer indicação visual. **Solução permanente:** CSS transitions + IntersectionObserver como camada base completa; GSAP apenas como progressive enhancement quando carregar.

---

### SITE 08 — Petshop Manda-chuva

**Nicho:** Petshop + Clínica Veterinária
**URL:** petshop-manda-chuva.vercel.app
**Stack:** HTML/CSS/JS puro

#### Paleta
Verde-água `#2BA8A8` + laranja `#FF6B35` + branco

#### Tipografia
A verificar via JS em próxima sessão.

#### Animações e estrutura visual
| Elemento | Animação / Característica |
|----------|--------------------------|
| Hero | Gato + cachorro sem fundo sobre base orgânica SVG |
| Transições de seção | Curva SVG obrigatória — nunca linha reta |
| Grid de diferenciais | 8 equipamentos com ícone + título |
| Depoimentos | Cards com float (não carrossel) |

---

### SITE 09 — Flash Estética Automotiva

**Nicho:** Estética Automotiva
**URL:** flash-estetica-automotiva.vercel.app
**Stack:** HTML/CSS/JS puro

#### Tipografia
| Papel | Fonte | Observação |
|-------|-------|------------|
| Display (títulos) | Bebas Neue | Geométrica display, toda caixa alta — 2º projeto a usar essa fonte (ver Flinstones) |
| Corpo | Sans-serif condensada | A confirmar via JS |

#### Paleta
Preto `#000000` (paleta BMW M via getdesign.md) + faixa tricolor M (azul/roxo/vermelho) como detalhe de header + dourado/âmbar em preços e CTAs secundários

**Nota:** Preto puro aprovado como exceção à regra global — justificado pela referência BMW M via `getdesign.md`.

#### Animações e estrutura visual
| Elemento | Característica |
|----------|---------------|
| Hero | Headline grande à esquerda + faixa tricolor no topo |
| Serviços | Layout alternado foto/texto por serviço |
| Antes e depois | Slider drag com 3 comparações (polimento, higienização, cerâmica) |
| Botão CTA principal | Branco sólido sobre preto |

---

## RESUMO DE DIVERSIDADE — O QUE JÁ FOI USADO

### Fontes display (títulos grandes)
| Fonte | Projeto | Personalidade |
|-------|---------|--------------|
| Cormorant Garamond | Everest v1 | Serifada elegante, neutra |
| Bebas Neue | Everest v2, Flinstones, Flash | Display geométrica, toda maiúscula, masculina — usada em 3 projetos |
| Cormorant (italic) | Laryssa | Serifada italiana com calor, feminina |
| Libre Baskerville | Carol | Serifada editorial robusta, clínica |
| Bodoni Moda | Renata | Serifada italiana de glamour, a mais sofisticada |
| Playfair Display | Dr. Pedro | Serifada editorial clássica, advocacia |
| Fraunces | Espaço Alfa | Serifada orgânica e cálida, eventos |

### Animações de entrada já usadas
- Fade In + Translate Y (universal — usar como base, variar com elementos adicionais)
- Slide Down (navbar)
- Clip-path Reveal (Carol — cortina descendo)
- Split Reveal (Renata — texto nasce de baixo)

### Animações de botão já usadas
- Shimmer dourado (Everest)
- Radial Ripple / Luz do centro (Laryssa)
- Stroke Animation / Borda desenhada (Carol)
- Fill Reveal vertical / Preenchimento de baixo para cima (Renata)

### Texturas de fundo já usadas
- Noise grain SVG (Everest — fundos claros)
- Veios diagonais repeating-linear-gradient (Everest — fundos escuros)
- Círculos orgânicos SVG (Laryssa — remete à pele)
- Losangos geométricos SVG (Carol — premium/sofisticado)
- Grainient fotográfico (Renata — fundos claros)

### Animações contínuas de fundo já usadas
- Soft Aurora com blobs CSS (Renata)

### Bibliotecas de scroll por projeto
| Projeto | Biblioteca | Versão |
|---------|-----------|--------|
| Everest | — | Sem scroll suave |
| Laryssa | — | Sem scroll suave |
| Carol | — | Sem scroll suave |
| Renata | — | Sem scroll suave |
| Dr. Pedro | locomotive-scroll (legado) | 4.1.4 |
| Espaço Alfa | Lenis | 1.1.14 |
| Flinstones | Lenis | 1.1.14 |
| Flash | A confirmar | — |
| Petshop | A confirmar | — |

**Regra:** A skill se chama `locomotive-scroll`, mas o código gerado usa **Lenis** (não o Locomotive legado). Lenis é a versão recomendada a partir de 2024.

### ⚠️ Aprendizado crítico — GSAP CDN
> GSAP carregado via CDN (`cdnjs.cloudflare.com`) pode ser bloqueado silenciosamente por ad-blocker em produção, sem nenhum erro no console. Todas as animações falham sem indicação visual. **Regra permanente:** sempre implementar CSS transitions + IntersectionObserver como camada base completa. GSAP entra como progressive enhancement por cima, se carregar.

### O QUE AINDA NÃO FOI USADO — próximos projetos
- Partículas (canvas ou biblioteca leve)
- Ondas SVG animadas
- Gradiente animado com hue-rotate
- Marquee / letreiro horizontal em loop
- Mouse parallax (elemento segue o cursor)
- Magnetic button (botão se aproxima do cursor)
- Text scramble / Glitch (texto embaralhado ao revelar)
- Morphing (formas que se transformam em loop)
- Spotlight cursor (holofote seguindo o mouse)
- Counter + sufixo animado
- Stagger reveal em letras individuais (não palavra inteira)
