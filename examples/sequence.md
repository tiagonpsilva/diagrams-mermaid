# Diagramas de Sequência com Mermaid

Os diagramas de sequência são excelentes para mostrar a interação entre diferentes componentes de um sistema ao longo do tempo. São particularmente úteis para documentar fluxos de comunicação e protocolos.

## Exemplo Básico: Autenticação de Usuário

```mermaid
sequenceDiagram
    actor User
    participant Frontend
    participant Auth
    participant Database

    User->>Frontend: Login Request
    Frontend->>Auth: Validate Credentials
    Auth->>Database: Query User
    Database-->>Auth: User Data
    Auth-->>Frontend: Token
    Frontend-->>User: Success Response
```

## Exemplo Avançado: Processo de Compra

```mermaid
sequenceDiagram
    actor Customer
    participant Cart
    participant Order
    participant Payment
    participant Stock
    participant Email

    Customer->>Cart: Add Item
    activate Cart
    Cart-->>Customer: Item Added
    deactivate Cart

    Customer->>Cart: Checkout
    activate Cart
    Cart->>Order: Create Order
    activate Order
    
    Order->>Payment: Process Payment
    activate Payment
    alt Payment Successful
        Payment-->>Order: Payment Confirmed
        Order->>Stock: Update Inventory
        Stock-->>Order: Inventory Updated
        Order->>Email: Send Confirmation
        Email-->>Customer: Order Confirmation
    else Payment Failed
        Payment-->>Order: Payment Error
        Order-->>Cart: Order Failed
        Cart-->>Customer: Payment Declined
    end
    deactivate Payment
    deactivate Order
    deactivate Cart
```

## Exemplo com Loops e Condicionais: Polling de Status

```mermaid
sequenceDiagram
    participant Client
    participant Server
    participant Worker

    Client->>Server: Start Job
    activate Server
    Server->>Worker: Queue Job
    Server-->>Client: Job ID
    deactivate Server

    loop Every 5 seconds
        Client->>Server: Check Status
        activate Server
        Server->>Worker: Get Progress
        Worker-->>Server: Progress Update
        alt Job Complete
            Server-->>Client: Result
            break
        else Job Failed
            Server-->>Client: Error
            break
        else In Progress
            Server-->>Client: Progress %
        end
        deactivate Server
    end
```

## Sintaxe Básica

### Participantes
```mermaid
sequenceDiagram
    participant A as Alice
    participant B as Bob
    participant C as Carol
    
    A->>B: Hello Bob
    B->>C: Hello Carol
    C-->>A: Hi Alice
```

### Tipos de Setas
```mermaid
sequenceDiagram
    A->>B: Seta sólida com ponta
    A-->B: Seta tracejada com ponta
    A--->B: Seta tracejada longa
    A-->>B: Seta tracejada com ponta dupla
    A-)B: Seta sólida com ponta aberta
    A--)B: Seta tracejada com ponta aberta
```

### Ativação e Desativação
```mermaid
sequenceDiagram
    participant S as Server
    participant D as Database

    activate S
    S->>+D: Query
    D-->>-S: Result
    deactivate S
```

## Recursos Avançados

### Notas
```mermaid
sequenceDiagram
    participant A
    participant B
    
    Note left of A: Cliente
    Note right of B: Servidor
    Note over A,B: Comunicação HTTP
```

### Cores e Estilos
```mermaid
sequenceDiagram
    participant C as Cliente
    participant S as Servidor
    
    rect rgb(200, 255, 200)
        C->>S: Request
        S-->>C: Response
    end
```

## Boas Práticas

1. **Clareza**
   - Use nomes descritivos para participantes
   - Mantenha mensagens concisas
   - Use notas para explicar detalhes complexos

2. **Organização**
   - Agrupe interações relacionadas
   - Use cores para destacar fluxos importantes
   - Mantenha um fluxo lógico de tempo

3. **Detalhamento**
   - Inclua tratamento de erros
   - Documente estados alternativos
   - Mostre ativação de participantes

4. **Legibilidade**
   - Evite muitos participantes
   - Use aliases para nomes longos
   - Mantenha o diagrama focado em um fluxo específico 