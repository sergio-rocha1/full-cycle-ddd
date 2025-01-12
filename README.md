# Full Cycle DDD

## 🏗 Estrutura do Projeto

O projeto está organizado seguindo os princípios de Domain-Driven Design (DDD) com a seguinte estrutura:

```
src/
├── domain/
│   ├── @shared/
│   ├── customer/
│   ├── orders/
│   └── product/
└── infra/
    ├── customer/
    ├── order/
    └── product/
```

## 💾 Repositories

### Desafio de Repository

O projeto implementa o padrão Repository para diferentes entidades (Customer, Order, Product) seguindo uma interface comum:

```typescript
export default interface RepositoryInterface<T> {
    create(entity: T): Promise<void>;
    update(entity: T): Promise<void>;
    find(id: string): Promise<T>;
    findAll(): Promise<T[]>;
}
```

#### Implementações:

1. **CustomerRepository**
   - Gerencia persistência de clientes
   - Implementa operações CRUD completas
   - Utiliza Sequelize como ORM

2. **OrderRepository**
   - Gerencia pedidos e seus itens
   - Suporta relacionamentos complexos
   - Implementa operações de agregados

3. **ProductRepository**
   - Gerencia catálogo de produtos
   - Implementa operações básicas de CRUD
   - Mantém consistência dos dados

## 🎯 Events

### Desafio de Events

O projeto implementa um sistema de eventos seguindo o padrão Observer com as seguintes características:

#### Event Dispatcher

O EventDispatcher atua como centralizador de eventos, permitindo:
- ✨ Registro de handlers
- 🗑️ Remoção de handlers
- 📢 Notificação de eventos
- 🔄 Gerenciamento do ciclo de vida dos eventos

#### Eventos Implementados:

1. **CustomerCreatedEvent**
   - Disparado quando um novo cliente é criado
   - Possui dois handlers:
     ```typescript
     - EnviaConsoleLog1Handler
     - EnviaConsoleLog2Handler
     ```

2. **CustomerChangeAddressEvent**
   - Disparado quando o endereço do cliente é alterado
   - Handler: `EnviaConsoleLogHandler`
   - Registra mudanças de endereço com detalhes

## 🛠 Tecnologias Utilizadas

- **TypeScript** - Linguagem principal
- **Jest** - Framework de testes
- **Sequelize** - ORM
- **SQLite** - Banco de dados para testes
- **SWC** - Compilador

## 🧪 Testes

O projeto possui cobertura de testes abrangente, incluindo:
- ✅ Testes unitários para entidades
- ✅ Testes de integração para repositories
- ✅ Testes específicos para eventos

Para executar os testes:

```bash
npm run test
```

## 📦 Configuração do Projeto

1. Instale as dependências:
```bash
npm install
```

2. Configure o banco de dados (para desenvolvimento):
   - O projeto usa SQLite em memória para testes
   - Configure outras bases conforme necessário

3. Execute os testes:
```bash
npm run test
```

## 🎯 Objetivos do Projeto

### 1. Repository Pattern
   - 📊 Implementar abstração de persistência
   - 🔒 Garantir consistência nas operações de dados
   - 🔧 Facilitar testes e manutenção

### 2. Event Pattern
   - 🔄 Implementar comunicação desacoplada
   - 🔌 Permitir extensibilidade via eventos
   - ⚡ Manter consistência do domínio

## 🤝 Contribuição

Sinta-se à vontade para contribuir com o projeto através de:
- 🐛 Issues
- 🚀 Pull Requests
- 💡 Sugestões de melhorias

## 📝 Licença

Este projeto faz parte do curso Full Cycle e está disponível para fins educacionais.