# Arquitetura - Alimenta Aí!

## Diagrama de Contexto

```mermaid
graph TD
    Doador["Doador"]
    Receptor["Receptor"]
    Admin["Admin"]
    Sistema["Alimenta Aí!"]
    
    Doador --> Sistema
    Receptor --> Sistema
    Admin --> Sistema
```

## Diagrama de Containers

```mermaid
graph TD
    Frontend["React"]
    Backend["Spring Boot"]
    Database["PostgreSQL"]
    Usuario["Usuário"]
    
    Usuario --> Frontend
    Frontend --> Backend
    Backend --> Database
```

## Diagrama de Componentes

```mermaid
graph TD
    Controller["Controller"]
    Service["Service"]
    Repository["Repository"]
    Frontend["React"]
    Database["PostgreSQL"]
    
    Frontend --> Controller
    Controller --> Service
    Service --> Repository
    Repository --> Database
```

## Tecnologias

- Java 21 + Spring Boot
- React 18
- PostgreSQL 15

## Justificativas

1. Java + Spring Boot: segurança e tipagem forte
2. PostgreSQL: evita que dois peguem a mesma doação
3. React: interface rápida
