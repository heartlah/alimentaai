# Arquitetura — Alimenta Aí!

## Escolhas Tecnológicas

A solução foi desenvolvida como uma **aplicação web estática** utilizando apenas HTML, CSS e JavaScript puro, sem frameworks ou bibliotecas externas. Esta escolha foi motivada pela simplicidade de execução e pela ausência de necessidade de infraestrutura de servidor para o escopo do projeto.

A persistência de dados é realizada via **localStorage** do navegador, o que permite que os dados sejam mantidos entre sessões sem a necessidade de um banco de dados externo.

## Modelo Arquitetural

A arquitetura segue o padrão de **Single Page Application (SPA) simplificada**, com uma única página HTML que gerencia múltiplas "telas" por meio de manipulação de DOM.

```
┌─────────────────────────────────────────┐
│              Navegador Web              │
│                                         │
│  ┌────────────────────────────────────┐ │
│  │         index.html (SPA)           │ │
│  │                                    │ │
│  │  ┌──────────┐  ┌────────────────┐  │ │
│  │  │   HTML   │  │   JavaScript   │  │ │
│  │  │ (Views)  │  │  (Controller)  │  │ │
│  │  └──────────┘  └───────┬────────┘  │ │
│  │       ▲                │           │ │
│  │       │         ┌──────▼────────┐  │ │
│  │       └─────────│  localStorage │  │ │
│  │                 │   (Model)     │  │ │
│  │                 └───────────────┘  │ │
│  └────────────────────────────────────┘ │
└─────────────────────────────────────────┘
```

**Camadas:**
- **View (HTML/CSS):** renderização das telas de autenticação, feed, cadastro e gerenciamento
- **Controller (JavaScript):** lógica de negócio, validações e manipulação de eventos
- **Model (localStorage):** armazenamento persistente de usuários e doações

## Justificativa

Para o escopo do projeto (aplicação acadêmica individual com foco em funcionalidade), a arquitetura escolhida é adequada pois:

1. **Simplicidade:** não exige instalação de dependências, servidores ou banco de dados
2. **Portabilidade:** qualquer navegador moderno executa a aplicação sem configuração
3. **Foco no domínio:** permite concentrar esforços nas regras de negócio e experiência do usuário
4. **Rastreabilidade:** todo o código em um único arquivo facilita revisão e avaliação
