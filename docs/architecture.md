**Aluno:** Nathália Cristine Lemos Santiago

**Repositório do Projeto:** [https://github.com/seu-usuario/seu-repositorio](https://github.com/santiago-nath/documentation_as_code/)


## 1. Mapeamento de Recursos (Cluster & Cloud)

### Cluster Kubernetes (K3s / Magalu Cloud)
- **App API:** Container rodando FastAPI (Python) na porta 8080
- **Ingress Controller:** Nginx para roteamento de tráfego
- **Prometheus:** Coleta de métricas (porta 9090)
- **Grafana:** Dashboard de monitoramento (porta 3000)

### Serviços Externos (Managed Services)
- **PostgreSQL Gerenciado:** Banco de dados DBaaS (porta 5432)
- **Container Registry:** Magalu Cloud Container Registry (MCR)


## 2. Diagrama C2 (Nível de Containers)

graph TD
    User([Usuário / Cliente]) -->|HTTPS / TLS| Ingress[Ingress Controller - Nginx]
    Ingress -->|HTTP / Port 8080| App[API Container - FastAPI]
    App -->|TCP / Port 5432| DB[(PostgreSQL Gerenciado)]
    App -->|HTTP / Port 9090| Prometheus[Prometheus Server]
    Prometheus -->|TCP| Grafana[Grafana Dashboard]


**🔍 Entendendo o diagrama:**
- `graph TD` = Top-Down (de cima para baixo)
- `[ ]` = Container
- `[( )]` = Banco de dados
- `|texto|` = Protocolo e porta
- `-->` = Setas indicando comunicação

### 3.5 - Defina Estilo Arquitetural e RNFs

```markdown
## 3. Estilo Arquitetural e Requisitos Não-Funcionais

### Estilo Arquitetural
**Monolito Modular em Camadas com Implantação Cloud-Native em Contêineres**

A aplicação segue uma arquitetura em camadas (Presentation, Business, Data) executada em contêineres Docker orquestrados por Kubernetes, com serviços gerenciados para persistência e observabilidade.

### Requisitos Não-Funcionais (RNFs)

| RNF | Valor | Descrição |
|-----|-------|-----------|
| **Disponibilidade (SLA)** | 99.9% | Máximo de 8,76 horas de downtime por ano |
| **Latência (P95)** | < 200ms | 95% das requisições respondem em até 200ms |
| **Vazão** | 500 RPS | Suportar 500 requisições por segundo |
| **Custo Mensal** | R$ 150,00 | Teto de gastos (FinOps) |
