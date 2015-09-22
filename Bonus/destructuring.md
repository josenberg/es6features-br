
Atribuir o valor ou a referencia de uma variavel para outra é sem duvidas uma das coisas mais feitas em qualquer linguagem de programação, o destructuring assingment é uma maneira mais facil de trabalhar com isso, essa feature já existe no pearl ou no python, alem de adicionar facilidades no desenvolvimento JS ela tambem facilita a entrada de desenvolvedores dessas linguagens no javascript. 

A sintax de destructuring assingment é uma expressão javascript que faz possivel extrair dados de um array ou objeto utilizando uma sintaxe que copia a construção desse array ou objeto literal.

Syntax

```
[a, b] = [1, 2]
[a, b, ...rest] = [1, 2, 3, 4, 5]
{a, b} = {a:1, b:2}
{a, b, ...rest} = {a:1, b:2, c:3, d:4}  //ES7
```

**Descrição**

As expressões para objetos literais e arrays nos permitem uma maneira de criar pacotes _ad hoc_ de dados. Uma vez que você tenha criado esses pacotes, você pode usar eles da maneira que você quiser, você pode inclusive faze-los ser retorno de funções.

Uma coisa particularmente bacana que você pode fazer com destructuring assignment é ler um statmente inteiro, porem existem outras diversas coisas para se fazer com eles, veja os exemplos abaixo.

Essa feature é similar à features presentes no Pearl e no Python.

**Array destructuring**

**Simple example**

```
var foo = ["one", "two", "three"];

// without destructuring
var one = foo[0];
var two = foo[1];
var three = foo[2];

// with destructuring
var [one, two, three] = foo;
```

**Assingment sem declaração**
Essa sintaxe tambem pode ser utilizada sem estar usar variaveis recem criadas.

```
var a, b;

[a, b] = [1, 2]
```

**Swapping variables**
Depois de executar esse script, `b = 1` e `a = 3`. Sem destructuring assingment, dar o swap em duas variaveis requer uma variavel temporaria.

```
var a = 1;
var b = 2;

[a, b] = [b, a];
```

**Retorno de multiplos valores**
Graças ao destructuring funções podem retornar multiplos valores, sempre foi possivel setar um array como retorno de uma função, porem agora nos temos mais algumas flexibilidades.


```
function f(){
	return [1,2]
}
```

Como você pode ver o result é feito usando uma notação parecida com a usada em arrays, com os valores dentro de colchetes `[]`. Você pode colocar qualquer numero de variaveis como esse tipo de return. Nesse exemplo `f()` retorna os valores [1, 2] como output.

```
var a, b;
[a, b] = f();
console.log("A é " + a + " B é " + b);
```

A parte do `[a, b] = f()` faz com que o valor que estiver dentro dos colchetes seja setado dentro das variaveis na ordem escrita, ou seja, `a = 1` e `b = 2`.

Você tambem pode receber esse valor como uma array

```
var a = f();
console.log("A é " + a);
```

Nesse caso, o valor de A é um array contendo os valores de a e b.

**Ignorando alguns dos valores retornados**

```
function f(){
	return [1, 2, 3];
}

var [a, , c] = f();
console.log("A é " + a + "B é " + b);
```

Depois de rodar esse codigo, `a = 1` e `b = 3`. O valor de 2 é ignorado. Você pode ignorar todos, ou nenhum dos valores retornados.

```
[,,,] = f();
```

**Recebendo valores baseados em uma expressão regular**
Quando o metodo de expressão regular `exec()` encontra um resultado, ele retorna um array retornar a porçção inteira da string na qual o resultado foi encontrado. destructuring assignment permite o mesmo tipo de comportamento, ignorando full match caso não seja necessaria.

```
var url = "http://josenberg.com.br";

var parsedURL = /^(\w+)\:\/\/([^\/]+)\/(.*)$/.exec(url);
var [, protocol, fullhost, fullpath] = parsedURL;
consoles.log(protocol) // logs "https:"
```

**Object destructuring**
Exemplo simples
```var o = {p: 42, q: true};
var {p, q} = o;

console.log(p); // 42
console.log(q); // true

// setando em variaveis novas;
var {p: foo, q: bar} = o;

console.log(foo); //42
console.log(bar); //true
```

**Function arguments default**
Versão ES5
```
function drawES5Chart(options){
	options = options === undefined ? {} : options;
	var size = options.size === undefined ? 'big' : options.size;
	var cords = options.cord === undefined ? {x: 0, y: 0} : options.cords;
	var radius = options.radius === undefined ? 25 : options.radius;
	console.log(size, conrds, radius);
	// Aqui seria o codigo que renderiza o chart de verdade
}
```
Versão ES6
```
function drawES6Chart({size = 'big', cords {x: 0, y: 0}. radius = 25} = {}){
    console.log(size, cords, radius);
    // do some chart drawing;
}

drawES6Chart({
	cords: {x: 18, y: 30},
	radius: 30
});
```
**Conclusão**

Só pelo fato de você poder manipular o valor default das variaveis que serão usadas em seus metodos isso já é uma features bem supinpa, existem outras aplicação para essa feature na ECMAScript 2015, eu provavelmente irei fazer mais um artigo sobre isso logo, mas se você tiver algum conhecimento em ingles você pode ver o [artigo](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) em que eu baseiei (traduzi) esse texto. 








