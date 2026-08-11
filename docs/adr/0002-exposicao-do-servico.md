
# ADR 002: Estratégia de Exposição e Roteamento de Tráfego

- **Status:** Aprovado
- **Data:** 2026-08-11

## Contexto
A aplicação precisa ser acessível externamente pelos usuários. Precisamos decidir entre usar um Load Balancer direto ou um Ingress Controller com roteamento baseado em domínio/path.

## Decisão
Adotamos o **Ingress Controller (Nginx)** com roteamento baseado em path e SSL/TLS termination.

## Consequências

### Positivas
- ✅ Roteamento inteligente de tráfego (path-based routing)
- ✅ Terminação SSL centralizada
- ✅ Suporte a múltiplos serviços no mesmo cluster
- ✅ Balanceamento de carga nativo

### Negativas
- ❌ Complexidade adicional de configuração
- ❌ Ponto único de entrada (SPOF - mitigado com replicação)
- ❌ Necessidade de certificados SSL gerenciados
