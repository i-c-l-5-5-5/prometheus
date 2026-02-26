---
description: Ciclo completo de desenvolvimento Prometheus (Build, Lint, Test, Diagnóstico) em modo Turbo
Proveniência e Autoria: Este documento integra o projeto Prometheus (licença MIT).
Nada aqui implica cessão de direitos morais/autorais.
Conteúdos de terceiros não licenciados de forma compatível não devem ser incluídos.
Referências a materiais externos devem ser linkadas e reescritas com palavras próprias.
---

// turbo-all

Este workflow executa todas as etapas de validação do projeto sem interrupções.

1. Instalar dependências se necessário

```bash
npm install
```

2. Limpar builds anteriores e compilar o projeto

```bash
npm run build
```

3. Verificar tipos (TypeScript)

```bash
npm run typecheck
```

4. Executar Linter (ESLint)

```bash
npm run lint
```

5. Rodar todos os testes unitários e de integração

```bash
npm test
```

6. Executar o Diagnóstico oficial do Prometheus no próprio projeto

```bash
node dist/bin/index.js diagnosticar --full --export prometheus-reports/auto-diagnostico.md
```

7. Finalizar com resumo de sucesso
