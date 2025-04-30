# Link da apressentação:
https://www.canva.com/design/DAGmCW0kPyE/he6v_Tn719lJixnpzkSliA/edit?utm_content=DAGmCW0kPyE&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton

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
```
## ✅ Vantagens

- ✅ **Separa regras de negócio da estrutura de dados**  
  Permite que as regras fiquem fora das classes principais, deixando o código mais limpo e modular.

- ✅ **Fácil adicionar novas operações (visitantes)**  
  Basta criar uma nova classe Visitor sem precisar alterar as classes dos objetos existentes.

- ✅ **Organiza melhor o código quando há muitas operações**  
  Evita poluir as classes de dados com múltiplos métodos relacionados a diferentes comportamentos.

---

## ❌ Desvantagens

- ⚠️ **Aumenta a complexidade**  
  Exige mais classes e interfaces, o que pode deixar o projeto mais difícil de entender para iniciantes.

- ⚠️ **Dificuldade se a estrutura dos objetos mudar**  
  Se você alterar as classes dos elementos visitados, será necessário atualizar todos os visitantes.

- ⚠️ **Pode violar o encapsulamento**  
  O Visitor pode precisar acessar detalhes internos do objeto, quebrando a ideia de esconder implementação.
