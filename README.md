# Prompts Unificando

Biblioteca de prompts padronizados para auditoria, refatoração, testes, segurança/LGPD e revisão de copy. Agnóstica de stack e de LLM — funciona com Claude, ChatGPT, Gemini ou qualquer outro modelo, em qualquer IDE.

## Instalação

Nenhuma instalação é necessária — use via `npx` (requer Node.js 18+):

```bash
npx prompts-unificando list
npx prompts-unificando get <id>
npx prompts-unificando get <id> --copy
```

`list` mostra os prompts disponíveis. `get <id>` imprime o conteúdo no terminal; `--copy` envia direto para a área de transferência, pronto para colar em qualquer chat de IA.

## Prompts disponíveis

| ID | Escopo | Edita código |
| --- | --- | --- |
| `frontend` | React/Next.js — código morto, duplicação, performance, tratamento de erros, acessibilidade e SEO | Sim |
| `fullstack` | Next.js full-stack — integração front-back, validação e segurança end-to-end, performance | Sim |
| `backend` | NestJS — arquitetura, banco de dados, segurança OWASP, escalabilidade, documentação de API | Sim |
| `testes` | Cobertura de testes real, qualquer stack — mapeamento de regras de negócio, reconciliação de testes existentes | Sim (gera testes) |
| `auditoria-engenharia` | Diagnóstico de qualidade de código (SOLID, código morto, dependências não usadas) | Não — somente leitura |
| `auditoria-seguranca` | Segurança (OWASP), conformidade LGPD e checklist de deploy | Não — somente leitura |
| `revisao-copy` | Ortografia, gramática e UX copy voltados ao usuário final | Só texto, nunca lógica |

## Como escolher

- **Não sabe onde estão os problemas?** Comece por `auditoria-engenharia`.
- **Vai para produção ou lida com dados pessoais?** Rode `auditoria-seguranca` antes do deploy.
- **Projeto React/Next.js sem backend próprio?** Use `frontend`.
- **Next.js com API Routes no mesmo repositório?** Use `fullstack` (e `frontend` se quiser focar só na camada visual).
- **Backend NestJS em repositório separado?** Use `backend`.
- **Já refatorou e quer cobertura de testes real?** Use `testes` — rode por último, depois da arquitetura estabilizar.
- **Gerou ou revisou copy com IA?** Use `revisao-copy` a qualquer momento.

## Fluxo recomendado

```
1. Diagnóstico (opcional, sem risco)
   auditoria-engenharia + auditoria-seguranca

2. Refatoração (conforme a stack)
   frontend e/ou fullstack e/ou backend

3. Testes
   testes — depois que a arquitetura estiver estável

4. Copy
   revisao-copy — a qualquer momento após gerar conteúdo com IA
```

Rodar o diagnóstico primeiro evita refatorar às cegas: os dois prompts de auditoria não alteram nada, apenas mapeiam os problemas reais antes de você decidir onde investir esforço.

## Como usar um prompt

1. `npx prompts-unificando get <id> --copy`
2. Cole no chat da sua LLM de preferência
3. Aguarde a análise — o resultado é um relatório estruturado com achados, soluções e prioridade
4. Aplique as mudanças e, se o documento tiver múltiplos prompts, execute o próximo na sequência indicada dentro do próprio arquivo

## Licença

MIT
