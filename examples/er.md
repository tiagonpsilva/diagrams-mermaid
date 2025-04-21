# Diagramas Entidade-Relacionamento com Mermaid

Os diagramas ER são essenciais para modelagem de banco de dados, mostrando entidades, seus atributos e relacionamentos.

## Exemplo Básico: Sistema de Biblioteca

```mermaid
erDiagram
    LIVRO ||--o{ EMPRESTIMO : possui
    LIVRO {
        string ISBN PK
        string titulo
        string autor
        date dataPublicacao
        string editora
        int copias
    }
    USUARIO ||--o{ EMPRESTIMO : realiza
    USUARIO {
        int ID PK
        string nome
        string email
        string telefone
        date dataCadastro
    }
    EMPRESTIMO {
        int ID PK
        string ISBN FK
        int usuarioID FK
        date dataEmprestimo
        date dataDevolucao
        string status
    }
```

## Exemplo Avançado: Sistema de E-commerce

```mermaid
erDiagram
    CLIENTE ||--o{ PEDIDO : faz
    CLIENTE {
        int ID PK
        string nome
        string email
        string CPF
        string telefone
    }
    
    PEDIDO ||--|{ ITEM_PEDIDO : contem
    PEDIDO {
        int ID PK
        int clienteID FK
        date dataPedido
        decimal valorTotal
        string status
        int enderecoEntregaID FK
    }
    
    PRODUTO ||--o{ ITEM_PEDIDO : possui
    PRODUTO {
        int ID PK
        string nome
        string descricao
        decimal preco
        int categoriaID FK
        int estoqueAtual
    }
    
    ITEM_PEDIDO {
        int pedidoID FK
        int produtoID FK
        int quantidade
        decimal precoUnitario
        decimal subtotal
    }
    
    CATEGORIA ||--|{ PRODUTO : classifica
    CATEGORIA {
        int ID PK
        string nome
        string descricao
    }
    
    ENDERECO }|--|| CLIENTE : possui
    ENDERECO {
        int ID PK
        int clienteID FK
        string logradouro
        string numero
        string complemento
        string cidade
        string estado
        string CEP
    }
```

## Exemplo com Herança: Sistema de RH

```mermaid
erDiagram
    FUNCIONARIO ||--o{ PONTO : registra
    FUNCIONARIO {
        int ID PK
        string nome
        string CPF
        date dataNascimento
        date dataAdmissao
        string cargo
        decimal salarioBase
    }
    
    DESENVOLVEDOR ||--|| FUNCIONARIO : e
    DESENVOLVEDOR {
        int funcionarioID PK,FK
        string linguagens
        string nivel
        string squad
    }
    
    GERENTE ||--|| FUNCIONARIO : e
    GERENTE {
        int funcionarioID PK,FK
        string departamento
        decimal bonus
    }
    
    PONTO {
        int ID PK
        int funcionarioID FK
        datetime entrada
        datetime saida
        string tipo
    }
    
    PROJETO }o--|| GERENTE : gerencia
    PROJETO {
        int ID PK
        string nome
        date dataInicio
        date dataFim
        decimal orcamento
        int gerenteID FK
    }
    
    PROJETO_DESENVOLVEDOR }o--|| DESENVOLVEDOR : participa
    PROJETO_DESENVOLVEDOR {
        int projetoID FK
        int desenvolvedorID FK
        date dataInicio
        date dataFim
        string papel
    }
```

## Sintaxe Básica

### Entidades e Atributos
```mermaid
erDiagram
    ENTIDADE {
        tipo atributo
        string nome PK "Chave Primária"
        int idade
        date nascimento
    }
```

### Relacionamentos
```mermaid
erDiagram
    ENTIDADE1 ||--|| ENTIDADE2 : um-para-um
    ENTIDADE1 ||--|{ ENTIDADE2 : um-para-muitos
    ENTIDADE1 }|--|{ ENTIDADE2 : muitos-para-muitos
    ENTIDADE1 |o--|| ENTIDADE2 : um-opcional-para-um
```

## Recursos Avançados

### Chaves e Referências
```mermaid
erDiagram
    TABELA1 {
        int ID PK "Chave Primária"
        string nome UK "Chave Única"
        int ref FK "Chave Estrangeira"
    }
```

### Comentários e Documentação
```mermaid
erDiagram
    ENTIDADE {
        string id PK "Identificador único"
        string email UK "Deve ser único"
        date criado "Data de criação"
    }
```

## Boas Práticas

1. **Nomenclatura**
   - Use nomes significativos
   - Mantenha padrão consistente
   - Documente campos importantes

2. **Modelagem**
   - Normalize adequadamente
   - Evite redundância
   - Defina chaves apropriadas

3. **Relacionamentos**
   - Especifique cardinalidade
   - Documente regras de negócio
   - Considere integridade referencial

4. **Documentação**
   - Adicione comentários relevantes
   - Explique regras complexas
   - Mantenha dicionário de dados

5. **Organização**
   - Agrupe entidades relacionadas
   - Mantenha diagrama legível
   - Use cores para categorização 