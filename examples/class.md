# Diagramas de Classe com Mermaid

Os diagramas de classe são fundamentais para modelagem orientada a objetos, mostrando a estrutura de classes, seus atributos, métodos e relacionamentos.

## Exemplo Básico: Sistema de Biblioteca

```mermaid
classDiagram
    class Livro {
        -String titulo
        -String autor
        -String isbn
        +emprestar()
        +devolver()
        +getStatus()
    }
    
    class Usuario {
        -String nome
        -String email
        -List~Livro~ livrosEmprestados
        +emprestarLivro(Livro)
        +devolverLivro(Livro)
    }
    
    class Biblioteca {
        -List~Livro~ acervo
        -List~Usuario~ usuarios
        +cadastrarLivro(Livro)
        +cadastrarUsuario(Usuario)
        +buscarLivro(String)
    }
    
    Biblioteca "1" *-- "n" Livro
    Biblioteca "1" *-- "n" Usuario
    Usuario "1" -- "n" Livro
```

## Exemplo Avançado: E-commerce

```mermaid
classDiagram
    class Produto {
        <<abstract>>
        -Long id
        -String nome
        -BigDecimal preco
        +calcularPrecoFinal()*
        +getDescricao()
    }
    
    class ProdutoFisico {
        -Double peso
        -Dimensoes dimensoes
        +calcularFrete()
        +calcularPrecoFinal()
    }
    
    class ProdutoDigital {
        -String formato
        -Long tamanhoBytes
        +gerarLinkDownload()
        +calcularPrecoFinal()
    }
    
    class Pedido {
        -Long numero
        -Date data
        -StatusPedido status
        -List~ItemPedido~ itens
        +adicionarItem()
        +removerItem()
        +calcularTotal()
    }
    
    class ItemPedido {
        -Produto produto
        -Integer quantidade
        -BigDecimal precoUnitario
        +calcularSubtotal()
    }
    
    class Cliente {
        -String nome
        -String email
        -Endereco endereco
        -List~Pedido~ pedidos
        +fazerPedido()
        +cancelarPedido()
    }
    
    Produto <|-- ProdutoFisico
    Produto <|-- ProdutoDigital
    Pedido "1" *-- "n" ItemPedido
    ItemPedido "n" --> "1" Produto
    Cliente "1" -- "n" Pedido
```

## Sintaxe Básica

### Definição de Classe
```mermaid
classDiagram
    class Animal {
        -String nome
        -Int idade
        +fazerSom()
        +mover()
    }
```

### Visibilidade
```mermaid
classDiagram
    class Exemplo {
        +publicoAtributo
        -privadoAtributo
        #protegidoAtributo
        ~packageAtributo
        +publicoMetodo()
        -privadoMetodo()
        #protegidoMetodo()
        ~packageMetodo()
    }
```

### Tipos de Relacionamentos
```mermaid
classDiagram
    ClasseA --|> ClasseB : Herança
    ClasseC --* ClasseD : Composição
    ClasseE --o ClasseF : Agregação
    ClasseG --> ClasseH : Associação
    ClasseI ..> ClasseJ : Dependência
    ClasseK ..|> ClasseL : Implementação
```

## Recursos Avançados

### Interfaces e Classes Abstratas
```mermaid
classDiagram
    class Animal {
        <<abstract>>
        +fazerSom()*
        +mover()*
    }
    
    class IVoador {
        <<interface>>
        +voar()*
    }
    
    class Passaro {
        -String especie
        +fazerSom()
        +mover()
        +voar()
    }
    
    Animal <|-- Passaro
    IVoador <|.. Passaro
```

### Multiplicidade
```mermaid
classDiagram
    Professor "1" --> "n" Aluno : ensina
    Turma "1" --> "30" Aluno : contém
    Universidade "1" --> "n" Departamento : possui
```

## Boas Práticas

1. **Organização**
   - Agrupe classes relacionadas
   - Mantenha relacionamentos claros
   - Use espaçamento adequado

2. **Nomenclatura**
   - Use nomes significativos
   - Siga convenções de nomenclatura
   - Seja consistente no estilo

3. **Detalhamento**
   - Inclua apenas atributos relevantes
   - Documente métodos importantes
   - Especifique tipos de dados

4. **Relacionamentos**
   - Use o tipo correto de relacionamento
   - Indique multiplicidade
   - Evite relacionamentos desnecessários

5. **Legibilidade**
   - Evite diagramas muito grandes
   - Use comentários quando necessário
   - Mantenha a simplicidade 