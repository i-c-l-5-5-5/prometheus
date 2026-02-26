---
name: Prometheus Development
description: Diretrizes específicas para o desenvolvimento e manutenção do ecossistema Prometheus
Proveniência e Autoria: Este documento integra o projeto Prometheus (licença MIT).
Nada aqui implica cessão de direitos morais/autorais.
Conteúdos de terceiros não licenciados de forma compatível não devem ser incluídos.
Referências a materiais externos devem ser linkadas e reescritas com palavras próprias.
---

# 🔎 Prometheus Development Skill

Esta skill define os padrões técnicos e arquiteturais para o **Prometheus CLI**. Use-a sempre que for criar novos analistas, modificar o core ou expandir a infraestrutura.

## 🏗️ Padrões de Arquitetura

1.  **Imutabilidade do Core**: O núcleo do motor (`src/core`) deve ser agnóstico aos analistas. Use Injeção de Dependências (IoC) para passar as técnicas/analistas.
2.  **Workers & Performance**: Qualquer operação pesada de análise deve suportar o `WorkerPool`. Evite bloquear o loop de eventos na thread principal.
3.  **Parser/AST**: Prefira o uso do Babel para parsing JS/TS. Quando lidar com outras linguagens, use os parsers específicos em `src/core/parsing`.
4.  **Internacionalização (i18n)**: Nunca use strings literais fixas para mensagens ao usuário. Use o helper `createI18nMessages` em `src/shared/helpers/i18n.ts`.

## 🧪 Desenvolvimento de Analistas (Técnicas)

Ao criar um novo analista em `src/analistas`:

- [ ] **Interface**: Siga a interface `Analista` definida em `src/types`.
- [ ] **Mensagens**: Crie um arquivo de mensagens dedicado em `src/core/messages/analistas/` com suporte PT/EN.
- [ ] **Performance**: Certifique-se de que a análise é eficiente (evite recursão profunda sem limite).
- [ ] **Falsos Positivos**: Implemente lógica de confiança (`confidence`) para filtrar ruído.
- [ ] **Testes**: Adicione testes em `tests/analistas/` cobrindo cenários reais e edge cases.

## 🛡️ Segurança e Integridade

- **Guardian**: Ao modificar arquivos críticos da estrutura, lembre-se de rodar/atualizar o baseline do `guardian`.
- **Sanitização**: Sempre valide caminhos (`paths`) para evitar ataques de _Path Traversal_.

## 🚀 Workflow de Modificação

1.  Mude o código.
2.  Rode `npm run typecheck` e `npm run lint`.
3.  Rode os testes afetados: `npx vitest tests/...`.
4.  Se houver mudanças em mensagens, adicione as traduções em Inglês.
5.  Se mudou o binário ou estrutura, rode `npm run build` e teste localmente com `node dist/bin/index.js`.

---

**Prioridade**: Qualidade de código e clareza no diagnóstico são mais importantes que velocidade bruta.
