
# ADR 001: Utilização de Banco de Dados Gerenciado Fora do Cluster K8s

- **Status:** Aprovado
- **Data:** 2026-08-11

## Contexto
A aplicação precisa persistir dados relacionais com alta confiabilidade e backups automáticos. Precisamos decidir se o PostgreSQL rodará dentro do cluster Kubernetes (como StatefulSet) ou se usaremos um serviço gerenciado (DBaaS).

## Decisão
Optamos por utilizar o **PostgreSQL Gerenciado (DBaaS)** fora do cluster Kubernetes.

## Consequências

### Positivas
- ✅ Backups automáticos e point-in-time recovery
- ✅ Failover automático em caso de falhas
- ✅ Redução da complexidade de gerenciamento de volumes persistentes
- ✅ Equipe não precisa se preocupar com manutenção do banco

### Negativas
- ❌ Custo adicional (aproximadamente R$ 80/mês)
- ❌ Dependência do provedor de nuvem
- ❌ Latência adicional (rede externa)
