# CLAUDE.md — Regras Globais de Kevin Leonardo
# Este arquivo é lido automaticamente pelo Claude Code em todo projeto

---

## IDENTIDADE DO PROJETO

Sou Kevin Leonardo, freelancer de soluções digitais em Anápolis-GO.
Crio sites premium para pequenas e médias empresas locais.
Stack principal: HTML/CSS/JS, React, Vercel, GitHub.

---

## REGRAS DE EXECUÇÃO — NÃO NEGOCIÁVEIS

- Nunca simplificar, substituir ou omitir animações descritas no prompt
- Se houver dificuldade técnica, PARAR e reportar antes de tomar qualquer decisão
- Nunca usar preto puro (#000000) como cor principal
- Nunca substituir fundo animado ou texturizado por cor sólida
- Nunca criar hero com foto + overlay escuro + headline centralizada + dois botões genéricos
- Reportar qualquer erro de TypeScript ou build antes de fazer commit
- Nunca fazer deploy sem executar as verificações finais listadas abaixo

---

## SKILLS OBRIGATÓRIAS — LER NO INÍCIO DE TODO PROJETO DE SITE

Antes de escrever qualquer linha de código, ler as seguintes skills nesta ordem:

1. cat "/c/Users/Kevin/.claude/Work/.claude/skills/design-taste-frontend"
2. cat "/c/Users/Kevin/.claude/Work/.claude/skills/ui-styling"
3. cat "/c/Users/Kevin/.claude/Work/.claude/skills/design"
4. cat "/c/Users/Kevin/.claude/Work/.claude/skills/find-animation-opportunities"
5. cat "/c/Users/Kevin/.claude/Work/.claude/skills/ui-ux-pro-max"
6. cat "/c/Users/Kevin/.claude/Work/.claude/skills/theme-factory"
7. cat "/c/Users/Kevin/.claude/Work/.claude/skills/emil-design-eng"

Exceção: cardápios digitais e portfólios puramente expositivos — omitir ui-ux-pro-max.

---

## SKILLS CONDICIONAIS — ATIVAR CONFORME O PROJETO

Ler apenas quando o projeto exigir:

| Situação | Skill a ler |
|---------|------------|
| Cliente tem identidade visual definida (logo, cores, tipografia) | brand-guidelines |
| Projeto precisa de fundo visual único gerado por código | algorithmic-art |
| Scroll cinematográfico | gsap-scrolltrigger |
| Scroll suave premium | locomotive-scroll |
| Hero 3D ou cena 3D | threejs-webgl |
| Cena 3D exportada do Spline | spline-interactive |
| Componentes React complexos | web-artifacts-builder |
| Animações React com Framer Motion | motion-framer |
| Banners, posters, material gráfico | canvas-design |
| GIF animado de imagem | slack-gif-creator |
| Visual minimalista premium estilo Apple | apple-design |
| Revisão de animações após gerar o site | review-animations |
| Refinamento de animações | improve-animations |

---

## VERIFICAÇÕES FINAIS — EXECUTAR ANTES DE TODO DEPLOY

Após finalizar o desenvolvimento, executar nesta ordem:

### 1. Auditoria de design — web-design-guidelines
```
use a skill web-design-guidelines para auditar todos os arquivos HTML e CSS do projeto
corrija todos os problemas de acessibilidade, contraste e UX encontrados antes de continuar
```

### 2. Teste automatizado — webapp-testing
```
use a skill webapp-testing para abrir o site no browser e testar:
- responsividade em mobile (375px), tablet (768px) e desktop (1280px)
- todos os botões e links funcionando
- animações rodando corretamente
- nenhum elemento cortado ou sobreposto
corrija tudo antes de fazer o deploy
```

### 3. Checklist manual — confirmar antes do commit
- [ ] Header sempre visível em todas as páginas
- [ ] Nenhuma animação foi substituída por cor sólida
- [ ] Botões não são retângulos genéricos sem animação
- [ ] Nenhuma seção com cor de fundo lisa sem textura
- [ ] Tipografia com hierarquia clara — h1, h2, h3 bem definidos
- [ ] Imagens com alt text descritivo
- [ ] WhatsApp, e-mail e Instagram clicáveis e funcionando
- [ ] sitemap.xml e robots.txt presentes
- [ ] llms.txt presente na raiz

### 4. Build sem erros
```
npm run build
```
Se houver erros TypeScript, corrigir antes do commit.

### 5. Commit e deploy
```
git add -A
git commit -m "feat: [descrição do que foi feito]"
git push
```
A Vercel publica automaticamente após o push.

---

## PADRÃO DE QUALIDADE VISUAL

Todo site criado deve:
- Ter identidade visual única — não ser reconhecível como site gerado por IA
- Usar textura de fundo em todas as seções — nunca cor sólida lisa
- Ter animações contínuas que funcionam no mobile sem depender de hover
- Ter tipografia com hierarquia clara e personalidade — não fontes padrão sem motivo
- Ter pelo menos um elemento visual único e memorável no hero
- Copy sempre em primeira pessoa do cliente — nunca plural corporativo genérico

---

*Arquivo criado em agosto de 2026 — Kevin Leonardo · kevinleonardo.digital*

---

## COMO ESTUDAR AS SKILLS — NÃO APENAS LER

Para cada skill do bloco obrigatório, ANTES de escrever qualquer código:

1. Leia a skill completa
2. Documente em comentário no topo do arquivo HTML/CSS:
   ```
   /* SKILL: [nome]
      Princípios aplicados a ESTE projeto:
      1. [princípio específico] → aplicado em [onde]
      2. [princípio específico] → aplicado em [onde]
      3. [princípio específico] → aplicado em [onde]
      Proibições para ESTE projeto:
      - [o que NÃO fazer aqui]
   */
   ```
3. Só avance para a próxima skill após documentar
4. Só comece a codar após documentar TODAS as skills do bloco

## DUAS PASSAGENS OBRIGATÓRIAS

**Passagem 1 — Planejar:**
Após ler todas as skills, declarar o plano completo antes de codar:
- Token system (cores, tipografia, espaçamentos)
- Mapa de animações por seção (tipo, timing, gatilho)
- Lista negra de padrões genéricos identificados e como evitar

**Passagem 2 — Executar:**
Só após o plano estar completo, escrever o código seguindo exatamente o plano.
Nunca simplificar uma animação descrita no plano — parar e reportar se houver dificuldade.
