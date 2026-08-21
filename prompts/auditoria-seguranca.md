# 🛡️ Prompt Otimizado para Auditoria de Segurança, LGPD e Deploy (Read-Only)
**Versão: 10/10 | AppSec/DevSecOps + LGPD + DevOps/SRE | Agnóstico de Stack | Engenharia de Prompt Aplicada**

---

## 📋 Índice de Execução
1. **Auto-detecção de Contexto (Stack, Auth, Infra, Dados Pessoais)**
2. **Gate de Confirmação de Aplicabilidade (38 itens)**
3. **Verificação Detalhada de Conformidade por Bloco**
4. **Regras Anti-Falso-Positivo**
5. **Relatório Final por Severidade**

---

## ✅ PROMPT: AUDITORIA DE SEGURANÇA, LGPD E CHECKLIST DE DEPLOY (READ-ONLY)

### 📖 O QUE ESTE PROMPT FAZ:
Diferente do Doc 5 (auditoria de qualidade de código — SOLID/DRY/código morto), este prompt audita três domínios distintos, cada um com **critério de julgamento próprio, aplicado por um "especialista" diferente**:

- **AppSec/DevSecOps** para os blocos de Segurança Front-End e Back-End (critério: OWASP ASVS/Top 10, CWE)
- **Especialista em conformidade LGPD** para o bloco LGPD (critério: conformidade regulatória com a Lei 13.709/2018 — ausência de item aqui é risco legal, não só técnico)
- **DevOps/SRE** para o Checklist de Deploy (critério: configuração operacional, que pode estar **fora do repositório** — CDN, provedor de hospedagem, painel do Supabase)

É estritamente **read-only**: nunca aplica correção, nunca gera patch — apenas descreve o problema e a sugestão de correção em texto. Também traz uma distinção importante que os outros documentos não têm: itens cuja verificação depende de infraestrutura externa ao repositório são classificados como **"Não verificável no repositório"**, nunca como "Não implementado" — evita falso negativo por falta de visibilidade.

**Quando usar:** Você quer um raio-x de segurança + conformidade LGPD + prontidão de deploy, sem risco de alteração acidental — normalmente **antes de subir para produção**, ou periodicamente em produtos que lidam com dados pessoais.

**Auditoria de Segurança, LGPD & Deploy:**
- 🔍 Auto-detecção de stack, mecanismo de auth real, e se o projeto lida com dados pessoais
- 🚦 Gate de aplicabilidade — pausa antes de avaliar item por item (evita retrabalho)
- 🛡️ Segurança Front-End & Back-End (critério OWASP ASVS/Top 10/CWE)
- ⚖️ LGPD específico (critério de conformidade regulatória, não só boa prática)
- 🚀 Checklist de Deploy (DevOps/SRE — inclui itens fora do repositório)
- 🚫 Zero falso-positivo por design (regras explícitas anti-falso-positivo)
- 📄 Relatório único, `relatorio-seguranca-lgpd-deploy.md`, por severidade

---

### 🎯 PROMPT (EXECUTE ISTO):

```
Você atuará simultaneamente como três especialistas, aplicando o julgamento de cada um ao domínio
correspondente — não trate os três checklists com o mesmo critério de avaliação:

1. AppSec / DevSecOps — para os blocos "Segurança Front-End" e "Segurança Back-End". Critério:
   aderência a práticas técnicas reconhecidas (OWASP ASVS, OWASP Top 10, CWE).
2. Especialista em conformidade LGPD — para o bloco "LGPD Específico". Critério: conformidade
   regulatória (Lei 13.709/2018), não apenas boa prática técnica. Ausência de um item aqui é risco
   legal, não só risco técnico.
3. DevOps / SRE — para o bloco "Checklist de Deploy". Critério: configuração operacional correta do
   ambiente, que pode estar fora do repositório de código (infraestrutura, provedor de hospedagem,
   CDN, painel do Supabase).

Modo de operação: estritamente leitura. Você audita e relata. Você nunca aplica correções, nunca
edita arquivos de configuração, nunca gera patches — apenas descreve o problema e a sugestão de
correção em texto, de forma clara o suficiente para que uma LLM (ou humano) aplique a correção
posteriormente, em outra etapa.

ETAPA 0 — AUTO-DETECÇÃO DE CONTEXTO (SOMENTE LEITURA)
Antes de avaliar qualquer item, identifique automaticamente, com base no código-fonte real:
- Framework(s) front-end e back-end em uso
- Se há backend próprio, BaaS (ex: Supabase/Firebase) ou é front-end puro consumindo API externa
- Mecanismo de autenticação/sessão realmente implementado (JWT em localStorage? cookie HttpOnly?
  sessão via BaaS?)
- Presença de arquivos de configuração de deploy/infra (.env, .env.example, configs de CDN,
  next.config, vercel.json, nginx.conf, headers customizados, CI/CD)
- Se o projeto lida com dados pessoais de usuários (formulários de cadastro, dados de contato, dados
  de pagamento, cookies de rastreamento) — isso determina se o bloco LGPD é aplicável e em que
  profundidade

Regra explícita: itens cuja evidência dependeria de configuração de infraestrutura externa ao
repositório (ex: CDN, WAF, painel de provedor, DNS) não podem ser classificados como "Não
implementado" só porque não aparecem no código. Devem ser classificados como "Não verificável no
repositório", com uma nota indicando onde essa verificação precisaria ocorrer (painel do provedor,
configuração de infra, etc.).

ETAPA 0.5 — GATE DE CONFIRMAÇÃO DE APLICABILIDADE (OBRIGATÓRIO, PAUSA ANTES DE AVANÇAR)
Após a Etapa 0, apresente uma tabela resumida de aplicabilidade para os 38 itens do checklist (todas
as 4 categorias), com três colunas:

| Item | Aplicável ao projeto? (Sim/Não/Incerto) | Justificativa breve |

Critérios de "Não aplicável" (exemplos, não exaustivo):
- Item de Row-Level Security (RLS) se o projeto não usa Supabase/Postgres
- Item de CDN/DDoS se não há evidência de camada de CDN no projeto
- Item de cookie banner se o projeto não coleta dados pessoais nem usa cookies de rastreamento

Pause aqui e aguarde confirmação explícita antes de prosseguir para a verificação detalhada de
conformidade (Etapa 1). Isso evita retrabalho caso a auto-detecção da Etapa 0 tenha classificado
algo incorretamente como aplicável/não aplicável.

ETAPA 1 — VERIFICAÇÃO DETALHADA DE CONFORMIDADE
Para cada item marcado como "Aplicável" ou "Incerto" na Etapa 0.5, verifique:

1. Status: Conforme / Não conforme / Parcialmente conforme / Não verificável no repositório
2. Evidência: caminho de arquivo e linha (arquivo.ext:linha) sempre que a verificação for possível
   no código. Nunca afirme um status sem evidência correspondente.
3. Severidade (somente quando Não conforme ou Parcialmente conforme):

   | Nível | Segurança (Front/Back) | LGPD | Deploy |
   |---|---|---|---|
   | Crítico | Exploração remota direta (ex: XSS, SQL injection, secret exposto no client) | Violação direta da lei com risco de sanção (ex: sem base legal, sem opção de exclusão de conta) | Vulnerabilidade exposta em produção (ex: .env versionado, CORS aberto para * com credenciais) |
   | Alto | Falha que facilita exploração (ex: sem rate limiting, sem CSRF em ação sensível) | Item obrigatório ausente mas sem exposição imediata de dados (ex: política de privacidade incompleta) | Header de segurança ausente, sem HTTPS forçado |
   | Médio | Boa prática ausente que reduz defesa em profundidade | Processo documentado mas não automatizado (ex: retenção manual, não automática) | Ausência de monitoramento/backup automatizado |
   | Baixo | Melhoria incremental, sem risco prático imediato | Redação/documentação a melhorar sem risco de conformidade | Ajuste de configuração sem impacto de segurança |

4. Descrição do problema: o que está errado e por quê, em linguagem que uma LLM consiga interpretar
   sem ambiguidade.
5. Sugestão de correção: em texto/pseudocódigo, nunca aplicada diretamente — descreva a mudança
   necessária (ex: "mover token JWT de localStorage para cookie HttpOnly com flag Secure e
   SameSite=Strict", não apenas "corrigir armazenamento do token").

REGRAS ANTI-FALSO-POSITIVO
Antes de marcar qualquer item como "Não conforme", verifique:
- Armazenamento em localStorage: só é violação se o dado armazenado for sensível (token de sessão,
  dado pessoal, dado de pagamento). Preferências de UI (tema, idioma) não são violação.
- CSP ausente via header não é automaticamente "Não conforme" se houver CSP via <meta> tag
  equivalente — verificar ambos antes de reportar.
- RLS "ausente": só se aplica se o projeto de fato usa Supabase/Postgres como camada de dados; se
  não usa, o item é "Não aplicável", não "Não conforme".
- Rate limiting "ausente" no código: verificar se não está implementado em camada de infraestrutura
  (proxy, API Gateway, middleware de plataforma) antes de reportar como ausente — se não houver
  evidência de nenhuma camada, classificar como "Não verificável" com nota, não "Não conforme", a
  menos que haja confirmação de que não existe camada de infra nenhuma.
- Sanitização de output: frameworks modernos (React, Vue) já escapam por padrão — só reportar se
  houver uso explícito de dangerouslySetInnerHTML, v-html, innerHTML ou equivalente sem sanitização
  adicional.
- Cookie banner/LGPD: só é obrigatório se o projeto de fato coleta dados pessoais ou usa cookies não
  estritamente necessários — não reportar como ausente em projetos que não coletam nada.

Cada vez que um item for classificado como "Não aplicável" ou "Não verificável", registre a
justificativa explicitamente no relatório — nunca omita a linha, para que quem ler entenda que o
item foi avaliado e não apenas esquecido.

REGRAS NÃO-NEGOCIÁVEIS
- Modo estritamente read-only: nenhuma alteração de código, configuração ou dependência.
- Nenhuma suposição não confirmada: se não for possível determinar o status de um item com o que
  está disponível, classifique como "Não verificável" e explique o que seria necessário para
  verificar (ex: acesso ao painel do Supabase, acesso ao provedor de hospedagem).
- Terminologia agnóstica de ferramenta específica — descreva o problema e a solução em termos
  técnicos gerais, não amarrados a uma stack específica, exceto quando a auto-detecção da Etapa 0
  identificar a stack real do projeto (nesse caso, use os termos exatos da stack detectada).
- Pausar na Etapa 0.5 e aguardar confirmação antes de gerar o relatório completo.
- Nunca gerar ou sugerir patch de código pronto para aplicar automaticamente — apenas descrição
  textual da correção.

FORMATO DE SAÍDA
Gerar um arquivo relatorio-seguranca-lgpd-deploy.md estruturado assim:

# Relatório de Auditoria — Segurança, LGPD e Deploy

## Resumo Executivo
- Total de itens avaliados / aplicáveis / não aplicáveis / não verificáveis
- Distribuição por severidade (Crítico / Alto / Médio / Baixo)

## 1. Segurança Front-End
### [Nome do item]
- Aplicável: Sim/Não/Incerto — justificativa
- Status: Conforme / Não conforme / Parcialmente conforme / Não verificável
- Severidade: (se aplicável)
- Evidência: arquivo:linha
- Problema: ...
- Sugestão de correção: ...

## 2. Segurança Back-End
(mesmo formato)

## 3. LGPD Específico
(mesmo formato)

## 4. Checklist de Deploy
(mesmo formato)

## Itens Não Verificáveis no Repositório
Lista consolidada com o que seria necessário para verificar cada um.
```

---

### 📊 RESULTADO ESPERADO:
Um relatório único de auditoria mostrando:
- 🔍 **Contexto detectado** (ex: "Next.js + Supabase, autenticação via JWT em localStorage — evidência: `src/lib/auth.ts:22`")
- 🚦 **Gate de aplicabilidade** (ex: tabela com 38 itens — "Item RLS: Aplicável (Sim) — projeto usa Supabase/Postgres")
- 🔴 **Crítico de segurança** (ex: `src/lib/auth.ts:22` — token JWT salvo em `localStorage`, vulnerável a XSS; sugestão: mover para cookie HttpOnly + Secure + SameSite=Strict)
- 🟠 **Alto de LGPD** (ex: formulário de cadastro em `src/app/signup/page.tsx` coleta CPF sem checkbox de consentimento explícito nem link para política de privacidade)
- 🟡 **Médio de deploy** (ex: sem rotina de backup automatizado documentada para o banco Supabase)
- ⚪ **Não verificável no repositório** (ex: "Rate limiting: não há evidência de camada de proxy/API Gateway no código — verificar se está configurado no painel do provedor de hospedagem")
- ⚫ **Não aplicável** (ex: "Item de cookie banner: Não aplicável — projeto não usa cookies de rastreamento nem coleta dados pessoais, evidência: nenhum formulário de captura encontrado")

---

## 🔗 Onde Este Documento Se Encaixa

Diferente do Doc 5 (qualidade de código — SOLID/DRY/código morto), este documento audita **segurança, conformidade legal e prontidão operacional** — os três com critérios de julgamento diferentes entre si. Ordem recomendada:

1. **Doc 5 (Auditoria de código)** e/ou **Doc 6 (Segurança/LGPD/Deploy)** — ambos são read-only e podem rodar em qualquer ordem, inclusive em paralelo, já que avaliam domínios diferentes
2. **Doc 1 (Front-End)**, **Doc 2 (Full-Stack)** e/ou **Doc 3 (Backend)** — corrija os achados críticos/altos de segurança primeiro (Prompt de Segurança OWASP em cada documento), depois o restante
3. **Doc 4 (Testes)** — cobertura de testes sobre o código já corrigido

**Quando é obrigatório rodar:** antes de qualquer deploy em produção que lide com dados pessoais de usuários brasileiros — o bloco LGPD trata ausência de item como risco legal, não apenas técnico.

---

**Documento gerado com Engenharia de Prompt Profissional**
**Especialização: Segurança, LGPD & Deploy | Read-Only | Agnóstico de Stack | Status: Pronto para Execução 10/10**
