# 🧭 Design Pattern - Visitor

## 📌 O que é o Visitor?

O **Visitor** é um padrão de projeto **comportamental** que permite **adicionar novas funcionalidades** a uma estrutura de objetos **sem modificar** as classes desses objetos.

> Ele separa o algoritmo da estrutura de dados, permitindo aplicar operações externas sobre objetos.

---

## 🎯 Exemplo simples

Imagine um sistema de pedidos:
- Temos **vários tipos de pedido** (ex: comum, com desconto).
- Cada tipo precisa de uma **regra diferente de cálculo**.
- Com o Visitor, criamos um "visitante" que **realiza esses cálculos**, fora da classe do pedido.

---

## 🧠 Como funciona?

### 🧩 Componentes principais:

| Componente     | Função                                                                 |
|----------------|------------------------------------------------------------------------|
| `Elemento`     | O objeto que será visitado.                                             |
| `Visitor`      | A classe que implementa as ações sobre o objeto.                       |
| `accept()`     | Método usado pelo objeto para aceitar e chamar o visitante.            |

---

### 🛠️ Exemplo de código

```js
// pedido.js

class PedidoComum {
  constructor(valor) {
    this.valor = valor;
  }

  accept(visitor) {
    return visitor.visitPedidoComum(this);
  }
}

class PedidoDesconto {
  constructor(valor) {
    this.valor = valor;
  }

  accept(visitor) {
    return visitor.visitPedidoDesconto(this);
  }
}

// O Visitor
class PedidoVisitor {
  visitPedidoComum(pedido) {
    return pedido.valor;
  }

  visitPedidoDesconto(pedido) {
    return pedido.valor * 0.9; // 10% de desconto
  }
}

🐾 Resumo simples
O Visitor é como um "visitante especialista" que olha cada tipo de objeto (como um pedido comum ou com desconto) e sabe exatamente o que fazer com ele, sem que o objeto precise saber como a lógica funciona.
