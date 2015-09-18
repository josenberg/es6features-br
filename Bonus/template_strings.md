Strings no JavaScript são historicamente limitadas, muitas funcionalidades simples do Python ou do Ruby simplesmente não existem no JS. ES6 chegou para mudar isso. Esse novo padrão permite a criação de strings com DSLs (doman-specific languages), trazendo melhorias em:

* Interpolação de strings
* Expressões embedadas
* Strings com multiplas linhas sem hacks

Mas em vez de aumentar o pacote de strings já existente, Templates Strings introduzirá uma maneira completamente diferente de resolver esse problemas.

##Sintaxe

Template String não usam aspas, elas usam crases (`\`\``), tirando isso elas são como strings normais e podem ser declaradas da seguinte forma:

``var greeting = \`Yo World!\`;``

##String Substitution

Uma das primeiras vantagens é a `string substitution`. Substituições nos permitem inserir qualquer expressão valida do JavaScript (incluindo operações matematicas) dentro de um `String Template`, e o resultado dessa expressão fará parte do output dessa string.

Template Strings podem usar uma o simbolo `${}` para escrever seus as expressões. Como podemos ver abaixo.

```
    //Simples string substituion
    var name = "Brendan";
    console.log(\`Yo, ${name}!\`);
	
    // => "Yo, Brendan!"
```

Como essas substituições são na verdade expressões JS nos podemos usar muito mais que o nome das variaveis. Por exemplo, abaixo nos usamos uma expressão matematica dentro de um string template:

```
    var a = 10;
    var b = 10;
    console.log(`JavaScript foi criada à ${a+b} anos atras. Maneiro!`);
    // => "JavaScript foi criada à 20 anos atras. Maneiro!"

    console.log(`Existindo até multiplicações como: ${2 * (a+b)}`);
    // => Existindo até multiplicações como: 20
```

Elas tambem podem ser usadas para inserir funções dentro das strings.

```
	function fn(){ return "Ola"; }
    console.log(`${fn()}, como vai você?`);
    //=> Ola, como vai você ?
```

Um exemplo mais real do uso de funcoes dentro de strings:

```
var user = {name: 'Anakin Skywalker'};
console.log(`Venha para o lado negro, ${user.name.toUpperCase()}.`);

// => "Venha para o lado negro, ANAKIN SKYWALKER";
```

##String com multiplas linhas

Uma string com diversas linhas no javascript requerem alguns truques, atualmente para poder fazer isso você precisa usar o simbolo `\\` no fim de cada linha. Por exemplo:

```
var greeting = "Yo \
World";
```

Apesar de isso funcionar em quase todos os navegadores modernos a sintaxa ainda deixa um pouco à desejar, um outro jeito que podemos fazer isso sem usar Templates Strings é usar a concatenação de strings para 'enganar' a quebra de linha do JavaScript.

```
var greeting = "Yo " +
"World";
```

Isso é bem mais simples quando usamos templates strings, basta você quebrar a linha e esta feito.

```
console.log(\`string texto da primeira linha
texto da segunda linha \`);
```

Existem outras vantagens tambem como o tagging desses templates, mas isso é assunto para outro post.


Testo baseado nesse [artigo](https://developers.google.com/web/updates/2015/01/ES6-Template-Strings), em caso de duvidas verifique o original.

	