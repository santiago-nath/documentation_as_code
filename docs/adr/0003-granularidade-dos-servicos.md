
# ADR 003: Granularidade da Aplicação

- **Status:** Aprovado
- **Data:** 2026-08-11

## Contexto
Precisamos definir se a aplicação será um **monolito** (single deployable unit) ou **microsserviços** (múltiplos serviços independentes).

## Decisão
Adotamos a abordagem de **Monolito Modular** com implantação em contêineres.

## Consequências

### Positivas
- ✅ Menor complexidade de desenvolvimento inicial
- ✅ Comunicação intra-processo (mais rápida)
- ✅ Fácil debug e testes end-to-end
- ✅ Single codebase (mais fácil onboarding)

### Negativas
- ❌ Escalabilidade limitada (toda aplicação escala junta)
- ❌ Dificuldade de isolar falhas
- ❌ Desafios para times grandes (concorrência de código)
