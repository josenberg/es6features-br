_"You can find the entire cosmos lurking in its least remarkable objects." - Wislawa Szymborska_ 

Artigo escrito com base nesse outro [aqui](http://www.htmlgoodies.com/beyond/javascript/js-ref/new-ecmascript-2015-features-part-ii.html).


Como você deve saber, as notations de objetos literais consistem de um lista com pares de name/value dentro de chaves `{}`. Nessa parte eles continuam iguais, porem dentro do `body` desses objetos as coisas ficam um pouco mais interessantes.

##Atalhos para propriedades Notations

Setar variaveis para um objeto literal sempre foi um problema por causa da duplicação do nome das variaveis. Agora, nos podemos tirar o nome dessas variaveis e simplesmente seta-las no objeto, depois referenciando-as do mesmo jeito que na EC5 utilizando `o.a` ou `o[a]`.

```
	//ES6
    var a = "foo",
        b = 42,
		c = {};
        
    var o = {
    	a: a,
        b: b,
        c: c
    };
    
    // Atalho da EC6
    var a = "foo",
        b = 42,
		c = {};
    var o = { a, b, c };
```

##Computed Property Names

Na EC6, uma expressão dentro de colchetes `[]` será disponivel dentro de si mesma. Antes da EC6 para usar um elemento de um objeto dentro dele mesmo você precisaria inicializa-lo e depois reescrever setando as propriedades que você gostaria, agora você pode fazer isso de uma maneira bem mais simples.

```
// ES5
var i = 0;
var o = {
  a: "foo",
  b: 42,
  c: {}
}
o['foo' + ++i] = i;
o['foo' + ++i] = i;
o['foo' + ++i] = i;
 
// ES6
var i = 0;
var o = {
  a: "foo",
  b: 42,
  c: {},
  ['foo' + ++i]: i,
  ['foo' + ++i]: i,
  ['foo' + ++i]: i
}
```

##Nomes de propriedades duplicados

Continuando o assunto sobre propriedades na EC6 quando você duplicava o nome de uma propriedade em strict mode, o JavaScript considerava isso como uma SintaxError. Porem agora com as `computed propertys` como isso seria algo comum de acontecer durante o runtime, o JS não retorna mais nenhum erro.

```
function testES6DuplicatePropertyNames(){
  "use strict";
  try {
    var test = { myprop: 1, myprop: 2 };
 
    // Não da erro na ES6
    return "ES6";
  } catch (e) {
    // Dá thrown na ES5
    return "ES5";
  }
}
```

##Jeitos mais simples de declarar funções

Não é um diferença muito grande, mas se você considerar alguns tipos de classe isso pode resultar em muito menos keywords no seu codigo, agora você não precisa escrever `function` para criar uma função dentro de um objeto literal.

```
// ES5
var cart = {
  _items: [],
  addItem: function(item) {
    this._items.push(item);
 
    return this;
  },
  toString: function() {
    return this._items.join(', ');
  }
}
 
// ES6
var cart = {
  _items: [],
  //function keyword omitted
  addItem(item) {
    this._items.push(item);
 
    return this;
  },
  //function keyword omitted
  toString() {
    return this._items.join(', ');
  }
}
```

##Assignments Desestruturados

Isso sim é uma grande ajuda quando se trabalha com objetos literais. Antes se você precisasse declarar varias propriedades dentro de um objeto literal você teria que fazer isso com todas elas individualmente, porem agora você pode dar assignment nelas em conjunto, como mostra no exemplo abaixo:

```
var planet = {
  positionFromTheSun: 3,
  radiusInKilometers: 6371,
  rotationTimeInHours: 24,
  yearlyCycle: 365,
  supportsLife: true
};
 
//ES5 assignment
var positionFromTheSun = planet.positionFromTheSun;
var radiusInKilometers = planet.radiusInKilometers;
var rotationTimeInHours = planet.rotationTimeInHours;
var yearlyCycle = planet.yearlyCycle;
var supportsLife = planet.supportsLife;
 
//ES6 assignment
var { positionFromTheSun, radiusInKilometers, rotationTimeInHours, yearlyCycle, supportsLife } = planet;
```

##Conclusão

É possivel notar um padrão entre a quantidades de linhas de uma aplicação quão a dificuldade de manutenção nele, se você conseguir usar esses atalhos para escrever menos codigo, sem duvidas nenhuma ele terá mais qualidade.

Seja um bom programador, escreva _menos_ codigo.