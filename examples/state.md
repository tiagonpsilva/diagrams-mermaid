# Diagramas de Estado com Mermaid

Os diagramas de estado são úteis para modelar o comportamento de um sistema, mostrando como ele transita entre diferentes estados em resposta a eventos.

## Exemplo Básico: Pedido de E-commerce

```mermaid
stateDiagram-v2
    [*] --> Carrinho
    Carrinho --> Checkout: Finalizar Compra
    Checkout --> Pagamento: Confirmar Dados
    Pagamento --> ProcessandoPagamento: Pagar
    ProcessandoPagamento --> PedidoConfirmado: Pagamento Aprovado
    ProcessandoPagamento --> Checkout: Pagamento Recusado
    PedidoConfirmado --> EmPreparacao: Iniciar Preparação
    EmPreparacao --> Enviado: Despachar
    Enviado --> Entregue: Confirmar Entrega
    Entregue --> [*]
```

## Exemplo Avançado: Máquina de Café

```mermaid
stateDiagram-v2
    [*] --> Pronto: Ligar
    
    state Pronto {
        [*] --> Aguardando
        Aguardando --> Selecionando: Inserir Moeda
        Selecionando --> Aguardando: Timeout
    }
    
    state Preparando {
        [*] --> MoendoCafe
        MoendoCafe --> AquecendoAgua
        AquecendoAgua --> Misturando
        Misturando --> [*]
    }
    
    Pronto --> Preparando: Selecionar Bebida
    Preparando --> Pronto: Bebida Pronta
    
    state Manutencao {
        [*] --> VerificandoInsumos
        VerificandoInsumos --> LimpandoSistema
        LimpandoSistema --> [*]
    }
    
    Pronto --> Manutencao: Iniciar Manutenção
    Manutencao --> Pronto: Finalizar Manutenção
    
    Pronto --> [*]: Desligar
```

## Exemplo com Choice: Processo de Aprovação

```mermaid
stateDiagram-v2
    [*] --> Submetido
    Submetido --> EmAnalise: Iniciar Análise
    
    state EmAnalise {
        [*] --> VerificacaoDocumentos
        VerificacaoDocumentos --> AnaliseDados
        AnaliseDados --> [*]
    }
    
    state choice <<choice>>
    EmAnalise --> choice: Análise Concluída
    choice --> Aprovado: Score > 700
    choice --> EmRevisao: Score > 500
    choice --> Rejeitado: Score <= 500
    
    EmRevisao --> Aprovado: Aprovação Manual
    EmRevisao --> Rejeitado: Rejeição Manual
    
    Aprovado --> [*]
    Rejeitado --> [*]
```

## Sintaxe Básica

### Estados Simples
```mermaid
stateDiagram-v2
    [*] --> Inicio
    Inicio --> Processando
    Processando --> Fim
    Fim --> [*]
```

### Estados Compostos
```mermaid
stateDiagram-v2
    [*] --> Ativo
    
    state Ativo {
        [*] --> Ocioso
        Ocioso --> Trabalhando
        Trabalhando --> Ocioso
    }
    
    Ativo --> [*]
```

### Transições
```mermaid
stateDiagram-v2
    Inicio --> Meio: Evento
    Meio --> Fim: [Condição]
    Fim --> Inicio: Evento [Condição] / Ação
```

## Recursos Avançados

### Fork e Join
```mermaid
stateDiagram-v2
    [*] --> Inicio
    state fork <<fork>>
    Inicio --> fork
    fork --> Processo1
    fork --> Processo2
    
    state join <<join>>
    Processo1 --> join
    Processo2 --> join
    join --> Fim
    Fim --> [*]
```

### História
```mermaid
stateDiagram-v2
    [*] --> Ativo
    
    state Ativo {
        [*] --> Configuracao
        Configuracao --> Operando
        Operando --> EmPausa
    }
    
    Ativo --> Suspenso: Suspender
    Suspenso --> Ativo[H]: Retomar
```

## Boas Práticas

1. **Clareza**
   - Use nomes descritivos para estados
   - Mantenha transições claras
   - Documente condições importantes

2. **Organização**
   - Agrupe estados relacionados
   - Use estados compostos para simplificar
   - Mantenha o fluxo lógico

3. **Detalhamento**
   - Inclua eventos relevantes
   - Especifique condições
   - Documente ações importantes

4. **Legibilidade**
   - Evite muitas transições cruzadas
   - Use estados compostos para reduzir complexidade
   - Mantenha o diagrama focado

5. **Validação**
   - Verifique estados sem saída
   - Confirme estados iniciais e finais
   - Valide todas as transições possíveis 