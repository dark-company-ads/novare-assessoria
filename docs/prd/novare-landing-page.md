# PRD — Landing Page Novare Assessoria

**Versão:** 1.0  
**Data:** 2026-04-17  
**Status:** Aprovado para desenvolvimento  
**Responsável:** Morgan (PM)

---

## 1. Visão Geral do Produto

A **Novare Soluções Financeiras** é uma assessoria especializada em auditoria e renegociação de contratos financeiros. Identifica cobranças ilegais em financiamentos e empréstimos e negocia com as instituições financeiras em nome do cliente, com remuneração 100% atrelada ao resultado.

**Site atual:** `novare_assessoria.html` — single-page HTML estático, sem backend, sem analytics, sem rastreamento de conversão.

**Objetivo do produto:** Ter uma landing page de alta conversão que sirva como principal canal de aquisição de leads qualificados via WhatsApp e formulário, com base de referência clara para futuras evoluções.

---

## 2. Problema

### 2.1 Problema do negócio
A Novare opera 100% por indicação e WhatsApp direto. Não há canal digital estruturado que:
- Eduque o lead sobre o serviço antes do primeiro contato
- Capture dados do prospecto fora do horário comercial
- Transmita credibilidade e prova social de forma sistematizada

### 2.2 Problemas identificados no HTML atual
| Item | Problema | Impacto |
|------|----------|---------|
| Imagem quebrada | `novare_assessoria.jpeg` referenciado, arquivo real é `novare-assessoria-logo.png` | Logo não aparece em header e footer |
| Formulário sem backend | `submitForm()` apenas esconde o form, não envia dados a lugar nenhum | Leads perdidos |
| CTA final incompleto | Seção `.ctaf` tem texto mas nenhum botão de ação | Funil incompleto |
| Sem analytics | Nenhum pixel, tag ou script de rastreamento | Impossível medir conversão |
| Sem favicon | Aba do browser sem identidade visual | Profissionalismo |
| Sem páginas legais | Política de Privacidade e Termos linkam para `#` | Risco jurídico / LGPD |
| Sem SEO técnico | Falta canonical, structured data, og:image, og:url | Visibilidade orgânica |

---

## 3. Público-Alvo

### Persona Primária — "O Endividado Sobrecarregado"
- **Perfil:** Brasileiro adulto (25–55 anos), tem financiamento de veículo, imóvel ou empréstimo consignado
- **Situação:** Paga parcelas há meses/anos, sente que a dívida não diminui
- **Gatilho:** Recebeu ameaça de negativação, busca e apreensão, ou simplesmente desconfia que foi lesado
- **Canal de chegada:** Busca orgânica ("como revisar contrato de financiamento"), indicação boca a boca, redes sociais
- **Comportamento:** Mobile-first, WhatsApp como canal principal de comunicação

### Persona Secundária — "O Pesquisador Cauteloso"
- **Perfil:** Mesma faixa, porém mais cético
- **Necessidade:** Entender o processo antes de qualquer contato, validar credibilidade da empresa
- **Comportamento:** Lê FAQ completo, verifica CNPJ, busca o nome da empresa no Google

---

## 4. Objetivos e Métricas de Sucesso

### Objetivos
1. Converter visitantes em leads qualificados (WhatsApp ou formulário)
2. Transmitir credibilidade técnica e prova social
3. Explicar o processo com clareza para reduzir fricção no primeiro contato
4. Ser base de referência para futuras implementações (SEO, A/B tests, versões multilíngue)

### KPIs (metas para 90 dias após publicação)
| Métrica | Meta |
|---------|------|
| Taxa de conversão (clique CTA WhatsApp ou envio de form) | ≥ 4% das sessões |
| Tempo médio na página | ≥ 2 minutos |
| Taxa de rejeição | ≤ 65% |
| Leads capturados por formulário/mês | ≥ 50 |
| Core Web Vitals — LCP | < 2.5s |
| Core Web Vitals — CLS | < 0.1 |

---

## 5. Escopo do Produto

### 5.1 Estrutura de Seções (estado atual — referência)

| # | Seção | Propósito | Status atual |
|---|-------|-----------|-------------|
| 1 | Header fixo | Navegação + CTA WhatsApp | ✅ Funcional |
| 2 | Hero | Proposta de valor principal, CTAs | ✅ Funcional |
| 3 | Trust Bar | Números de credibilidade | ✅ Funcional |
| 4 | Dor + Formulário | Qualificar lead e capturar contato | ⚠️ Form sem backend |
| 5 | Como Funciona | Processo em 3 passos | ✅ Funcional |
| 6 | Especialidades | Flip cards por tipo de contrato | ✅ Funcional |
| 7 | Missão / Quem Somos | Humanizar a empresa | ✅ Funcional |
| 8 | Por Que Escolher | Diferenciais competitivos | ✅ Funcional |
| 9 | Depoimentos | Prova social com resultados reais | ✅ Funcional |
| 10 | Números | Impacto quantificado | ✅ Funcional |
| 11 | FAQ | Reduzir objeções pré-contato | ✅ Funcional |
| 12 | CTA Final | Última chamada para ação | ⚠️ Sem botão |
| 13 | Footer | Contato, endereço, links legais | ⚠️ Links legais quebrados |

### 5.2 Requisitos Funcionais

**RF-01 — Formulário de captura de leads**
- Campos: Nome, WhatsApp, E-mail (opcional), Tipo de contrato
- Submissão deve enviar dados para destino configurado (webhook, planilha ou CRM)
- Exibir mensagem de sucesso após envio
- Fallback: se backend falhar, redirecionar para WhatsApp pré-preenchido

**RF-02 — Rastreamento de conversão**
- Implementar Google Analytics 4 (GA4) ou Meta Pixel conforme necessidade
- Disparar evento de conversão em: clique em qualquer botão WhatsApp, envio de formulário com sucesso

**RF-03 — CTA Final completo**
- Seção `.ctaf` deve conter botão WhatsApp funcional idêntico aos demais CTAs da página

**RF-04 — Correção de imagem**
- Renomear `novare-assessoria-logo.png` para `novare_assessoria.jpeg` OU atualizar todas as referências no HTML para o nome correto do arquivo

**RF-05 — Favicon**
- Adicionar favicon baseado na identidade visual da Novare (amarelo `#F5C518` + inicial "N")

**RF-06 — Páginas legais**
- Criar páginas mínimas: `politica-de-privacidade.html` e `termos-de-uso.html`
- Atualizar links no footer

### 5.3 Requisitos Não-Funcionais

**RNF-01 — Performance**
- LCP < 2.5s em conexão 4G mobile
- Imagens otimizadas (WebP onde possível, lazy loading para imagens abaixo do fold)
- CSS crítico inline para first paint rápido

**RNF-02 — Responsividade**
- Breakpoints já implementados para ≤ 860px
- Testar em iPhone SE, Samsung Galaxy A, iPad

**RNF-03 — Acessibilidade**
- Todos os botões com `aria-label` descritivo
- Contraste mínimo WCAG AA nas cores principais
- `alt` em todas as imagens

**RNF-04 — SEO Técnico**
- `<link rel="canonical">` apontando para URL definitiva
- `og:image` e `og:url` preenchidos
- Schema.org `LocalBusiness` no `<head>`

**RNF-05 — LGPD**
- Aviso de cookies (banner simples) antes de ativar qualquer script de rastreamento
- Link para Política de Privacidade visível no footer

---

## 6. Design e Identidade Visual

### Tokens de cor (já definidos no CSS)
| Variável | Hex | Uso |
|----------|-----|-----|
| `--amarelo` | `#F5C518` | CTA primário, destaques, números |
| `--cinza-dark` | `#1c1c1c` | Background hero, header |
| `--cinza-esc` | `#2e2e2e` | Títulos, ícones |
| `--cinza-bg` | `#f5f5f5` | Seções de fundo claro |

### Princípios visuais
- Dark header/hero + seções claras alternadas cria ritmo visual
- Amarelo como único acento — reservado para ações e números
- Cards com hover `translateY(-4px)` + border amarelo como padrão de interação
- Tipografia: `Segoe UI, Arial, sans-serif` (system font — sem webfont extra)

---

## 7. Integrações e Dependências

| Integração | Situação | Prioridade |
|------------|----------|-----------|
| WhatsApp Business API | Número: `+55 11 921704799` — já integrado via links `wa.me` | ✅ Ativo |
| Google Analytics 4 | Não implementado | Alta |
| Formulário backend | Não implementado (opções: n8n webhook, Google Sheets, Formspree) | Alta |
| Google Maps embed | Implementado no footer via iframe | ✅ Ativo |
| Instagram | Link no footer: `instagram.com/novaresolucoes` | ✅ Ativo |

---

## 8. Restrições e Premissas

- **Stack:** HTML/CSS/JS puro (sem framework) — manter simplicidade de deploy
- **Hospedagem:** A definir (GitHub Pages, Vercel ou servidor próprio)
- **Domínio:** A definir
- **Sem e-commerce:** Nenhuma transação financeira na página
- **Conteúdo:** Todos os textos, números e depoimentos já validados pelo cliente estão no HTML atual

---

## 9. Fora do Escopo (v1.0)

- Blog ou área de conteúdo
- Área do cliente / login
- Chatbot automatizado
- Integração com CRM completo
- Versão em inglês/espanhol
- Calculadora de economia online

---

## 10. Riscos

| Risco | Probabilidade | Impacto | Mitigação |
|-------|--------------|---------|-----------|
| Formulário sem destino causa perda de leads | Alta | Alto | Prioridade máxima no RF-01 |
| Imagem quebrada prejudica credibilidade | Alta | Médio | Corrigir antes de qualquer divulgação |
| Sem analytics impossibilita otimização | Média | Alto | Implementar GA4 no primeiro deploy |
| Links legais quebrados — risco LGPD | Média | Alto | Criar páginas mínimas antes de trafego pago |

---

## 11. Glossário

| Termo | Definição |
|-------|-----------|
| **CTA** | Call to Action — botão ou link de conversão |
| **Lead** | Prospecto que demonstrou interesse e forneceu contato |
| **LCP** | Largest Contentful Paint — métrica de performance do Google |
| **LGPD** | Lei Geral de Proteção de Dados Pessoais (Brasil) |
| **TR** | Taxa Referencial — índice de correção usado em financiamentos imobiliários |
| **IOF** | Imposto sobre Operações Financeiras |

---

*Documento gerado por Morgan (PM Agent) — Synkra AIOX · 2026-04-17*
