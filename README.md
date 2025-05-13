Claro! Abaixo você encontrará um **guia completo da sintaxe do LESS**, com **exemplos claros e práticos** para entender como funciona cada recurso.

---

## 📘 O que é LESS?

LESS (Leaner CSS) é um pré-processador CSS que adiciona **variáveis, aninhamento, mixins, operações e funções** ao CSS padrão, tornando-o mais poderoso e reutilizável.

---

## 📌 1. **Variáveis**

As variáveis em LESS são definidas com `@`.

```less
@cor-primaria: #3498db;
@padding: 10px;

button {
  background-color: @cor-primaria;
  padding: @padding;
}
```

---

## 📌 2. **Aninhamento de Seletores (Nesting)**

LESS permite que seletores sejam aninhados para representar a hierarquia HTML.

```less
nav {
  ul {
    li {
      a {
        color: black;
        text-decoration: none;

        &:hover {
          color: @cor-primaria;
        }
      }
    }
  }
}
```

`&` representa o seletor pai — no exemplo acima, `&:hover` vira `a:hover`.

---

## 📌 3. **Mixins (Reutilização de código)**

Mixins são blocos de estilo reutilizáveis.

```less
.borda-arredondada(@raio) {
  border-radius: @raio;
  -webkit-border-radius: @raio;
}

.caixa {
  width: 200px;
  height: 100px;
  .borda-arredondada(10px);
}
```

---

## 📌 4. **Mixins com parâmetros padrão**

Você pode definir valores padrão:

```less
.sombra(@x: 2px, @y: 2px, @cor: #aaa) {
  box-shadow: @x @y @cor;
}

.card {
  .sombra(); // usa valores padrão
}

.card-destacado {
  .sombra(4px, 4px, #000); // substitui os valores
}
```

---

## 📌 5. **Herança de Estilos com Mixins sem Parâmetro**

Você pode reutilizar estilos diretamente:

```less
.botoes-base {
  padding: 10px 20px;
  font-size: 16px;
}

.btn-primary {
  .botoes-base;
  background-color: @cor-primaria;
}
```

---

## 📌 6. **Operações matemáticas**

LESS permite somar, subtrair, multiplicar e dividir diretamente:

```less
@largura: 1000px;

.container {
  width: @largura / 2; // 500px
}
```

---

## 📌 7. **Funções de cor**

LESS tem várias funções integradas como `lighten`, `darken`, `fade`, etc.

```less
@cor-base: #e74c3c;

.alerta {
  background-color: lighten(@cor-base, 20%);
  border: 1px solid darken(@cor-base, 10%);
}
```

---

## 📌 8. **Escopo de variáveis**

LESS permite variáveis com escopo local (dentro de seletores ou mixins):

```less
@cor: red;

.div1 {
  @cor: blue;
  color: @cor; // azul
}

.div2 {
  color: @cor; // vermelho (variável global)
}
```

---

## 📌 9. **Importação de Arquivos**

Você pode dividir seu CSS em vários arquivos.

**\_cores.less**:

```less
@cor-primaria: #1abc9c;
```

**main.less**:

```less
@import "cores.less";

body {
  background-color: @cor-primaria;
}
```

---

## 📌 10. **Escapando CSS (interpolação)**

Permite criar seletores ou propriedades dinamicamente:

```less
@prefix: btn;

.@{prefix}-salvar {
  background-color: green;
}

.@{prefix}-cancelar {
  background-color: red;
}
```

Resultado:

```css
.btn-salvar { background-color: green; }
.btn-cancelar { background-color: red; }
```

---

## ✅ Exemplo Completo

```less
@cor-fundo: #f0f0f0;
@cor-texto: #333;
@espacamento: 16px;

.container {
  background-color: @cor-fundo;
  padding: @espacamento;

  h1 {
    color: @cor-texto;
  }

  .botao {
    .borda-arredondada(8px);
    padding: 10px 15px;
    background-color: lighten(@cor-texto, 40%);
    color: white;

    &:hover {
      background-color: darken(@cor-texto, 10%);
    }
  }
}

.borda-arredondada(@raio) {
  border-radius: @raio;
}
```

---

Se quiser, posso gerar o CSS resultante desse código para você ver a transformação final. Quer isso?
