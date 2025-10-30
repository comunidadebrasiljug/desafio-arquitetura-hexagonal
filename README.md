# 🧩 Projeto Desafio — Arquitetura Hexagonal em Java (Ports & Adapters)

## 🎯 Objetivo
Implementar um sistema seguindo os princípios da **Arquitetura Hexagonal**, também conhecida como **Ports and Adapters**, utilizando **Java** e **Spring Boot**.  
O foco é criar uma aplicação modular, independente de frameworks e tecnologias externas, onde as **regras de negócio** (domínio) são o centro da aplicação.

---

## 📘 Conceito
A **Arquitetura Hexagonal** tem como principal objetivo **isolar o domínio** da aplicação das camadas externas (como banco de dados, APIs ou interface web).

A ideia é dividir o sistema em **três grandes partes**:
1. **Domínio (Core / Application)** → Regras de negócio e lógica da aplicação.
2. **Ports (Interfaces)** → Contratos que definem a comunicação com o domínio.
3. **Adapters (Implementações)** → Integram tecnologias externas (banco, API, fila, etc.).

---

## 🏗️ Tema do Desafio: Sistema de Pedidos de Restaurante

Você vai desenvolver uma API simples para gerenciar **pedidos**, **clientes** e **produtos**, seguindo o estilo **hexagonal**.

---

## 🧱 Componentes Principais

### 🏗️ Domínio
Camada central e independente:
- `Pedido`, `Produto`, `Cliente`
- Regras como: calcular total do pedido, validar estoque, etc.

---

### 🚪 Ports
Interfaces que definem **como o domínio se comunica com o mundo externo**:
- `CriarPedidoUseCase` (entrada)
- `BuscarPedidoUseCase` (entrada)
- `PedidoRepositoryPort` (saída)

---

### 🔌 Adapters
Implementações concretas:
- **Entrada (in/web):**
  - `PedidoController` expõe endpoints REST.
- **Saída (out/db):**
  - `PedidoRepositoryAdapter` implementa `PedidoRepositoryPort` com Spring Data ou MongoDB.

---

## 🚀 Exemplo de Fluxo

1️⃣ O usuário faz uma requisição `POST /pedidos`.  
2️⃣ O **Controller** (Adapter In) chama o **Caso de Uso** `CriarPedidoService`.  
3️⃣ O caso de uso chama o **Port de saída** `PedidoRepositoryPort`.  
4️⃣ O **Adapter Out** grava no banco.  
5️⃣ O domínio retorna o resultado sem depender de tecnologia.

---

## 💡 Benefícios da Arquitetura Hexagonal
✅ Independência de frameworks  
✅ Testes unitários mais simples  
✅ Fácil substituição de tecnologias (ex: trocar MySQL por Mongo)  
✅ Código mais modular e limpo  
✅ Regras de negócio totalmente desacopladas

---

## 🧠 Desafio Extra
1. Implementar cache Redis para pedidos recentes.  
2. Adicionar mensageria com Kafka ou RabbitMQ (adapter out).  
3. Criar testes unitários simulando os ports com Mockito.  
4. Implementar validações de domínio (ex: pedido sem itens não pode ser criado).
