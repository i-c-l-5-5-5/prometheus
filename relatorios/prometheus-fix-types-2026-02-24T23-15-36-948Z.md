# Relatório de Análise de Tipos Inseguros

**Gerado em:** 2026-02-24T23:15:36.948Z
**Comando:** `prometheus fix-types`
**Confiança Mínima:** 85%

## 📊 Resumo Executivo

- **Total de Casos:** 1
- **Confiança Média:** 60%

### Distribuição por Categoria

| Categoria | Total | Percentual | Descrição |
|-----------|-------|------------|-----------|
| [SUCESSO] LEGÍTIMO | 0 | 0% | Uso correto - nenhuma ação necessária |
| [AVISO] MELHORÁVEL | 1 | 100% | Pode ser mais específico - revisão manual recomendada |
| [ERRO] CORRIGIR | 0 | 0% | Deve ser substituído - correção necessária |

## [AVISO] Casos com Análise Incerta (<70% confiança)

*Estes casos requerem revisão manual cuidadosa - múltiplas possibilidades detectadas*

### 1. src/licensas/scanner.ts:66 (60%)

**Motivo:** Tipo unknown genérico - análise contextual limitada
**Sugestão:** Analisar fluxo de dados para inferir tipo correto

**Possibilidades Alternativas:**
1. Se vem de API externa: definir interface baseada na resposta esperada
2. Se é callback: especificar assinatura da função
3. Se é config/options: criar interface com campos opcionais
4. Se é polimórfico: considerar discriminated union ou generics

```typescript
const repository = repo == null ? null : typeof repo === 'string' ? repo : (typeof repo === 'object' && repo != null && 'url' in repo ? String((repo as { url: unknown }).url) : null);
```

## [INFO] Lista Completa de Casos

### [AVISO] MELHORAVEL (1 casos)

- **src/licensas/scanner.ts:66** (60%)
  - Tipo unknown genérico - análise contextual limitada
  - [INFO] Analisar fluxo de dados para inferir tipo correto
