# SEO, Segurança e LGPD — Guia de Referência
> Documento de uso interno para criação, entrega e auditoria de sites.
> Deve ser consultado antes de gerar o prompt no QG e após o deploy na Vercel.

---

## PARTE 1 — SEO (Search Engine Optimization)

### O que é
SEO é o conjunto de práticas que fazem um site aparecer nos resultados do Google e outros buscadores. Dividido em SEO técnico (código) e SEO de conteúdo (texto, palavras-chave).

---

### 1.1 Meta Description

**O que é:** Texto de até 160 caracteres que aparece embaixo do título do site nos resultados do Google. Não afeta diretamente o ranking, mas aumenta a taxa de cliques.

**Como funciona:**
```html
<meta name="description" content="Descrição clara do negócio, com a palavra-chave principal. Até 160 caracteres.">
```

**Regras:**
- Sempre única por página
- Incluir a palavra-chave principal naturalmente
- Terminar com uma chamada para ação implícita ("Agende agora", "Conheça a coleção")

**Quem faz:** Claude Code, instruído no prompt do QG.

**Quando:** Na criação do site. Obrigatório em todo projeto.

**Instrução para o QG:** Sempre perguntar ao cliente qual é a descrição do negócio e a palavra-chave principal antes de gerar o prompt.

---

### 1.2 Palavras-chave

**O que é:** Os termos que o público-alvo digita no Google para encontrar o negócio do cliente.

**Como funciona:** As palavras-chave devem aparecer naturalmente em:
- Título da página (tag `<title>`)
- Meta description
- Heading principal (H1) — apenas um por página
- Subtítulos (H2, H3)
- Primeiros parágrafos do texto
- Atributo `alt` das imagens

**Exemplos por nicho:**
| Nicho | Palavras-chave principais |
|---|---|
| Clínica estética | "clínica estética em [cidade]", "botox [cidade]" |
| Advocacia | "advogado trabalhista [cidade]", "escritório advocacia" |
| Restaurante | "restaurante [tipo] em [cidade]", "cardápio [culinária]" |
| Loja de joias | "joias banhadas a ouro", "cordão masculino banhado" |

**Quem faz:** Kevin define as palavras-chave no briefing do QG. Claude Code as distribui no código.

**Quando:** Antes de gerar o prompt — é um passo obrigatório no briefing.

**Instrução para o QG:** Sempre perguntar ao cliente quais termos seus clientes usam para encontrá-lo antes de gerar o prompt. Nunca criar site sem definir pelo menos 3 palavras-chave.

---

### 1.3 Sitemap.xml

**O que é:** Arquivo que lista todas as páginas do site em formato de mapa. Entregue ao Google para acelerar o rastreamento e indexação.

**Como funciona:** É um arquivo `.xml` separado na raiz do projeto:
```
meu-site/
├── index.html
├── sitemap.xml   ← aqui
├── style.css
└── script.js
```

**Exemplo de sitemap simples:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://www.seusite.com.br/</loc>
    <lastmod>2026-01-01</lastmod>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://www.seusite.com.br/contato.html</loc>
    <lastmod>2026-01-01</lastmod>
    <priority>0.8</priority>
  </url>
</urlset>
```

**Quem faz:** Claude Code cria o arquivo. Kevin submete ao Google Search Console após o deploy.

**Quando:** Na criação do site. Instrução obrigatória no prompt.

**Instrução para o QG:** Sempre incluir no prompt: "Crie o arquivo sitemap.xml na raiz do projeto listando todas as páginas."

---

### 1.4 llms.txt

**O que é:** Arquivo de texto na raiz do site que instrui IAs (ChatGPT, Perplexity, Claude, Gemini) sobre o que o site faz e como recomendar seu conteúdo. Funciona como um "robots.txt para inteligências artificiais".

**Como funciona:** Arquivo de texto simples em `seusite.com/llms.txt`:
```
# Nome do Negócio

> Descrição curta do que o negócio faz.

## Sobre
Informações principais sobre o negócio, serviços, localização.

## Serviços
- Serviço 1
- Serviço 2

## Contato
WhatsApp: (XX) XXXXX-XXXX
```

**Por que incluir agora:** A adoção está crescendo rapidamente. Sites que já têm o arquivo saem na frente quando IAs fazem recomendações de negócios locais.

**Quem faz:** Claude Code, instruído no prompt do QG.

**Quando:** Na criação do site. Incluir em todo projeto a partir de agora.

**Instrução para o QG:** Sempre incluir no prompt: "Crie o arquivo llms.txt na raiz do projeto com nome, descrição, serviços e contato do negócio."

---

### 1.5 Google Search Console

**O que é:** Painel gratuito do Google onde você cadastra o site, monitora como ele aparece nas buscas e submete o sitemap.

**Passo a passo para cadastrar:**

1. Acesse: `search.google.com/search-console`
2. Clique em **"Adicionar propriedade"**
3. Escolha **"Prefixo de URL"** e cole a URL do site (ex: `https://www.seusite.com.br`)
4. Clique em **Continuar**
5. O Google oferece métodos de verificação — escolha **"Arquivo HTML"**
6. Baixe o arquivo `.html` fornecido pelo Google
7. Envie o arquivo para o Claude Code colocar na raiz do projeto
8. Faça o deploy novamente na Vercel
9. Volte ao Search Console e clique em **Verificar**
10. Após verificado, clique em **Sitemaps** no menu lateral
11. Cole a URL do sitemap: `https://www.seusite.com.br/sitemap.xml`
12. Clique em **Enviar**

**O que monitorar após cadastro:**
- Cobertura: quais páginas foram indexadas
- Desempenho: quais palavras-chave trazem visitas
- Erros: páginas com problema de indexação

**Quem faz:** Kevin, após o deploy. Não é automático.

**Quando:** Após cada novo site publicado. Fazer para cada cliente.

**Prazo:** O Google leva de 3 a 7 dias para indexar após a submissão.

---

## PARTE 2 — SEGURANÇA (Cybersegurança)

### Checklist de Segurança — aplicar em todo site

#### 1. Gestão de Segredos e Credenciais
- [ ] Nunca armazenar chaves de API no front-end (código visível no navegador)
- [ ] Nunca expor tokens, senhas ou credenciais no código do cliente
- [ ] Utilizar variáveis de ambiente para armazenar informações sensíveis
- [ ] Restringir permissões das chaves de API ao mínimo necessário
- [ ] Arquivo `.gitignore` criado com `.env` incluído antes do primeiro commit

#### 2. Arquitetura e Acesso a Dados
- [ ] O front-end não deve acessar diretamente o banco de dados
- [ ] Todas as consultas e operações devem passar pela API/back-end
- [ ] Implementar validações de acesso no servidor
- [ ] Aplicar o princípio do menor privilégio para usuários e serviços

#### 3. Proteção de Dados dos Usuários
- [ ] Exibir apenas as informações necessárias para cada usuário
- [ ] Nunca expor senhas em nenhuma interface
- [ ] Evitar a exposição de dados sensíveis de outros usuários
- [ ] Utilizar criptografia para dados sensíveis armazenados

#### 4. Validação e Sanitização de Entradas
- [ ] Validar todos os dados recebidos do usuário
- [ ] Sanitizar entradas antes de processá-las
- [ ] Proteger contra SQL Injection
- [ ] Proteger contra Cross-Site Scripting (XSS)
- [ ] Limitar tamanho e formato dos dados recebidos
- [ ] Validar entradas tanto no front-end quanto no back-end

#### 5. Autenticação e Autorização (sites com login)
- [ ] Toda autenticação deve ser realizada no back-end
- [ ] O front-end apenas envia credenciais e exibe resultados
- [ ] Verificar permissões do usuário em cada requisição
- [ ] Utilizar senhas com hash seguro (bcrypt, Argon2 ou equivalente)
- [ ] Implementar autenticação multifator (MFA) quando possível

#### 6. Monitoramento e Logs (sites com back-end)
- [ ] Registrar eventos importantes do sistema
- [ ] Monitorar tentativas de login falhadas
- [ ] Registrar atividades suspeitas
- [ ] Manter logs protegidos contra alterações
- [ ] Criar alertas para comportamentos anormais

#### 7. Proteção Contra Abusos (sites com formulários e APIs)
- [ ] Implementar Rate Limiting nas APIs
- [ ] Limitar tentativas de login consecutivas
- [ ] Bloquear ou desafiar acessos suspeitos
- [ ] Utilizar CAPTCHA quando necessário
- [ ] Proteger endpoints críticos contra ataques automatizados

---

### 2.1 Arquivo .gitignore e variáveis de ambiente

**O que é o .gitignore:**
Arquivo que instrui o Git a nunca enviar determinados arquivos para o GitHub. O `.env` deve estar sempre listado aqui.

**O que é o .env:**
Arquivo local (no seu computador) onde ficam as chaves secretas durante o desenvolvimento. Nunca deve subir para o repositório.

**Como verificar se o Claude Code fez corretamente:**
1. Abra o repositório no GitHub
2. Procure pelo arquivo `.gitignore` na raiz
3. Abra o arquivo e confirme que `.env` está listado dentro
4. Procure nos arquivos `.js` por qualquer chave exposta (ex: `APP_USR-`, `TEST-`, `sk_live_`)
5. Se encontrar chave exposta no código, ela precisa ser removida e movida para a Vercel

**Instrução para o QG:** Sempre incluir no prompt: "Crie o arquivo .gitignore na raiz com .env incluído. Nenhuma chave de API deve aparecer no código."

---

### 2.2 Variáveis de ambiente na Vercel

**O que é:**
Forma segura de guardar chaves de API e dados sensíveis fora do código. Você cadastra o valor na Vercel e o código apenas lê o nome da variável.

**Quando usar:**
- Integração com Mercado Pago (chave secreta)
- Integração com qualquer API externa que exija autenticação
- Senhas de banco de dados

**Como cadastrar na Vercel:**
1. Acesse o painel da Vercel: `vercel.com/dashboard`
2. Clique no projeto
3. Vá em **Settings → Environment Variables**
4. Clique em **Add New**
5. Nome: `MERCADOPAGO_SECRET_KEY` (exemplo)
6. Valor: cole a chave real
7. Selecione os ambientes: Production, Preview, Development
8. Clique em **Save**
9. Faça um novo deploy para as variáveis entrarem em vigor

**Quem faz:** Kevin, no painel da Vercel. O Claude Code não deve ter acesso a valores reais de chaves.

**Quando:** Após o deploy, antes de colocar o site em produção com integrações de pagamento.

---

### 2.3 Verificação do KW Imports (www.kwimports.com.br)

**O que já está correto:**
- ✅ HTTPS ativo — certificado SSL funcionando (Vercel garante automaticamente)
- ✅ Pagamento via Mercado Pago (gateway confiável, não armazena dados de cartão no site)
- ✅ Política de Privacidade presente
- ✅ Página de Trocas e Devoluções presente

**O que você precisa verificar manualmente:**
1. Abrir o repositório do KW Imports no GitHub
2. Procurar nos arquivos `.js` por qualquer texto iniciando com `APP_USR-` ou `TEST-`
3. Se encontrar: remover do código, cadastrar na Vercel em Settings → Environment Variables
4. Verificar se o arquivo `.gitignore` existe e contém `.env`
5. Verificar no painel da Vercel se há variáveis de ambiente cadastradas (Settings → Environment Variables)

**Status geral:** Site simples em HTML/JS, risco baixo. Principal ponto de atenção é a chave do Mercado Pago.

---

### 2.4 Prefixo NEXT_PUBLIC (Next.js)

**O que é:**
Convenção do framework Next.js. Qualquer variável com prefixo `NEXT_PUBLIC_` fica exposta no navegador e pode ser lida por qualquer pessoa.

**Quando se aplica:** Apenas em projetos Next.js. Seus sites atuais em HTML/CSS/JS puro não usam Next.js, então não se aplica agora.

**Regra quando chegar a hora:**
- `NEXT_PUBLIC_` → só para dados públicos (URL do site, nome da marca)
- Nunca usar `NEXT_PUBLIC_` para chaves de API, tokens ou senhas

---

### 2.5 localStorage vs Cookies seguros

**localStorage — o que não guardar:**
- Tokens de autenticação (JWT)
- CPF, e-mail, senha
- Dados de sessão de login

**Por quê:** O localStorage é acessível por qualquer JavaScript na página. Um ataque XSS consegue ler tudo que está lá.

**O que usar no lugar:**
- Cookies com flag `HttpOnly` — o JavaScript não consegue acessá-los, apenas o servidor
- `sessionStorage` quando necessário — limpo automaticamente ao fechar a aba

**Configuração correta de cookie seguro:**
```
Set-Cookie: token=abc123; HttpOnly; Secure; SameSite=Strict
```

**Quando se aplica:** Apenas em sites com sistema de login. Seus sites atuais sem autenticação não precisam disso agora.

---

### 2.6 HTTPS e protocolo seguro

**O que é:** Protocolo de comunicação criptografado entre o navegador do usuário e o servidor.

**Status nos seus sites:** A Vercel ativa o HTTPS automaticamente em todo deploy. Não é necessário configurar manualmente.

**Verificação:** O cadeado no navegador indica que o HTTPS está ativo. Se aparecer "Não seguro", o certificado expirou — acesse o painel da Vercel e force um novo deploy.

---

## PARTE 3 — LGPD (Lei Geral de Proteção de Dados)

### O que é

<cite index="5-1">A LGPD (Lei nº 13.709/2018) é a legislação brasileira criada para garantir a privacidade, segurança e controle dos dados pessoais de indivíduos. Entrou em vigor em agosto de 2020 e estabelece regras e princípios para o tratamento de dados pessoais por parte de organizações, com previsão de sanções em caso de descumprimento, como multas e outras penalidades.</cite>

<cite index="1-1">A LGPD é baseada na GDPR europeia e dispõe sobre o tratamento de dados pessoais tanto no meio digital quanto físico, com o objetivo de proteger direitos fundamentais, privacidade e liberdade.</cite>

---

### 3.1 O que são dados pessoais (contexto e-commerce)

<cite index="2-1">A LGPD define dado pessoal como qualquer informação que permita identificar uma pessoa, direta ou indiretamente. No contexto do e-commerce, isso inclui: cadastro (nome, CPF, CNPJ, data de nascimento), contato (e-mail, telefone, WhatsApp), endereço (entrega, cobrança, geolocalização) e pagamento (dados do cartão, histórico de compras).</cite>

---

### 3.2 O que todo site deve ter para estar em conformidade

**Obrigatório em todo site que coleta dados (formulário, checkout, WhatsApp):**

#### Política de Privacidade
Página explicando quais dados são coletados, para que são usados, como são armazenados e os direitos do usuário. Deve ser linkada no footer.

O que incluir:
- Quais dados são coletados (nome, e-mail, CPF, endereço)
- Por que são coletados (processamento de pedido, contato)
- Com quem são compartilhados (Mercado Pago, Correios)
- Direitos do titular (acesso, correção, exclusão)
- Contato do responsável pelos dados

**Instrução para o QG:** Todo site com formulário ou checkout deve ter página de Política de Privacidade. Incluir no prompt obrigatoriamente.

#### Aviso de Cookies (quando aplicável)
Sites que usam cookies de rastreamento (Google Analytics, Facebook Pixel) precisam informar o usuário e pedir consentimento.

Banner simples no rodapé ou popup ao entrar no site com botão "Aceitar" e link para a Política de Privacidade.

#### Termo de Uso (recomendado para e-commerce)
Documento explicando as regras de uso do site, política de troca e devolução, e condições de compra.

---

### 3.3 Direitos do titular dos dados

O cliente do seu cliente tem direito a:
- Saber quais dados foram coletados
- Corrigir dados incorretos
- Solicitar exclusão dos dados
- Revogar consentimento

O responsável por atender essas solicitações é o seu cliente (dono do negócio), não você como desenvolvedor.

---

### 3.4 Penalidades por descumprimento

A ANPD (Autoridade Nacional de Proteção de Dados) pode aplicar:
- Advertência
- Multa de até 2% do faturamento, limitada a R$ 50 milhões por infração
- Bloqueio ou eliminação dos dados

Para os portes de negócio dos seus clientes (pequenas empresas), o risco imediato é baixo, mas a adequação é obrigatória e protege também a reputação.

---

### 3.5 GDPR (Internacional)

A GDPR é o equivalente europeu da LGPD. Se um site atende clientes fora do Brasil (especialmente da Europa), deve seguir também a GDPR.

O KW Imports menciona "Envios Internacionais — Brasil e Exterior", então tecnicamente deveria ter aviso de GDPR para visitantes europeus.

**Na prática para seus clientes:** Se o site vende apenas para o Brasil, a LGPD é suficiente. Sites com vendas internacionais precisam de aviso de GDPR no banner de cookies.

---

## PARTE 4 — PROTOCOLO DE CRIAÇÃO

### O que deve acontecer em todo projeto, do briefing ao deploy

#### No QG (antes do prompt)

- [ ] Definir pelo menos 3 palavras-chave principais com o cliente
- [ ] Escrever a meta description do negócio (até 160 caracteres)
- [ ] Confirmar se o site terá formulário ou checkout (define necessidade de LGPD)
- [ ] Confirmar se haverá integração com API (define necessidade de variáveis de ambiente)

#### No prompt para o Claude Code

Incluir sempre:
```
- Criar arquivo sitemap.xml na raiz com todas as páginas
- Criar arquivo llms.txt na raiz com nome, descrição, serviços e contato
- Criar arquivo .gitignore com .env incluído
- Inserir meta description: "[descrição definida no briefing]"
- Inserir meta keywords: "[palavras-chave definidas no briefing]"
- Estrutura de headings correta: um H1 por página, H2 para seções, H3 para subseções
- Atributo alt em todas as imagens
- [Se tiver formulário ou checkout] Criar página de Política de Privacidade linkada no footer
```

#### Após o deploy na Vercel

- [ ] Cadastrar chaves de API em Settings → Environment Variables (se houver integração)
- [ ] Cadastrar o site no Google Search Console
- [ ] Submeter o sitemap.xml no Search Console
- [ ] Verificar se o HTTPS está ativo (cadeado no navegador)
- [ ] Verificar no GitHub se o .gitignore existe e contém .env
- [ ] Verificar se nenhuma chave de API está exposta nos arquivos .js

---

## PARTE 5 — AUDITORIA DE SITE EXISTENTE

### Procedimento para auditar um site já publicado

**1. Verificar SEO básico**
- Acessar o site e ver o código-fonte (Ctrl+U no Chrome)
- Procurar por `<meta name="description"` — se não existir, está faltando
- Procurar por `<title>` — verificar se contém palavras-chave
- Verificar se as imagens têm atributo `alt`
- Acessar `seusite.com/sitemap.xml` — se retornar 404, o arquivo não existe

**2. Verificar segurança básica**
- Confirmar HTTPS ativo (cadeado no navegador)
- Abrir o repositório no GitHub e buscar por chaves expostas (`APP_USR-`, `TEST-`, `sk_live_`, `pk_live_`)
- Verificar se `.gitignore` existe e contém `.env`
- Verificar no painel da Vercel se variáveis de ambiente estão cadastradas

**3. Verificar LGPD**
- Verificar se existe página de Política de Privacidade
- Verificar se o link está no footer
- Verificar se formulários informam para que os dados serão usados

**4. Ferramentas de auditoria gratuitas**
- `search.google.com/search-console` — indexação e performance de busca
- `pagespeed.web.dev` — performance e SEO técnico (dá nota de 0 a 100)
- `validator.w3.org` — valida o HTML
- `observatory.mozilla.org` — segurança dos headers HTTP

---

*Documento criado em agosto de 2026. Atualizar sempre que novas práticas forem incorporadas ao workflow.*
