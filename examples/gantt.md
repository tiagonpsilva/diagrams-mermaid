# Diagramas Gantt com Mermaid

Os diagramas Gantt são ideais para planejamento de projetos, mostrando tarefas, durações e dependências ao longo do tempo.

## Exemplo Básico: Sprint de Desenvolvimento

```mermaid
gantt
    title Sprint de Desenvolvimento
    dateFormat  YYYY-MM-DD
    
    section Planejamento
    Refinamento de Backlog    :2024-01-01, 2d
    Planning                  :2024-01-03, 1d
    
    section Desenvolvimento
    Feature A                 :2024-01-04, 3d
    Feature B                 :2024-01-08, 4d
    Correção de Bugs         :2024-01-12, 2d
    
    section Qualidade
    Testes                    :2024-01-15, 3d
    Code Review               :2024-01-16, 2d
    
    section Entrega
    Deploy Staging            :2024-01-18, 1d
    Validação                 :2024-01-19, 1d
    Deploy Produção          :2024-01-22, 1d
```

## Exemplo Avançado: Projeto de Software

```mermaid
gantt
    title Projeto E-commerce
    dateFormat  YYYY-MM-DD
    excludes    weekends
    
    section Análise
    Levantamento de Requisitos    :a1, 2024-01-01, 10d
    Análise de Negócio           :after a1, 5d
    Prototipação                 :after a1, 8d
    
    section Arquitetura
    Design de Sistema            :2024-01-15, 8d
    Setup de Infraestrutura      :2024-01-20, 5d
    
    section Backend
    API de Usuários              :2024-02-01, 10d
    API de Produtos              :2024-02-01, 12d
    API de Pedidos               :2024-02-15, 15d
    Integração Pagamento         :2024-03-01, 10d
    
    section Frontend
    Layout Base                  :2024-02-01, 8d
    Páginas de Usuário          :2024-02-10, 12d
    Catálogo de Produtos        :2024-02-15, 10d
    Checkout                     :2024-03-01, 15d
    
    section Testes
    Testes Unitários            :2024-03-15, 10d
    Testes de Integração        :2024-03-20, 8d
    Testes E2E                  :2024-03-25, 12d
    
    section Deploy
    Deploy Staging              :2024-04-10, 3d
    Testes de Aceitação        :2024-04-15, 5d
    Deploy Produção            :crit, 2024-04-20, 2d
```

## Exemplo com Dependências: Construção de Casa

```mermaid
gantt
    title Construção de Casa
    dateFormat  YYYY-MM-DD
    
    section Fundação
    Preparação do Terreno    :a1, 2024-01-01, 5d
    Fundação                :after a1, 15d
    
    section Estrutura
    Paredes                 :after a1, 20d
    Telhado                 :after a1, 10d
    
    section Instalações
    Elétrica               :b1, after a1, 10d
    Hidráulica             :b2, after b1, 10d
    
    section Acabamento
    Reboco                 :c1, after b2, 10d
    Pintura               :c2, after c1, 8d
    Piso                  :c3, after c1, 7d
    
    section Finalização
    Limpeza               :after c2, 3d
    Vistoria              :after c3, 2d
```

## Sintaxe Básica

### Definição de Tarefas
```mermaid
gantt
    title Exemplo de Sintaxe
    dateFormat YYYY-MM-DD
    
    Tarefa Simples           :2024-01-01, 5d
    Tarefa com ID            :t1, 2024-01-06, 3d
    Tarefa Crítica          :crit, 2024-01-09, 4d
    Tarefa Ativa            :active, 2024-01-13, 3d
    Milestone               :milestone, 2024-01-16, 0d
```

### Seções e Dependências
```mermaid
gantt
    Seção A                  :a1, 2024-01-01, 5d
    Depende de A            :after a1, 3d
    Em Paralelo com A       :2024-01-01, 4d
    Milestone               :milestone, after a1, 0d
```

## Recursos Avançados

### Status e Estilos
```mermaid
gantt
    title Estilos e Status
    dateFormat YYYY-MM-DD
    
    section Desenvolvimento
    Completo    :done, 2024-01-01, 2d
    Em Progresso :active, 2024-01-03, 3d
    Crítico     :crit, 2024-01-06, 4d
    
    section Testes
    Pendente    :2024-01-10, 3d
```

### Exclusões e Formatação
```mermaid
gantt
    title Configurações Avançadas
    dateFormat YYYY-MM-DD
    axisFormat %d/%m
    excludes weekends 2024-01-01
    
    Tarefa A    :2024-01-02, 5d
    Tarefa B    :2024-01-08, 5d
```

## Boas Práticas

1. **Organização**
   - Agrupe tarefas relacionadas em seções
   - Mantenha uma hierarquia clara
   - Use cores para indicar status

2. **Temporização**
   - Seja realista com as durações
   - Considere dependências
   - Inclua folgas para imprevistos

3. **Clareza**
   - Use nomes descritivos
   - Indique milestones importantes
   - Destaque caminhos críticos

4. **Manutenção**
   - Atualize regularmente
   - Monitore progresso
   - Ajuste conforme necessário

5. **Visualização**
   - Mantenha escala apropriada
   - Use formatação consistente
   - Destaque datas importantes 