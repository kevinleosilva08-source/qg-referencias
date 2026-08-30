# VERIFICAÇÃO E OTIMIZAÇÃO PÓS-DEPLOY
## Processo padrão para todo site publicado

---

## INSTRUÇÕES PARA O CLAUDE CODE

Cole este documento no Claude Code com a seguinte instrução:

```
Leia este documento e execute cada verificação no projeto atual, na ordem listada.
Para cada item, informe: ✅ OK, ❌ Faltando ou ⚠️ Precisa ajuste.
Ao final, liste tudo que precisa ser corrigido e peça autorização antes de alterar qualquer arquivo.
```

---

## PARTE 1 — VERIFICAÇÃO DE ARQUIVOS OBRIGATÓRIOS

### 1.1 Arquivos na raiz do projeto
- [ ] `index.html` — página principal existe
- [ ] `sitemap.xml` — mapa do site para o Google
- [ ] `llms.txt` — instruções para IAs (ChatGPT, Perplexity, Claude, Gemini)
- [ ] `.gitignore` — contém `.env` para proteger credenciais
- [ ] `robots.txt` — instruções para rastreadores do Google

**Se algum estiver faltando**, o Claude Code deve criá-lo com base nos dados do projeto.

**Modelo de robots.txt:**
```
User-agent: *
Allow: /
Sitemap: https://URL-DO-SITE/sitemap.xml
```

---

## PARTE 2 — VERIFICAÇÃO DE SEO

### 2.1 Meta tags no `<head>`
- [ ] `<title>` presente e contém palavra-chave principal
- [ ] `<meta name="description">` presente, até 160 caracteres, com palavra-chave
- [ ] `<meta name="keywords">` presente com pelo menos 3 palavras-chave
- [ ] `<meta name="robots" content="index, follow">` presente
- [ ] `<meta property="og:title">` presente (compartilhamento em redes sociais)
- [ ] `<meta property="og:description">` presente
- [ ] `<meta property="og:type" content="website">` presente
- [ ] `<meta charset="UTF-8">` presente
- [ ] `<meta name="viewport" content="width=device-width, initial-scale=1.0">` presente

### 2.2 Estrutura de headings
- [ ] Existe exatamente **um** `<h1>` por página
- [ ] Seções usam `<h2>`
- [ ] Subseções usam `<h3>`
- [ ] Nenhum heading está sendo usado apenas para estilo visual

### 2.3 Imagens
- [ ] Todas as imagens têm atributo `alt` descritivo e não vazio
- [ ] Nenhuma imagem tem `alt=""` ou `alt="image"` genérico
- [ ] Imagens pesadas têm `loading="lazy"`
- [ ] Imagem do hero tem `loading="eager"`

### 2.4 Links
- [ ] Links internos funcionando (sem 404)
- [ ] Links externos têm `target="_blank" rel="noopener noreferrer"`
- [ ] Nenhum link com `href="#"` vazio sem função

### 2.5 Performance básica
- [ ] CSS inline ou em arquivo único (sem múltiplos arquivos CSS desnecessários)
- [ ] JS no final do `<body>` ou com atributo `defer`
- [ ] Sem bibliotecas desnecessárias carregadas

---

## PARTE 3 — VERIFICAÇÃO DE SEGURANÇA

### 3.1 Credenciais e chaves de API
- [ ] Nenhuma chave de API exposta no código HTML ou JS
- [ ] Nenhum token iniciando com `APP_USR-`, `TEST-`, `sk_live_`, `pk_live_` nos arquivos
- [ ] Arquivo `.gitignore` existe e contém `.env`
- [ ] Variáveis de ambiente estão na Vercel (Settings → Environment Variables) e não no código

### 3.2 Formulários (se houver)
- [ ] Inputs têm validação no front-end
- [ ] Campos sensíveis têm `autocomplete` configurado corretamente
- [ ] Formulário não envia dados para URL visível na barra do navegador

### 3.3 HTTPS
- [ ] Site abre com `https://` (verificar cadeado no navegador)
- [ ] Nenhum recurso carregado via `http://` (imagens, fontes, scripts)

---

## PARTE 4 — VERIFICAÇÃO DE LGPD

### 4.1 Coleta de dados
- [ ] Se há formulário → existe página de Política de Privacidade
- [ ] Política de Privacidade linkada no footer
- [ ] Formulários informam para que os dados serão usados
- [ ] Se usa Google Analytics ou pixel de rastreamento → existe banner de cookies

### 4.2 E-commerce (se aplicável)
- [ ] Página de Política de Trocas e Devoluções presente
- [ ] Dados de pagamento processados por gateway confiável (Mercado Pago, Stripe)
- [ ] Nenhum dado de cartão armazenado no site

---

## PARTE 5 — VERIFICAÇÃO VISUAL E RESPONSIVIDADE

### 5.1 Mobile (viewport 375px)
- [ ] Nenhum elemento cortado horizontalmente
- [ ] Botões do hero completamente visíveis sem scroll horizontal
- [ ] Textos legíveis sem zoom
- [ ] Menu mobile funcional e sem bugs de toque
- [ ] Imagens não transbordam o container

### 5.2 Tablet (viewport 768px)
- [ ] Layout colapsa corretamente
- [ ] Grids ajustam o número de colunas

### 5.3 Desktop (viewport 1280px+)
- [ ] Layout sem elementos quebrados
- [ ] Espaçamentos consistentes entre seções

### 5.4 Animações
- [ ] Todas as animações definidas estão funcionando
- [ ] Animações de fundo estão ativas (não substituídas por cor sólida)
- [ ] `prefers-reduced-motion` respeitado (animações pausam quando sistema solicita)
- [ ] Hover funciona em todos os elementos interativos

---

## PARTE 6 — RELATÓRIO FINAL DO CLAUDE CODE

Após verificar todos os itens, o Claude Code deve gerar:

```
RELATÓRIO DE VERIFICAÇÃO — [Nome do Projeto]
Data: [data atual]

✅ APROVADOS: [lista]
❌ FALTANDO: [lista com o que precisa ser criado]
⚠️ AJUSTES NECESSÁRIOS: [lista com o que precisa ser corrigido]

AÇÕES RECOMENDADAS:
1. [ação 1]
2. [ação 2]

Aguardando autorização para executar as correções.
```

---

## PARTE 7 — APÓS AS CORREÇÕES DO CLAUDE CODE

### 7.1 Deploy na Vercel
Após o Code fazer as correções, pedir:
```
faça commit de todas as alterações com a mensagem "fix: verificação pós-deploy SEO, segurança e LGPD" e envie para o GitHub
```
A Vercel publica automaticamente após o push.

### 7.2 Google Search Console
Fazer manualmente após o deploy:

1. Acesse `search.google.com/search-console`
2. Clique em **"Adicionar propriedade"**
3. Escolha **"Prefixo de URL"** e cole a URL do site
4. Método de verificação: **"Arquivo HTML"**
5. Baixe o arquivo `.html` fornecido
6. Leve ao Claude Code: *"adicione este arquivo na raiz do projeto e faça o deploy"*
7. Volte ao Search Console e clique em **Verificar**
8. Após verificado, vá em **Sitemaps** no menu lateral
9. Cole: `https://URL-DO-SITE/sitemap.xml`
10. Clique em **Enviar**

**Prazo:** Google leva de 3 a 7 dias para indexar após a submissão.

### 7.3 Ferramentas de auditoria gratuitas — rodar após o deploy

| Ferramenta | URL | O que verifica |
|-----------|-----|---------------|
| PageSpeed Insights | pagespeed.web.dev | Performance, SEO e acessibilidade (nota 0-100) |
| Google Search Console | search.google.com/search-console | Indexação e palavras-chave |
| W3C Validator | validator.w3.org | Erros de HTML |
| Mozilla Observatory | observatory.mozilla.org | Segurança dos headers HTTP |

**Meta mínima:** nota acima de 80 no PageSpeed tanto mobile quanto desktop.

---

## PARTE 8 — OTIMIZAÇÃO CONTÍNUA (após o site no ar)

### Semana 1 — Logo após o deploy
- [ ] Cadastrar no Google Search Console
- [ ] Submeter sitemap.xml
- [ ] Rodar PageSpeed Insights e anotar a nota
- [ ] Verificar se o site aparece no Google buscando pelo nome do negócio

### Mês 1 — Primeiros 30 dias
- [ ] Verificar no Search Console quais palavras-chave estão trazendo visitas
- [ ] Verificar se o sitemap foi processado sem erros
- [ ] Identificar páginas com problema de indexação na aba "Cobertura"
- [ ] Verificar se a meta description está aparecendo corretamente nos resultados do Google

### Manutenção mensal
- [ ] Checar Search Console por novos erros
- [ ] Verificar se o HTTPS continua ativo
- [ ] Verificar se todos os links continuam funcionando
- [ ] Atualizar a data do `sitemap.xml` se houver alterações no site

### Quando o cliente pedir melhorias
1. Abrir o projeto no Claude Code
2. Descrever a alteração
3. Code edita o arquivo
4. Fazer commit e push para o GitHub
5. Vercel publica automaticamente
6. Verificar o resultado no navegador

---

*Documento criado em agosto de 2026.*
*Usar em todo site criado ou existente antes de considerar o projeto concluído.*
