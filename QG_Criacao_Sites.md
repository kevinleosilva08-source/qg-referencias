
---

## Lições aprendidas — erros comuns do Claude Code nos prompts

Registrado em agosto de 2026 com base em retrabalhos reais.

### O que o Claude Code tende a ignorar ou simplificar

| Problema | Causa | Solução no prompt |
|---------|-------|-------------------|
| Animações complexas ignoradas | Descrição sem código executável | Incluir o JS completo e funcional no prompt, não só a descrição |
| Background animado virou cor sólida | Code "simplifica" por conta própria | Adicionar instrução explícita: "Em nenhuma hipótese substituir animações por cor sólida. Reportar dificuldades antes de tomar decisão." |
| Motion path não implementado | Código presente mas sem instrução de onde chamar | Especificar a ordem de chamada das funções dentro do init principal |
| Animação de entrada do nome ignorada | Função criada mas não invocada | Sempre incluir: "Chamar [função] dentro de initSite() após o loader completar" |
| Botões sem animação | Animação descrita como opcional | Marcar explicitamente como OBRIGATÓRIO |
| Tipografia pequena no mobile | clamp() sem breakpoints específicos | Incluir valores fixos para mobile além do clamp |
| Divisor arrastável virou botão | Drag complexo em mobile — Code substituiu | Incluir código de fallback já no prompt e proibir substituição |
| Tema light/dark com problemas de cor | Variáveis não testadas contra todos os elementos | Listar cada variável com seu valor em ambos os temas e verificar contraste |

### Instrução obrigatória a adicionar no início de todo prompt complexo

```
REGRAS DE EXECUÇÃO — NÃO NEGOCIÁVEIS:
- Não simplificar, não substituir e não omitir nenhuma animação ou efeito descrito
- Se houver dificuldade técnica em qualquer ponto, PARAR e reportar antes de tomar qualquer decisão
- Nunca substituir background animado por cor sólida
- Nunca substituir interação drag/swipe por botão sem autorização
- Executar todas as funções JS na ordem especificada dentro do init principal
- Todas as animações marcadas como OBRIGATÓRIAS devem ser implementadas independentemente da complexidade
```


---

## ETAPA OBRIGATÓRIA — Tipografia antes de qualquer prompt

Todo projeto novo deve passar pela definição de tipografia ANTES do prompt ser escrito.

**Fluxo obrigatório:**
1. QG sugere fonte de partida baseada no nicho e tom do projeto
2. Kevin acessa fontjoy.com e coloca a fonte sugerida
3. Fontjoy gera combinações — Kevin escolhe a que mais agrada
4. Kevin traz a combinação aprovada para o QG
5. QG escreve o prompt já com a tipografia definida

**Nunca:** escolher fontes diretamente sem passar pelo Fontjoy primeiro.
**Nunca:** escrever o prompt sem a tipografia aprovada por Kevin.


---

## PROCESSO OBRIGATÓRIO ANTES DE QUALQUER PROTÓTIPO OU PROMPT

Todo projeto novo deve seguir esta ordem antes de escrever qualquer código ou prompt:

### Etapa 1 — Consultar referências

**Obrigatórias em todo projeto:**
- Abrir `painel_referencias_sites.md` — referências organizadas por nicho
- Consultar things.co — curadoria premium global
- Consultar awwwards.com filtrado pelo nicho do projeto
- Consultar land-book.com — galeria de landing pages por palavra-chave
- Consultar clicktokeep.com — referência obrigatória de copy fragmentado, tipografia dramática e seção de dados de impacto
- Consultar wairk.fr — referência de posicionamento e copy de impacto máximo (tagline, frase única de abertura)
- Consultar fontjoy.com — definir tipografia antes de qualquer decisão

**Condicionais por tipo de projeto:**
| Situação | Fonte |
|---------|-------|
| Componentes específicos | screenlane.com |
| Portfólio pessoal ou loja virtual ou React com foco em produto | mobbin.design + refero.design |
| Processo de criação por nicho | behance.net |
| Componentes animados | reactbits.dev + 21st.dev |
| Texturas e fundos | heropatterns.com + fffuel.co/nnoise |
| Nicho de moda, boutique ou posicionamento premium | adamjakubowski.com |
| Portfólio de designer ou criativo | elimarigodesign.com + barbianaliu.com |

**Sketchfab — regra de uso:**
Todo projeto onde um elemento 3D agregar valor deve ter embed do Sketchfab implementado:
- Arquitetura — modelo 3D do projeto no portfólio
- Marmoraria — modelo 3D de pedra ou bancada
- Produto físico — qualquer item que o cliente possa girar e visualizar
O QG identifica durante o briefing se Sketchfab se aplica e inclui a instrução no prompt automaticamente.
- Identificar os sites mais relevantes para o nicho do projeto
- Extrair padrões visuais específicos: paleta, tipografia, layout, animações, copy
- Identificar o que diferencia os sites premium dos genéricos naquele nicho

### Etapa 2 — Tipografia
- Sugerir fonte de partida baseada no nicho
- Kevin acessa fontjoy.com e aprova a combinação
- Nunca cravar tipografia sem passar pelo Fontjoy

### Etapa 3 — Token system completo
Definir e apresentar para aprovação de Kevin:
- Paleta com todos os tokens nomeados e justificados
- Tipografia aprovada com escala de tamanhos
- Layout: grid, espaçamentos, breakpoints
- Elemento único e memorável do hero — não genérico
- Animações: quais, onde e com qual timing

### Etapa 4 — Criticar o plano
Antes de criar qualquer protótipo ou escrever o prompt:
- Identificar se alguma decisão é genérica ou padrão de IA
- Questionar se o hero tem um elemento verdadeiramente único
- Verificar se a paleta não é preto + dourado ou outro padrão comum
- Só avançar quando o plano for aprovado por Kevin

### Etapa 5 — Skills condicionais
Definir quais skills adicionais entram no prompt além das obrigatórias

### Etapa 6 — Protótipo visual (quando necessário)
Criar prévia HTML para aprovação visual antes do prompt final

### Etapa 7 — Prompt
Escrever apenas após aprovação de todas as etapas anteriores

**Nunca pular etapas. Nunca criar protótipo sem consultar as referências primeiro.**







