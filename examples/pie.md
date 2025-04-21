# Diagramas de Pizza com Mermaid

Os diagramas de pizza são úteis para visualizar distribuições e proporções de dados em formato circular.

## Exemplo Básico: Distribuição de Bugs por Severidade

```mermaid
pie title Bugs por Severidade
    "Crítico" : 15
    "Alto" : 25
    "Médio" : 35
    "Baixo" : 25
```

## Exemplo Avançado: Distribuição de Tecnologias em um Projeto

```mermaid
pie showData
    title Tecnologias Utilizadas no Projeto
    "Frontend (React)" : 30
    "Backend (Node.js)" : 25
    "Database (PostgreSQL)" : 20
    "DevOps (Docker/K8s)" : 15
    "Testes" : 10
```

## Exemplo com Valores Percentuais: Cobertura de Testes

```mermaid
pie title Cobertura de Testes
    "Unitários" : 45
    "Integração" : 30
    "E2E" : 15
    "Manual" : 10
```

## Sintaxe Básica

### Diagrama Simples
```mermaid
pie
    "Categoria A" : 30
    "Categoria B" : 70
```

### Com Título
```mermaid
pie title Meu Diagrama
    "Segmento 1" : 50
    "Segmento 2" : 50
```

### Com Dados Visíveis
```mermaid
pie showData
    "Item 1" : 35
    "Item 2" : 65
```

## Exemplos de Uso

### Distribuição de Recursos
```mermaid
pie title Alocação de Recursos
    "Desenvolvimento" : 40
    "Infraestrutura" : 20
    "Marketing" : 20
    "Suporte" : 15
    "Outros" : 5
```

### Status de Tarefas
```mermaid
pie title Status do Sprint
    "Completo" : 60
    "Em Progresso" : 25
    "Pendente" : 10
    "Bloqueado" : 5
```

### Métricas de Qualidade
```mermaid
pie title Métricas de Código
    "Código Limpo" : 75
    "Necessita Refatoração" : 15
    "Débito Técnico" : 10
```

## Boas Práticas

1. **Clareza**
   - Use títulos descritivos
   - Limite o número de segmentos
   - Ordene por relevância

2. **Dados**
   - Use valores precisos
   - Mostre dados quando relevante
   - Mantenha proporções realistas

3. **Visualização**
   - Use cores contrastantes
   - Mantenha legibilidade
   - Considere o contexto

4. **Uso Apropriado**
   - Para distribuições simples
   - Quando soma é 100%
   - Para comparações proporcionais

5. **Limitações**
   - Evite muitos segmentos
   - Não use para tendências
   - Não para comparações complexas 