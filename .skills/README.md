---
Proveniência e Autoria: Este documento integra o projeto Prometheus (licença MIT).
Nada aqui implica cessão de direitos morais/autorais.
Conteúdos de terceiros não licenciados de forma compatível não devem ser incluídos.
Referências a materiais externos devem ser linkadas e reescritas com palavras próprias.
---
# 🧠 AI Skills System

Este diretório contém os **Skills** do projeto Prometheus. Eles foram projetados para serem consumidos por assistentes de IA (como Cursor, Claude Dev, etc.) para garantir que as contribuições sigam os padrões de qualidade e arquitetura do projeto.

## 📂 Organização

- **`prometheus-dev/`**: 🚀 **[Skill Principal]** Diretrizes de arquitetura, i18n e desenvolvimento de analistas.
- **`code-review/`**: 🧐 Checklist para revisão sistemática de código.
- **`commit-workflow/`**: 📝 Padrões para Conventional Commits e Git.
- **`feature-dev/`**: 🛠️ Workflow estruturado para criação de novas funcionalidades.
- **`pr-review/`**: 📋 Guia para revisão de Pull Requests.
- **`security-check/`**: 🛡️ Auditoria de segurança e prevenção de vulnerabilidades.

## 🤖 Como usar com uma IA

Sempre que pedir para a IA realizar uma tarefa específica, você pode prefixar o pedido com:
_"Use a skill localizada em `.skills/<nome-da-skill>` para me ajudar nesta tarefa."_

Isto garante que a IA:

1.  Siga o workflow correto de desenvolvimento da feature.
2.  Use o sistema de internacionalização (i18n) do Prometheus.
3.  Respeite os padrões de commit do projeto.
