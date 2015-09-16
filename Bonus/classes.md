## Definição
Classes no JavaScript são mais semanticas que a as existentes heranças baseadas em prototype. Essa sintaxe **NÃO** é a introdução de uma nova forma de orientação à objetos no JavaScript. É uma apenas uma nova sintaxe mais simples de criar e lidar com objetos que manipulam herença.

Na verdade classes são `funções`, e assim como você pode definir funções como `function expressions` e como `function declarations` você tambem pode definir classes como `class expressions` e `class declarations`

###Class declarations

Uma das maneiras de definir classes é usando a forma `Class declarations`. Para declarar essa classe, você precisa usar a keywork class junto com o nome da classe. (Como no exemplo);

``class Polygon {
   constructor(height, width){
      this.height = height;
      this.width = width;
   }
}``

Hoisting

Uma diferença importante entre `function delarations` e `class declarations` é que funções declarativas possuem hoist, e classes declarativas não . Primeiro você iá declarar sua classe para acessa-la, senão ela irá dar throw em um ReferenceError:

``var p = new Polygon(); //ReferenceError``
``class Polygon {} ``

###Class expressions

`Class expressions` são apenas outro jeito de se declarar uma classe. Classes expressivas podem ou não possuir um nome. O nome é dado para essa classe quando é escrito antes do corpo dela.

``//Unnamed
var Polygon = class {
   constructor(height, width){
    this.height = height;
    this.width = width;
   }
};`` 

``//named
var Polygon = class Polygon {
   constructor(height, width){
    this.height = height;
    this.width = width;
   }
};`` 


###Class body and method definitions

O corpo da classe é a parte que esta entre chaves `{}`. isso é, onde você define os membros dessa classe, assim como methodos e construtores.

###Strict Mode
O corpo das classes é (tanto declarativa como o da expressiva) executado em strict mode.

###Metodo Construtor
O metodo construtor (`constructor`) é um metodo especial para a criação e inicialização de um objeto com a classe. Só pode existir um unico metodo ccom o nome de "construtor" em uma classe. Um SintaxError será lançado caso você aconteça de você ter mais de um metodo desse declarado dentro do sua classe.

O construtor pode usar a keyword `super` para acessar o construtor da classe pai.

###Metodos Prototype
"Em breve existirá um artigo explicando melhor essa parte".

``class Polygon {
  constructor(height, width){
    this.height = height;
    this.width = width;
  }
  getArea(){
    return this.calArea();
  }
  calcArea(){
    return this.height * this.width;
  }
}``

###Metodos estaticos

A keyword `static` define um metodo estatico para uma classe. Metodos estaticos podem ser chamados quando a classe ainda não foi instanciada. Eles são usados normalmente para definir funções de utilidade `utils` para uma aplicação. 

``class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }
  
  static distance(a, b){
    const dx = a.x - b.x;
    const dy = a.y - b.y;
    
    return Math.sqrt(dx*dx + dy*dy);
  }
}

const p1 = new Point(5, 5);
const p2 = new Point(10, 10);

console.log(Point.distance(p1, p2));``

###Criando uma subclass com extends

A keyword `extends` é usada nas classes para criar ela sendo filha de outra classe (de um jeito semelhante ao do java).


``class Animal {
  constructor(name){
    this.name = name;
  }
  
  speak() {
    console.log(this.name + " make a noise.")
  }
}

class Dog extends Animal {
  speak() {
    console.log(this.name + " barks.");
  }
}``

###Chamar a classe pai com 'super'

Você pode usar a keyword `super` para poder chamar uma função do mesmo nome se referindo à classe pai. É um pouco complicado abstrair isso só com essa frase, veja como funciona no exemplo abaixo.

``class Cat { 
  constructor(name) {
    this.name = name;
  }
  
  speak() {
    console.log(this.name + ' makes a noise.');
  }
}

class Lion extends Cat {
  speak() {
    super.speak();
    console.log(this.name + ' roars.');
  }
}``

