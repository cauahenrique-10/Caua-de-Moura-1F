# Respostas escritas: Introdução ao JavaScript

**Aluno:** Cauã Henrique de Moura
**Turma:** 1F, Técnico Integrado em Informática para Internet
**Disciplina:** Desenvolvimento Web I, Prof. Hewerton Enes de Oliveira

Os códigos de cada etapa estão nas pastas `etapa-0` a `etapa-8`. Todas as saídas abaixo foram conferidas executando o código.

---

## Etapa 0: Preparando o ambiente

**1. Em qual aba das ferramentas do desenvolvedor a mensagem apareceu?**
Na aba **Console**. A mensagem `Olá, JavaScript!` aparece ali e não na página.

**2. Por que o `defer` será importante quando o script precisar mexer em elementos da página?**
Porque o `defer` faz o navegador ler o HTML inteiro antes de executar o script. Se o script rodasse antes, os elementos (como o parágrafo `mensagem`) ainda não existiriam e o JavaScript não conseguiria encontrá-los.

**3. O que aconteceria se o HTML pedisse `codigo.js` e o arquivo se chamasse `script.js`?**
O navegador não encontraria o arquivo (erro 404, "Failed to load resource" no console). O script não seria executado e nada apareceria no console.

---

## Etapa 1: O que é JavaScript

Tabela preenchida:

| Expressão | Resultado observado |
|---|---|
| `2 + 3` | `5` |
| `"Web" + " I"` | `"Web I"` |
| `"5" + 3` | `"53"` |
| `"5" - 3` | `2` |
| `2 + 3 * 4` | `14` |
| `(2 + 3) * 4` | `20` |

**1. Por que `"5" + 3` e `"5" - 3` dão resultados tão diferentes?**
Quando um dos lados do `+` é texto, o operador concatena: o `3` vira texto e o resultado é o texto `"53"`. Já o `-` só faz subtração de números, então o JavaScript converte `"5"` para o número 5 e calcula `5 - 3 = 2`.

**2. Por que `2 + 3 * 4` e `(2 + 3) * 4` dão resultados diferentes?**
Porque a multiplicação é feita antes da soma, como na matemática. Em `2 + 3 * 4` faz-se `3 * 4 = 12` e depois `2 + 12 = 14`. Com parênteses, a soma vem primeiro: `5 * 4 = 20`.

---

## Etapa 2: Variáveis e tipos

**1. O que as quatro linhas com `typeof` imprimem?**

```
string
number
boolean
undefined
```

**2. Qual erro apareceu na última linha? Por quê?**
`TypeError: Assignment to constant variable.` A variável `escola` foi criada com `const`, que não permite trocar o valor depois de definido. Se ela precisasse mudar, deveria ser declarada com `let`.

**3. Quais nomes de variável são válidos?**

- [x] `nota_final`: válido
- [ ] `3nota`: inválido, pois não pode começar com número
- [ ] `nota-final`: inválido, pois o hífen seria lido como subtração
- [x] `$total`: válido
- [ ] `class`: inválido, pois é palavra reservada da linguagem

**4. O que será impresso?**

```js
let idade = 15;
idade = idade + 1;
console.log(idade);
```

Imprime **16**. Primeiro calcula-se `15 + 1` e o resultado é guardado de volta em `idade`.

**Experimentos por conta própria:**
- Com `console.log(nota1);` antes da linha do erro, aparece **9**, porque `let` permite trocar o valor.
- Mudando para `let nota1 = "8.5";` (com aspas), o `typeof` imprime **string**, pois o valor passa a ser texto.

---

## Etapa 3: Operadores, conversão e texto com variáveis

**1. Saída prevista de cada `console.log` (8 linhas):**

```
9 5 14
3.5
1
49
Olá, Ana! 7 dividido por 2 é 3.5.
8.5
7.51
NaN
```

**2. Diferença entre `Number("7.5") + 1` e `"7.5" + 1`.**
`Number("7.5") + 1` converte o texto em número e soma: **8.5**. `"7.5" + 1` soma um texto com um número, então concatena e produz o texto **"7.51"**. Para quem lê um número de um campo de formulário, isso significa que o valor chega como texto e precisa ser convertido com `Number()` antes de fazer contas. Sem isso, as notas seriam concatenadas em vez de somadas.

**3. Cálculos sem executar:**

| Expressão | Resultado |
|---|---|
| `10 % 3` | `1` (10 dividido por 3 dá 3 e sobra 1) |
| `2 ** 3` | `8` |
| `10 / 4` | `2.5` |

---

## Etapa 4: Condicionais

**1. Com `temperatura = 20` e com `30`, qual mensagem aparece?**
- Com **20**: `Agradável`. A primeira condição (`>= 30`) é falsa, e a segunda (`>= 20`) é verdadeira, pois 20 é maior *ou igual* a 20.
- Com **30**: `Calor`. A primeira condição (`>= 30`) já é verdadeira, e o resto é ignorado.
- Com **19** aparece `Frio`, porque nenhuma das duas condições é verdadeira.

**2. Saídas das quatro últimas linhas e por que usar `===`:**

```
true     // 5 == "5"
false    // 5 === "5"
true     // 0 == false
false    // 0 === false
```

O `==` converte os tipos antes de comparar, o que gera resultados surpreendentes (um número igual a um texto, `0` igual a `false`). O `===` exige mesmo valor **e** mesmo tipo, então o resultado é previsível. Por isso a regra é usar sempre `===` e `!==`.

**3. Condição verdadeira apenas quando `nota` está entre 0 e 10 (inclusive):**

```js
nota >= 0 && nota <= 10
```

---

## Etapa 5: Repetição e listas

**1. Média das quatro notas (`8`, `6.5`, `9`, `4`):**
A soma é 27.5 e, dividindo por 4, a média é **6.875**.

**2. Índices na lista `notas`:**
O primeiro elemento tem índice **0**. O último tem índice **`notas.length - 1`** (na lista original, 3).

**3. Laço que imprime os pares de 2 a 10:**

```js
for (let i = 2; i <= 10; i += 2) {
  console.log(i);
}
```

Imprime 2, 4, 6, 8 e 10.

**4. Teste de mesa:**

```js
let total = 0;
for (let i = 1; i <= 4; i++) {
  total += i;
}
console.log(total);
```

| Volta | i | total depois da volta |
|---|---|---|
| 1 | 1 | 1 |
| 2 | 2 | 3 |
| 3 | 3 | 6 |
| 4 | 4 | 10 |

Será impresso **10**.

---

## Etapa 6: Funções

**1. O que a função abaixo imprime? Qual é o erro?**

```js
function soma(a, b) {
  a + b;
}
console.log(soma(2, 3));
```

Imprime **`undefined`**. A função calcula `a + b`, mas não devolve o resultado, pois falta o `return`. Correção:

```js
function soma(a, b) {
  return a + b;
}
```

Assim `soma(2, 3)` devolve **5**.

**2. Função `ehPar(n)`:**

```js
function ehPar(n) {
  return n % 2 === 0;
}
```

`ehPar(4)` devolve `true` e `ehPar(7)` devolve `false`.

**3. Diferença entre `console.log(x)` e `return x` dentro de uma função.**
O `console.log(x)` apenas **mostra** o valor no console, para quem está programando ver. A função continua devolvendo `undefined` a quem a chamou. O `return x` **devolve** o valor a quem chamou a função e encerra a função, e esse valor pode ser guardado em uma variável ou usado em outra conta.

**Chamadas feitas à mão no console:** `dobro(5)` devolve `10` e `media([10, 6])` devolve `8`.

---

## Etapa 7: Mexendo na página (DOM e eventos)

**1. Removendo o `defer`, qual erro aparece e por quê?**
Aparece `TypeError: Cannot set properties of null (setting 'textContent')`. Sem o `defer`, o script roda no `<head>`, antes de o navegador ler o `<body>`. Nesse momento o parágrafo ainda não existe, então `document.getElementById("mensagem")` devolve `null` (nada encontrado) e a linha `mensagem.textContent = ...` tenta mexer em `null`.

**2. O que acontece, passo a passo, a cada clique no botão?**
1. O navegador percebe o evento `click` no botão e executa a função que foi registrada com `addEventListener`.
2. A linha `cliques++` soma 1 na variável `cliques`.
3. A linha `contador.textContent = cliques` mostra o novo valor dentro do `<span>`, e o número na página sobe.
4. A linha `botao.textContent = "Clicado!"` troca o texto do botão.

**3. Por que `cliques` foi declarada com `let` e não com `const`?**
Porque o valor muda a cada clique. Com `const`, o `cliques++` geraria `TypeError: Assignment to constant variable`.

**Alterações feitas por conta própria (no `etapa-7/script.js`):**
- `mensagem.style.color = "green";` pinta a mensagem de verde.
- `botao.textContent = "Clicado!";` dentro da função do clique troca o texto do botão.

---

## Etapa 8: Mini-projeto, calculadora de média

A Etapa 8 foi feita em partes, uma pasta para cada seção da apostila, dentro de `etapa-8`. Cada pasta tem o código no ponto em que a seção termina.

### 8.1: Montar a página (HTML)
Pasta `etapa-8/8-1-pagina`. O `index.html` tem dois campos numéricos (`nota1` e `nota2`), o botão `calcular` e o parágrafo `resultado`, ainda vazio. O botão ainda não faz nada. Os `id` são a "ponte" que o JavaScript usa para encontrar os elementos.

### 8.2: Esqueleto e leitura dos campos
Pasta `etapa-8/8-2-esqueleto`. O `script.js` tem a constante `NOTA_MINIMA`, as duas funções vazias e o evento de clique, com os quatro `TODO`. Digitando 8 e 7 e clicando em Calcular, o console mostra:

```
Digitado: 8 7 string
```

O valor lido de um campo (`.value`) é **texto**, por isso o código converte para número com `Number()`.

### 8.3: TODO 1, calcular a média
Pasta `etapa-8/8-3-media`.

```js
function calcularMedia(n1, n2) {
  return (n1 + n2) / 2;
}
```

Testes no console: `calcularMedia(8, 7)` devolve `7.5`, `calcularMedia(10, 5)` devolve `7.5` e `calcularMedia(6, 6)` devolve `6`.

**Por que não se pode escrever `n1 + n2 / 2`?**
Porque a divisão é feita antes da soma. Para 8 e 6, `n1 + n2 / 2` dá `8 + 3 = 11`, enquanto a média correta é `(8 + 6) / 2 = 7`. Os parênteses são necessários.

### 8.4: TODO 2, verificar se a nota é válida
Pasta `etapa-8/8-4-validacao`.

```js
function notaValida(n) {
  return !Number.isNaN(n) && n >= 0 && n <= 10;
}
```

Em português: "não é NaN, e é maior ou igual a 0, e é menor ou igual a 10". Testes no console: `notaValida(5)` e `notaValida(10)` devolvem `true`. `notaValida(11)`, `notaValida(-1)` e `notaValida(NaN)` devolvem `false`.

### 8.5: TODO 3 e 4, validar, calcular e mostrar
Pasta `etapa-8/8-5-completo`, que é a versão final do projeto.

```js
if (texto1 === "" || texto2 === "" || !notaValida(n1) || !notaValida(n2)) {
  resultado.textContent = "Informe duas notas entre 0 e 10.";
  return;
}

const media = calcularMedia(n1, n2);
let situacao;

if (media >= NOTA_MINIMA) {
  situacao = "Aprovado";
} else {
  situacao = "Abaixo da média";
}

resultado.textContent = `Média: ${media.toFixed(1)} - ${situacao}`;
```

O campo vazio é testado antes de confiar na conversão, porque `Number("")` vale `0` e viraria uma nota zero "válida". O `return` dentro do `if` encerra a função, então o código abaixo só roda se tudo estiver correto. Os atributos `min` e `max` do HTML não impedem de digitar 11, por isso a validação em JavaScript continua necessária. Na versão final removi o `console.log` de apoio.

### 8.6: Teste da solução

| Nota 1 | Nota 2 | Resultado esperado | Resultado obtido | Deu certo? |
|---|---|---|---|---|
| 8 | 7 | Média: 7.5 - Aprovado | Média: 7.5 - Aprovado | Sim |
| 5 | 6 | Média: 5.5 - Abaixo da média | Média: 5.5 - Abaixo da média | Sim |
| 6 | 6 | Média: 6.0 - Aprovado (limite) | Média: 6.0 - Aprovado | Sim |
| 10 | 10 | Média: 10.0 - Aprovado | Média: 10.0 - Aprovado | Sim |
| (vazio) | 5 | Mensagem de erro | Informe duas notas entre 0 e 10. | Sim |
| 11 | 5 | Mensagem de erro | Informe duas notas entre 0 e 10. | Sim |

### Checkpoint

**1. Por que a média foi calculada em uma função separada (`calcularMedia`)?**
Porque assim o cálculo fica escrito uma única vez e pode ser reutilizado. A função também pode ser testada sozinha no console, e o código do clique fica mais curto e mais fácil de ler.

**2. Se a média mínima mudasse de 6 para 7, quantas linhas seriam alteradas?**
**Uma só**: a linha `const NOTA_MINIMA = 6;`. O restante do código usa `NOTA_MINIMA`, então não é preciso procurar o número 6 pelo código.

---

## Autoavaliação

- [x] Explicar o que o JavaScript faz em uma página, em comparação com HTML e CSS.
- [x] Abrir o console e ler uma mensagem de erro.
- [x] Escolher entre `let` e `const` e identificar o tipo de um valor.
- [x] Converter texto em número e explicar por que isso é necessário com formulários.
- [x] Escrever `if`/`else` e usar `===`.
- [x] Percorrer uma lista com `for`.
- [x] Criar uma função com parâmetros e `return`.
- [x] Selecionar um elemento, mudar seu texto e reagir a um clique.
