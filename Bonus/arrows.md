#Introdução

As funções são anonimas tem a sintaxe bem simples e curta, mas elas poderiam ser encurtadas ainda mais, ter que escrever milhões de `functions(){}` acaba deixando seu codigo um pouco feio, isso é um dos motivos para se usar arrows, o segundo é o `this` lexical dele que difere do default das funções, ele tem o mesmo contexto de onde a função foi declarada, isso significa que você não vai precisar mais declarar `self`. Lindo não?

##Definição

Na especificação da [MDN10](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Functions/Arrow_functions) as expressões arrows são definidas como:

> Uma expressão arrow function possui uma síntaxe mais curta quando comparada com expressões de função (function expressions) e vincula o valor de this de maneira léxica. Arrow functions sempre são anônimas.


**Sintaxe**

``([param] [, param]) => {
   statements
}``


**Vantagens**

Criar funções anonimas que são usadas apenas uma vez em um unico objeto se torna algo fantastico. Um exemplo bem comum disso é a função `map` em um array.

``var numbers = [1, 4, 9];
var doubles = numbers.map(function(num) { return num * 2; });``

Ele cria um array, e popula ele com os valores do primeiro array multiplicados por dois, você poderia fazer a mesma coisa utilizando arrows da seguinte forma:

``var numbers = [1, 4, 9];
var doubles = numbers.map(num => num * 2);``

Outra vantagem é que ela compartilha o this lexico do escopo onde ela foi implementada, segue o exemplo tirado da MDN

``function Pessoa() { 
  var self = this; // Alguns escolhem 'that' ao invés de 'self'.
      self.idade = 0;
      setInterval(function crescer() {
          // O callback referência a variável `self`
          self.idade++;
      }, 1000);
}``

No EcmaScript2015 você vai poder escrever ela sem precisar criar uma variavel pra guardar o contexto em que sua função tem que trabalhar, já que o `this` lexico é igual ao do lugar onde a função foi implementada, você pode reescrever essa função da seguinte forma:

``function Pessoa(){
  this.idade = 0;
    setInterval(() => {
        this.idade++; // |this| correto
    }, 1000);
}
``

Você vai poder jogar fora a maior parte das variaveis de contexto que você cria apenas para usar uma vez, isso sem duvidas melhora a qualidade do codigo e diminiu o 'mapemento mental' que é necessario para entender determinadas funções.

"Cupido e suas arrows de puro amor;"

Como arrows de cupido, essa nova feature do JavaScript sem duvidas é puro amorzinho.


(Eu tambem escrevi esse artigo no meu blog pessoal, assim se você quiser você pode se cadastrar no RSS e receber notificações de forma mais eficiente sobre o conteudo desse repositorio. [clique aqui para ver o artigo](http://josenberg.com.br/ecmascript-arrows/))