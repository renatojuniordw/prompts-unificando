# 📚 Guia Completo de Refatoração - Índice & Navegação

**Prompts Otimizados para React/Next.js, Full-Stack e NestJS | Versão 10/10**

---

## 🎯 O QUE VOCÊ TEM

Você agora possui **5 documentos especializados** para auditoria, refatoração e teste de projetos:

### 📄 **Documento 1: Front-End (React/Next.js)**

**Arquivo:** `1_FrontEnd_React_NextJS_Otimizado.md`

Especializado em refatoração de **camada frontend**:

- Limpeza de código morto
- Detecção de duplicação
- Otimização de performance (Core Web Vitals)
- Tratamento de erros com bom UX
- Separação de responsabilidades
- Otimizações Next.js específicas
- Acessibilidade & SEO

**Quando usar:** Você está trabalhando em um projeto **React ou Next.js** focado em melhorar a **qualidade do frontend**

**Total de prompts:** 7  
**Tempo de análise:** ~110-140 min  
**Tempo de implementação:** ~25-50h

---

### 📄 **Documento 2: Full-Stack (Next.js)**

**Arquivo:** `2_FullStack_NextJS_Otimizado.md`

Especializado em refatoração **full-stack em um único repositório Next.js**:

- Integração front-back & fluxo de dados
- Validação & segurança end-to-end (OWASP)
- Performance end-to-end
- Tratamento de erros (full-stack)
- Testes & observabilidade

**Quando usar:** Você está trabalhando em um projeto **Next.js com API Routes** e quer **otimizar a comunicação entre frontend e backend** no mesmo repositório

**Total de prompts:** 5  
**Tempo de análise:** ~75-100 min  
**Tempo de implementação:** ~20-41h

---

### 📄 **Documento 3: Backend (NestJS)**

**Arquivo:** `3_Backend_NestJS_Otimizado.md`

Especializado em refatoração de **backend profissional com NestJS**:

- Arquitetura & design patterns NestJS
- Banco de dados & query optimization
- Segurança backend (OWASP Top 10)
- Performance & escalabilidade
- Testes & observabilidade backend
- API documentation & contract

**Quando usar:** Você está trabalhando em um **projeto NestJS em repositório separado** e quer **arquitetura robusta, segura e escalável**

**Total de prompts:** 6  
**Tempo de análise:** ~95-130 min  
**Tempo de implementação:** ~27-52h

---

### 📄 **Documento 4: Testes & Cobertura (Agnóstico de Stack)**

**Arquivo:** `4_Testes_Cobertura_Otimizado.md`

Especializado em **cobertura de testes 100%**, em qualquer linguagem/framework:

- Leitura autônoma do diretório (lê o projeto, não pede código colado)
- Mapeamento ultra-específico de regras de negócio (`business-rules.md`)
- Reconciliação de testes existentes (corrige testes que validam bugs, renomeia, remove redundantes)
- Árvore de branches completa + Pirâmide de Testes (Unit/Integration/E2E)
- Modo projeto extenso com plano de fases autônomo (`test-plan.md`)

**Quando usar:** Você já refatorou o projeto (Docs 1-3) e quer **cobertura de testes real** que encontra defeitos, não só "passa" — em qualquer stack (não impõe framework de teste próprio, usa o que já existe no projeto)

**Total de prompts:** 1 (fluxo completo)  
**Tempo de análise:** varia com o tamanho do projeto (modo padrão: 2 pontos de confirmação; modo projeto extenso: execução por fases sem parada)  
**Tempo de implementação:** varia com a cobertura atual do projeto

---

### 📄 **Documento 5: Auditoria de Engenharia (Read-Only, Agnóstico de Stack)**

**Arquivo:** `5_Auditoria_Engenharia_Software_ReadOnly.md`

Especializado em **diagnóstico técnico sem nenhuma alteração de código**:

- Detecção automática de stack via evidência de arquivo
- Avaliação SOLID, DRY, KISS, YAGNI, Clean Code — cada achado com arquivo:linha
- Código morto com checklist anti-falso-positivo
- Dependências não usadas ou duplicadas
- Cobertura de testes por statement e branch (se aplicável)
- Relatório único classificado por severidade (Crítico/Alto/Médio/Baixo)

**Quando usar:** Você ainda não sabe onde estão os problemas reais do projeto e quer um **diagnóstico objetivo, sem risco** (zero edição, zero commit, zero push) antes de decidir onde investir esforço — normalmente o **primeiro documento a rodar**, antes dos Docs 1-4

**Total de prompts:** 1 (fluxo completo)  
**Tempo de análise:** varia com o tamanho do projeto  
**Tempo de implementação:** N/A (documento não corrige nada, apenas diagnostica)

---

## 🗺️ COMO ESCOLHER QUAL DOCUMENTO USAR

```
┌─ Não sabe onde estão os problemas ainda?
│  └─ Documento 5: Auditoria (Read-Only) ✅ — rode primeiro, sem risco
│
┌─ Qual é sua stack?
│
├─ React ou Next.js (sem backend separado)
│  └─ Documento 1: Front-End (React/Next.js) ✅
│
├─ Next.js com API Routes integradas
│  └─ Documento 2: Full-Stack (Next.js) ✅
│  │  (se também quer otimizar API Routes nesse projeto)
│  │
│  └─ Documento 1: Front-End (React/Next.js) ✅
│     (se foca apenas em frontend)
│
└─ NestJS em repositório separado
   └─ Documento 3: Backend (NestJS) ✅
      (+ use Documento 1 ou 2 para frontend que consome)

Depois de refatorar (qualquer combinação acima):
└─ Quer cobertura de testes real sobre o código já refatorado?
   └─ Documento 4: Testes & Cobertura ✅ (qualquer stack)
```

---

## 📊 TABELA COMPARATIVA

| Aspecto                 | Doc 1: Front-End       | Doc 2: Full-Stack   | Doc 3: Backend         | Doc 4: Testes                        | Doc 5: Auditoria                  |
| ----------------------- | ---------------------- | ------------------- | ---------------------- | ------------------------------------- | ---------------------------------- |
| **Foco**                | React/Next.js frontend | Next.js completo    | NestJS backend         | Cobertura de testes (qualquer stack) | Diagnóstico read-only (qualquer stack) |
| **Prompts**             | 7                      | 5                   | 6                      | 1 (fluxo completo)                    | 1 (fluxo completo)                 |
| **Tempo de análise**    | 110-140 min            | 75-100 min          | 95-130 min             | Varia com o tamanho do projeto        | Varia com o tamanho do projeto     |
| **Tempo implementação** | 25-50h                 | 20-41h              | 27-52h                 | Varia com a cobertura atual           | N/A (não corrige nada)             |
| **Performance**         | Front-end metrics      | End-to-end          | Backend optimization   | —                                      | —                                   |
| **Segurança**           | XSS, CSRF              | Full-stack OWASP    | OWASP Top 10           | —                                      | —                                   |
| **Database**            | Não                    | Sim (básico)        | Sim (profundo)         | —                                      | —                                   |
| **API Routes**          | Não                    | Sim                 | Não (NestJS routes)    | —                                      | —                                   |
| **Testes**              | Unit, Integration, E2E | Unit, Integration   | Unit, Integration, E2E | Unit, Integration, E2E (100%)         | Reporta cobertura existente        |
| **Edita código?**       | Sim                    | Sim                 | Sim                    | Sim (gera testes)                     | **Não — somente leitura**          |
| **Melhor para**         | Frontend puro          | Monorepo full-stack | Backend separado       | Qualquer projeto já refatorado        | Diagnóstico inicial, sem risco     |

---

## 🔄 FLUXO RECOMENDADO

### Cenário 0: Não Sei Por Onde Começar (Diagnóstico Primeiro)

```
┌─────────────────────────────────────────┐
│ 0. Auditoria (Doc 5, read-only)         │ ← Start here
│    (fluxo único, sem risco)             │ (descobre os problemas reais)
└─────────────────────────────────────────┘
                    ↓
      (com o relatório em mãos, escolha
       Doc 1, 2 e/ou 3 para corrigir)
                    ↓
┌─────────────────────────────────────────┐
│ 1-3. Refatoração (Doc 1, 2 e/ou 3)      │
└─────────────────────────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│ 4. Testes & Cobertura (Doc 4)           │
└─────────────────────────────────────────┘
```

**Por quê começar pela auditoria?** Ela não edita nada — é diagnóstico puro. Você usa o relatório para decidir com dados quais dos Docs 1-3 valem o esforço, em vez de adivinhar.

---

### Cenário 1: Next.js Full-Stack (Frontend + API Routes)

```
┌─────────────────────────────────────────┐
│ 1. Front-End (React/Next.js)            │ ← Start here
│    (7 prompts, 110-140 min)             │
└─────────────────────────────────────────┘
                    ↓
         (ou use Documento 2 se
          quer otimizar API Routes)
                    ↓
┌─────────────────────────────────────────┐
│ 2. Full-Stack (Next.js)                 │ ← Execute depois
│    (5 prompts, 75-100 min)              │ (para otimizar integração)
└─────────────────────────────────────────┘
```

**Total:** ~185-240 minutos de análise + ~45-91 horas de implementação

---

### Cenário 2: Next.js Frontend + NestJS Backend (Repositórios Separados)

```
┌─────────────────────────────────────────┐
│ 1. Back-End (NestJS)                    │ ← Start here
│    (6 prompts, 95-130 min)              │ (base arquitetural)
└─────────────────────────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│ 2. Front-End (React/Next.js)            │ ← Execute depois
│    (7 prompts, 110-140 min)             │ (consome API)
└─────────────────────────────────────────┘
                    ↓
          (opcional) Otimizar integração
                    ↓
┌─────────────────────────────────────────┐
│ 3. Full-Stack Review                    │ ← Para reviews
│    Prompts 1-2 do Doc 2                 │ (integração)
│    (2 prompts, 30-40 min)               │
└─────────────────────────────────────────┘
```

**Total:** ~235-310 minutos de análise + ~52-103 horas de implementação

---

### Cenário 3: Projeto NestJS Puro (Sem Frontend Web)

```
┌─────────────────────────────────────────┐
│ Back-End (NestJS)                       │
│ (6 prompts, 95-130 min)                 │
└─────────────────────────────────────────┘
```

**Total:** ~95-130 minutos de análise + ~27-52 horas de implementação

---

### Cenário 4: Cobertura de Testes (Após Qualquer Refatoração Acima)

```
┌─────────────────────────────────────────┐
│ 1-3. Refatoração (Doc 1, 2 e/ou 3)      │ ← Já executado
└─────────────────────────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│ 4. Testes & Cobertura (Doc 4)           │ ← Roda por último
│    (fluxo único, tempo varia)           │ (testa o código já refatorado)
└─────────────────────────────────────────┘
```

**Por quê por último?** Testar antes de refatorar significa reescrever os testes depois que a arquitetura mudar. Doc 4 assume que o código já está na forma final.

---

## 🎯 ORDEM DE EXECUÇÃO POR PRIORIDADE

Independente do documento, **sempre siga essa ordem**:

### 🔎 DIAGNÓSTICO (Opcional, mas Recomendado)

0. **Auditoria:** Doc 5 (Read-Only, qualquer stack)

→ **Por quê?** Não edita nada — mapeia os problemas reais antes de você decidir onde investir esforço nos passos abaixo.

### 🚨 CRÍTICO (Segurança)

1. **Back-End:** Prompt 3 (Segurança OWASP)
2. **Front-End:** Prompt 4 (Tratamento de Erros)
3. **Full-Stack:** Prompt 2 (Segurança E2E)

→ **Por quê?** Uma vulnerabilidade cancela todas as otimizações. Segurança primeiro.

### 🏗️ ARQUITETURA

4. **Back-End:** Prompt 1 (Arquitetura NestJS)
5. **Front-End:** Prompt 5 (Separação de Responsabilidades)
6. **Full-Stack:** Prompt 1 (Integração Front-Back)

→ **Por quê?** Código bem arquitetado facilita todas as otimizações seguintes.

### 📊 BANCO DE DADOS

7. **Back-End:** Prompt 2 (Database Optimization)
8. **Full-Stack:** Incluído no Prompt 3 (Performance E2E)

→ **Por quê?** Database é geralmente o gargalo. Maior ROI.

### ⚡ PERFORMANCE

9. **Front-End:** Prompts 1, 2, 3 (Limpeza, Duplicação, Performance)
10. **Back-End:** Prompt 4 (Performance & Escalabilidade)
11. **Full-Stack:** Prompt 3 (Performance E2E)

→ **Por quê?** Com base sólida, agora otimiza o que importa.

### 🧪 TESTES & OBSERVABILIDADE

12. **Back-End:** Prompt 5 (Testes & Observabilidade)
13. **Front-End:** Incluído em Prompts 4 & 7
14. **Full-Stack:** Prompt 5 (Testes & Observabilidade)

→ **Por quê?** Garante que mudanças não quebram nada.

### 📋 DOCUMENTAÇÃO & CONTRACT

15. **Back-End:** Prompt 6 (API Documentation)
16. **Front-End:** Prompt 7 (Acessibilidade & SEO)

→ **Por quê?** Último passo antes de testes. Frontend e terceiros dependem disso.

### 🧪 COBERTURA DE TESTES

17. **Testes:** Doc 4 (Cobertura 100%, agnóstico de stack)

→ **Por quê?** Roda por último — testa o código já refatorado, arquitetado, seguro e documentado, evitando reescrever testes por causa de mudanças posteriores.

---

## 💡 COMO EXECUTAR OS PROMPTS

### Passo 1: Leia o Documento

Abra o arquivo `.md` correspondente ao seu projeto.

### Passo 2: Escolha o Prompt

Cada prompt tem seção **"O QUE ESTE PROMPT FAZ"** e **"PROMPT (EXECUTE ISTO)"**.

### Passo 3: Execute no seu Chat IA

- Copie o **bloco de código** da seção `🎯 PROMPT (EXECUTE ISTO)`
- Cole no seu chat com a IA (Claude, ChatGPT, etc)
- Aguarde a análise (geralmente 2-10 minutos)

### Passo 4: Salve o Resultado

O resultado de cada prompt é um **relatório estruturado** com:

- ✂️ Problemas encontrados (em ordem de prioridade)
- 🔧 Soluções concretas
- 📊 Estimativa de impacto
- 🛠️ Exemplos de implementação

**Salve esse resultado!** Use para refatoração.

### Passo 5: Execute Sequencialmente

- Não pule prompts
- Cada prompt presume que os anteriores foram completados
- Espere terminar um antes de rodar o próximo

---

## 📈 ESTIMATIVA DE TEMPO

### Se você quer análise completa (todos os documentos)

**Frontend + Full-Stack + Backend:**

- Análise: ~400-470 minutos (6.5-8 horas)
- Implementação: ~72-147 horas (1.5-3 semanas @40h/week)

**Recomendação:** Faça em sprints. Não tente tudo de uma vez.

---

### Se você quer análise focada (um documento)

**Apenas Front-End:**

- Análise: ~110-140 minutos (2-2.5 horas)
- Implementação: ~25-50 horas (1 semana @40h/week)

**Apenas Full-Stack:**

- Análise: ~75-100 minutos (1.5-2 horas)
- Implementação: ~20-41 horas (1 semana @40h/week)

**Apenas Backend:**

- Análise: ~95-130 minutos (1.5-2.5 horas)
- Implementação: ~27-52 horas (1.5 semanas @40h/week)

---

## 🔍 ENCONTRAR INFORMAÇÕES RÁPIDO

### Por Stack

- **React puro:** Doc 1 (Front-End)
- **Next.js (frontend):** Doc 1 (Front-End)
- **Next.js (com API Routes):** Doc 1 + Doc 2 (Front-End + Full-Stack)
- **NestJS:** Doc 3 (Backend)
- **Next.js + NestJS:** Doc 1 + Doc 2 + Doc 3
- **Qualquer stack, quero cobertura de testes:** Doc 4 (Testes), depois de refatorar
- **Qualquer stack, não sei onde estão os problemas:** Doc 5 (Auditoria, read-only) — comece por aqui

### Por Tópico

**Performance:**

- Front-End → Prompt 3 (Performance Front-End)
- Back-End → Prompt 4 (Performance & Escalabilidade)
- Full-Stack → Prompt 3 (Performance E2E)

**Segurança:**

- Front-End → Prompt 4 (Erros), Prompt 7 (A11y)
- Back-End → Prompt 3 (Segurança OWASP) **← CRÍTICO**
- Full-Stack → Prompt 2 (Segurança E2E) **← CRÍTICO**

**Banco de Dados:**

- Back-End → Prompt 2 (Database Optimization) **← CRÍTICO**
- Full-Stack → Incluído em Prompt 3

**Testes:**

- Front-End → Incluído em Prompts 4 & 7
- Back-End → Prompt 5 (Testes & Observabilidade)
- Full-Stack → Prompt 5 (Testes & Observabilidade)
- Cobertura 100% (qualquer stack) → Doc 4 (Testes & Cobertura) **← use por último**

---

## ✅ CHECKLIST DE USO

- [ ] Identifiquei qual documento(s) preciso
- [ ] Entendi a ordem correta de execução
- [ ] Li o "O QUE ESTE PROMPT FAZ" para cada prompt
- [ ] Copiei o prompt correto para o chat
- [ ] Aguardei a análise completa
- [ ] Salvei o resultado em um arquivo
- [ ] Criei um plano de implementação
- [ ] Comecei com os CRÍTICOS (Segurança, Database)
- [ ] Testo cada mudança antes de prosseguir
- [ ] Documentei as mudanças

---

## 🚀 PRONTO PARA COMEÇAR?

### Qual é seu cenário?

**A) React/Next.js Frontend**
→ Abra: `1_FrontEnd_React_NextJS_Otimizado.md`
→ Comece: Prompt 1 (Análise de Código Morto)

**B) Next.js Full-Stack (Frontend + API)**
→ Abra: `2_FullStack_NextJS_Otimizado.md` (depois `1_FrontEnd_React_NextJS_Otimizado.md`)
→ Comece: Prompt 2 (Validação & Segurança)

**C) NestJS Backend**
→ Abra: `3_Backend_NestJS_Otimizado.md`
→ Comece: Prompt 3 (Segurança OWASP)

**D) Já refatorei e quero cobertura de testes 100%**
→ Abra: `4_Testes_Cobertura_Otimizado.md`
→ Comece: o prompt único do documento (funciona em qualquer stack)

**E) Não sei onde estão os problemas ainda**
→ Abra: `5_Auditoria_Engenharia_Software_ReadOnly.md`
→ Comece: o prompt único do documento (read-only, sem risco, funciona em qualquer stack)

**F) Não tenho certeza**
→ Responda essas 3 perguntas:

1. Seu código é React/Next.js ou NestJS?
2. O backend é em API Routes ou repositório separado?
3. Quer otimizar frontend, backend ou ambos?

→ Use a tabela de **"COMO ESCOLHER QUAL DOCUMENTO USAR"** acima

---

## 📞 SUPORTE

Se durante a execução dos prompts você:

**Tiver dúvidas sobre qual prompt rodar:**
→ Consulte a seção **"Por Tópico"** acima

**Não entender um resultado:**
→ O resultado tem "📊 RESULTADO ESPERADO" - compare com seu projeto

**Precisar escalar escopo:**
→ Execute os prompts de outro documento também

**Achar que um prompt não funcionou:**
→ Tente novamente, com mais contexto sobre seu projeto

---

## 📚 ESTRUTURA DOS DOCUMENTOS

Cada documento segue esse padrão:

```
📄 Documento
├─ 📖 O QUE ESTE PROMPT FAZ (contexto)
├─ 🎯 PROMPT (código para copiar)
├─ 📊 RESULTADO ESPERADO (exemplos)
├─ ... (próximos prompts)
├─ 🎯 ORDEM DE EXECUÇÃO
├─ 📊 TABELA RESUMO
└─ 💡 DICAS
```

Sempre leia **"O QUE ESTE PROMPT FAZ"** antes de executar.

---

## 🎁 BÔNUS

Todos os prompts foram:
✅ Otimizados por engenheiro de prompt profissional  
✅ Testados e validados (10/10)  
✅ Escritos em inglês (melhor para LLMs)  
✅ Com explicações em português  
✅ Estruturados com deliverables claros  
✅ Incluindo exemplos de código  
✅ Com priorização (Critical → High → Medium)

---

**Última atualização:** 2026-05-10  
**Versão:** 10/10 | Production-Ready  
**Status:** Pronto para Execução ✅

---

_Bora turbinar seu código, Renatinho! 🚀_
