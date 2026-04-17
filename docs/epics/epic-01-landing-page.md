# EPIC-01 — Landing Page Novare Assessoria

**Versão:** 1.0  
**Data:** 2026-04-17  
**Status:** Pronto para refinamento com @sm  
**PRD de referência:** `docs/prd/novare-landing-page.md`  
**Agente responsável:** Morgan (PM)

---

## Visão do Epic

Entregar uma landing page de alta conversão para a Novare Soluções Financeiras que:
1. **Corrija todos os bugs críticos** do HTML atual (imagem quebrada, formulário sem backend, CTA incompleto)
2. **Adicione rastreamento de conversão** para permitir otimização data-driven
3. **Atenda requisitos legais** (LGPD, Política de Privacidade, Termos de Uso)
4. **Seja publicada** com domínio e hospedagem configurados

O HTML atual (`novare_assessoria.html`) é a base — não reescrever do zero, evoluir o que existe.

---

## Critérios de Aceitação do Epic

- [ ] Logo aparece corretamente em header e footer (sem imagem quebrada)
- [ ] Formulário envia dados para destino configurado e confirma ao usuário
- [ ] Seção CTA Final possui botão WhatsApp funcional
- [ ] Google Analytics 4 rastreia cliques em CTAs e envios de formulário
- [ ] Favicon aparece na aba do browser
- [ ] Páginas de Política de Privacidade e Termos de Uso existem e são acessíveis
- [ ] Page speed score ≥ 85 no PageSpeed Insights (mobile)
- [ ] Site publicado em URL definitiva

---

## Stories do Epic

### Story 1.1 — Correção de Ativos Visuais
**Como** visitante da landing page,  
**Quero** ver o logo da Novare corretamente em todas as seções,  
**Para que** a empresa transmita credibilidade visual desde o primeiro acesso.

**Critérios de aceitação:**
- [ ] Identificar nome correto do arquivo de logo no diretório
- [ ] Atualizar todas as referências `src` no HTML para o nome correto
- [ ] Testar renderização em header e footer em desktop e mobile
- [ ] Verificar se `alt` text está descritivo em todos os `<img>` de logo

**Arquivos afetados:** `novare_assessoria.html`  
**Estimativa:** XS (< 1h)  
**Prioridade:** Crítica — bloqueia publicação

---

### Story 1.2 — Backend do Formulário de Leads
**Como** prospecto interessado nos serviços da Novare,  
**Quero** enviar meu contato pelo formulário e receber confirmação,  
**Para que** a equipe da Novare possa me retornar sem que eu precise ir ao WhatsApp.

**Critérios de aceitação:**
- [ ] Formulário envia dados (Nome, WhatsApp, E-mail, Tipo de contrato) para destino configurado
- [ ] Destino aceito: webhook n8n, Google Sheets via API, ou Formspree (decisão técnica a definir)
- [ ] Mensagem de sucesso exibida após envio confirmado pelo backend
- [ ] Em caso de falha de rede, usuário é redirecionado para WhatsApp com mensagem pré-preenchida
- [ ] Nenhum dado de lead é perdido silenciosamente

**Dependência técnica:** Escolher e configurar destino do formulário antes de codificar  
**Arquivos afetados:** `novare_assessoria.html` (função `submitForm`)  
**Estimativa:** S (2–4h)  
**Prioridade:** Crítica — sem isso, o principal objetivo de negócio não é atingido

---

### Story 1.3 — CTA Final Completo
**Como** visitante que chegou ao fim da página,  
**Quero** encontrar um botão de ação claro para iniciar contato,  
**Para que** eu não precise rolar de volta ao topo para converter.

**Critérios de aceitação:**
- [ ] Seção `.ctaf` contém botão WhatsApp com mesmo estilo do `.btn-primary`
- [ ] Link do botão usa o mesmo padrão `wa.me/5511921704799?text=...` dos demais CTAs
- [ ] Botão tem ícone SVG do WhatsApp e texto alinhado com o tom da seção
- [ ] Renderização correta em mobile (botão não ultrapassa viewport)

**Arquivos afetados:** `novare_assessoria.html` (seção `.ctaf`)  
**Estimativa:** XS (< 1h)  
**Prioridade:** Alta

---

### Story 1.4 — Favicon e Identidade da Aba
**Como** visitante com múltiplas abas abertas,  
**Quero** identificar visualmente a aba da Novare,  
**Para que** eu encontre o site rapidamente e perceba profissionalismo.

**Critérios de aceitação:**
- [ ] Favicon gerado com identidade visual da Novare (fundo escuro `#1c1c1c`, letra "N" em amarelo `#F5C518`)
- [ ] Favicon declarado no `<head>` nos formatos: `favicon.ico` (32x32) e PNG 192x192 para mobile
- [ ] Aba do browser exibe ícone correto em Chrome, Firefox e Safari

**Arquivos afetados:** `novare_assessoria.html` (`<head>`), novo arquivo `favicon.ico`  
**Estimativa:** XS (< 1h)  
**Prioridade:** Média

---

### Story 1.5 — Rastreamento de Conversão (GA4)
**Como** gestor da Novare,  
**Quero** visualizar quantas pessoas clicam nos CTAs e enviam o formulário,  
**Para que** eu possa tomar decisões baseadas em dados sobre o desempenho da página.

**Critérios de aceitação:**
- [ ] Google Analytics 4 instalado via `<script>` no `<head>`
- [ ] Evento `generate_lead` disparado em todo clique em botão WhatsApp (header, hero, especialidades, porq, ctaf)
- [ ] Evento `form_submit` disparado em envio de formulário com sucesso
- [ ] Banner de consentimento de cookies exibido antes da ativação dos scripts (LGPD)
- [ ] GA4 property ID configurado como variável no topo do script (facilita troca)

**Pré-requisito:** Conta GA4 criada e Property ID obtido pelo cliente  
**Arquivos afetados:** `novare_assessoria.html`  
**Estimativa:** S (2–3h incluindo banner de cookies)  
**Prioridade:** Alta

---

### Story 1.6 — Páginas Legais (LGPD)
**Como** visitante preocupado com privacidade,  
**Quero** acessar a Política de Privacidade e os Termos de Uso da Novare,  
**Para que** eu me sinta seguro ao fornecer meus dados no formulário.

**Critérios de aceitação:**
- [ ] Arquivo `politica-de-privacidade.html` criado com conteúdo mínimo legal (dados coletados, finalidade, direitos LGPD, contato do responsável)
- [ ] Arquivo `termos-de-uso.html` criado com escopo do serviço e limitações
- [ ] Links no footer atualizados para apontar para os arquivos corretos (não mais `href="#"`)
- [ ] Ambas as páginas mantêm identidade visual da landing page (header/footer reutilizados)
- [ ] CNPJ `63.811.122/0001-88` e e-mail `solucoesnovare@gmail.com` mencionados como responsável

**Nota:** Conteúdo jurídico deve ser revisado por advogado antes de publicação final  
**Arquivos afetados:** Novos arquivos `politica-de-privacidade.html`, `termos-de-uso.html`; `novare_assessoria.html` (footer)  
**Estimativa:** M (3–5h)  
**Prioridade:** Alta (obrigatório antes de trafego pago)

---

### Story 1.7 — SEO Técnico Básico
**Como** responsável pela Novare,  
**Quero** que a página apareça bem indexada no Google,  
**Para que** leads orgânicos encontrem o site sem depender exclusivamente de anúncios.

**Critérios de aceitação:**
- [ ] `<link rel="canonical" href="[URL-definitiva]">` no `<head>`
- [ ] `og:url` e `og:image` preenchidos (og:image = logo da Novare em 1200x630px)
- [ ] Schema.org `LocalBusiness` JSON-LD inserido no `<head>` com: name, url, telephone, address, email, openingHours
- [ ] `robots.txt` criado na raiz permitindo indexação
- [ ] `sitemap.xml` criado com as 3 URLs (index, política, termos)

**Pré-requisito:** URL de hospedagem definitiva definida  
**Arquivos afetados:** `novare_assessoria.html`, novos `robots.txt`, `sitemap.xml`  
**Estimativa:** S (2–3h)  
**Prioridade:** Média

---

### Story 1.8 — Otimização de Performance
**Como** visitante acessando pelo celular em rede 4G,  
**Quero** que a página carregue rapidamente,  
**Para que** eu não desista antes de ver o conteúdo.

**Critérios de aceitação:**
- [ ] Imagens abaixo do fold com `loading="lazy"` e `decoding="async"`
- [ ] Logo convertido para formato WebP (com fallback PNG)
- [ ] PageSpeed Insights mobile score ≥ 85
- [ ] LCP < 2.5s em simulação 4G Mobile
- [ ] CLS < 0.1 (sem layout shifts visíveis)
- [ ] Imagens do Unsplash nas flip cards substituídas por versões dimensionadas corretamente (evitar download de 600px desnecessário)

**Arquivos afetados:** `novare_assessoria.html`, assets de imagem  
**Estimativa:** M (3–5h)  
**Prioridade:** Média

---

### Story 1.9 — Deploy e Publicação
**Como** responsável pela Novare,  
**Quero** que o site esteja publicado em URL acessível ao público,  
**Para que** eu possa começar a divulgar e capturar leads.

**Critérios de aceitação:**
- [ ] Hospedagem escolhida e configurada (GitHub Pages, Vercel ou servidor próprio)
- [ ] Domínio configurado com SSL (HTTPS obrigatório)
- [ ] Todos os assets (HTML, logo, favicon, páginas legais) publicados corretamente
- [ ] Teste smoke: acessar cada seção, enviar formulário de teste, clicar em todos os CTAs WhatsApp
- [ ] URL definitiva atualizada no canonical, schema, og:url e sitemap

**Pré-requisito:** Todas as stories 1.1–1.8 concluídas  
**Estimativa:** M (4–6h incluindo configuração de DNS)  
**Prioridade:** Alta — entrega final do epic  
**Agente executor:** @devops (Gage) — push e configuração de infraestrutura

---

## Ordem de Execução Recomendada

```
1.1 (Imagem) → 1.3 (CTA) → 1.4 (Favicon)   ← Paralelo — quick wins visuais
       ↓
   1.2 (Formulário backend)                   ← Bloqueia geração de leads
       ↓
   1.5 (GA4 + Cookies)                        ← Habilita rastreamento
   1.6 (Páginas legais)                       ← Paralelo com 1.5
       ↓
   1.7 (SEO técnico)                          ← Depende de URL definitiva
   1.8 (Performance)                          ← Paralelo com 1.7
       ↓
   1.9 (Deploy)                               ← Última etapa
```

---

## Decisões em Aberto

| # | Decisão | Opções | Quem decide | Prazo |
|---|---------|--------|------------|-------|
| D1 | Backend do formulário | Formspree (zero infra) · n8n webhook · Google Sheets API | Cliente + @architect | Antes de 1.2 |
| D2 | Hospedagem | GitHub Pages (grátis) · Vercel (grátis) · servidor próprio | Cliente | Antes de 1.9 |
| D3 | Domínio | novareassessoria.com.br · novaresolucoes.com.br · outro | Cliente | Antes de 1.7 |
| D4 | Property ID GA4 | Criar nova propriedade GA4 | Cliente | Antes de 1.5 |

---

## Estimativa Total

| Tier | Stories | Estimativa |
|------|---------|-----------|
| Crítico | 1.1, 1.2, 1.3 | 4–6h |
| Alto | 1.5, 1.6, 1.9 | 9–14h |
| Médio | 1.4, 1.7, 1.8 | 6–9h |
| **Total** | **9 stories** | **~19–29h** |

---

## Stack Técnica

| Camada | Tecnologia | Justificativa |
|--------|-----------|--------------|
| Frontend | HTML5 + CSS3 + Vanilla JS | Manter simplicidade — sem build tooling |
| Formulário backend | A definir (ver D1) | Escolha do cliente |
| Analytics | Google Analytics 4 | Gratuito, padrão de mercado |
| Hospedagem | A definir (ver D2) | Escolha do cliente |
| SSL | Automático via Vercel/GH Pages ou Let's Encrypt | Obrigatório para HTTPS |

---

## Referências

- PRD completo: `docs/prd/novare-landing-page.md`
- HTML atual: `novare_assessoria.html`
- Logo: `novare-assessoria-logo.png`
- WhatsApp de contato: `+55 11 92170-4799`
- E-mail: `solucoesnovare@gmail.com`
- CNPJ: `63.811.122/0001-88`
- Endereço: Av. Artur de Queirós, 287 — Casa Branca, Santo André — SP

---

*Epic gerado por Morgan (PM Agent) — Synkra AIOX · 2026-04-17*
