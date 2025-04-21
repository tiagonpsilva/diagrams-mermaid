# Fluxogramas com Mermaid

Os fluxogramas são uma das funcionalidades mais utilizadas do Mermaid. Eles são perfeitos para representar processos, tomadas de decisão e fluxos de trabalho.

## Exemplo Básico: Processo de Login

```mermaid
graph TD
    A[Início] --> B{Usuário Cadastrado?}
    B -->|Sim| C[Login]
    B -->|Não| D[Cadastro]
    C --> E{Credenciais Válidas?}
    E -->|Sim| F[Dashboard]
    E -->|Não| C
    D --> C
```

## Exemplo Avançado: Pipeline de CI/CD

```mermaid
graph LR
    A[Commit] --> B[Build]
    B --> C{Testes}
    C -->|Passou| D[Deploy Staging]
    C -->|Falhou| E[Notifica Dev]
    D --> F{Testes E2E}
    F -->|Passou| G[Deploy Prod]
    F -->|Falhou| E
    E --> A
    
    style A fill:#d4ff7d
    style B fill:#85C1E9
    style C fill:#FFE5B4
    style D fill:#85C1E9
    style E fill:#FF9999
    style F fill:#FFE5B4
    style G fill:#98FB98
```

## Exemplo com Subgraphs: Arquitetura de Microserviços

```mermaid
graph TB
    subgraph Frontend
        A[Web App]
        B[Mobile App]
    end
    
    subgraph API Gateway
        C[Load Balancer]
        D[Auth Service]
    end
    
    subgraph Microservices
        E[User Service]
        F[Product Service]
        G[Order Service]
    end
    
    subgraph Database
        H[(User DB)]
        I[(Product DB)]
        J[(Order DB)]
    end
    
    A & B --> C
    C --> D
    D --> E & F & G
    E --> H
    F --> I
    G --> J
```

## Sintaxe Básica

### Nós
- `A[Texto]` - Nó retangular
- `B(Texto)` - Nó arredondado
- `C{Texto}` - Nó de decisão (losango)
- `D([Texto])` - Nó em formato de estádio
- `E[(Texto)]` - Nó de cilindro (database)

### Conexões
- `-->` - Seta padrão
- `---` - Linha sem seta
- `-.->` - Linha pontilhada
- `==>` - Linha grossa
- `-->|texto|` - Seta com texto

### Direções
- `TB` - Top to Bottom
- `BT` - Bottom to Top
- `LR` - Left to Right
- `RL` - Right to Left

## Dicas de Estilização

### Cores e Estilos
```mermaid
graph LR
    A[Padrão]
    B[Colorido]
    C[Com Borda]
    D[Personalizado]
    
    style B fill:#bbf,stroke:#333,stroke-width:2px
    style C stroke:#f66,stroke-width:4px
    style D fill:#f9f,stroke:#333,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
```

### Subgraphs com Estilos
```mermaid
graph TB
    subgraph Produção
        style Produção fill:#f9f,stroke:#333,stroke-width:4px
        A[Server 1]
        B[Server 2]
    end
    
    subgraph Staging
        style Staging fill:#bbf,stroke:#333,stroke-width:4px
        C[Test Server]
    end
    
    A & B --> D[Load Balancer]
    C --> E[Test Load Balancer]
```

## Boas Práticas

1. **Clareza**
   - Use nomes descritivos
   - Mantenha o diagrama simples
   - Agrupe elementos relacionados

2. **Consistência**
   - Use o mesmo estilo para elementos similares
   - Mantenha um padrão de direção
   - Use cores com significado

3. **Organização**
   - Use subgraphs para agrupar logicamente
   - Alinhe elementos quando possível
   - Evite cruzamento de linhas 