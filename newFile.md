
# _JavaScript ES6 - Higher Order Functions - Map e Reduce (9.2)_

- Você aprendeu até agora diversas funções sobre Arrays, e hoje vai aprender sobre mais duas _Higher Order Functions_ extremamente potentes e importantes no dia a dia da pessoa desenvolvedora de _software_, são elas Array.map e Array.reduce.
---

## Você será capaz de:

- Manter uma melhor legibilidade e manutenibilidade do código;
- Escrever código simples e conciso;
- Utilizar o conceito de imutabilidade, o resultado da nova lista nunca irá alterar os valores da lista original;

---

## Por que isso é importante?

- A resolução de problemas faz parte do desafio diário da pessoa desenvolvedora, e conhecer as ferramentas que podem te auxiliar é extremamente importante.
---

## Conteúdo
### Array.map
O método _Array.map_ tem o funcionamento similar aos métodos aprendidos no dia 9.1. Map passa por todas as posições de um array aplicando o que sua função pede a todos os elementos, e no final retorna um novo Array com seus novos valores.

Suponha que você tem o seguinte Array de inteiros:

```javascript
const array = [0, 1, 2, 3, 4, 5];
```

Se quisermos adicionar 10 unidades em cada posição com o Array.map, ficaria na seguinte forma:

```javascript
const novoArray = array.map((unidade)=> unidade + 10);
```

Há alguns detalhes que são de importante observação:

- "unidade" é o parâmetro da função, ele assume o valor de cada posição do array e pode ser nomeado da forma que identificar melhor o que você possui dentro do Array.
- Foi necessário atribuir o resultado ao novoArray, se isso não fosse feito, **não seria possível em outros momentos do código acessar esse valor sem realizar o map novamente**.
- O valor de array fica como  [0, 1, 2, 3, 4, 5], já novoArray é [10, 11, 12, 13, 14, 15];

É importante também tomar cuidado com condicionais dentro de map, aqui vai um exemplo de como poderia gerar um problema:
```javascript
  const array = [0,1,2,3,4,5];                                                                                                           
  const newArray = array.map((unidade)=> {                                                                                               
    if(ele % 2 === 0) return unidade;
  });
```
O novo array gerado seria [0, undefined, 2, undefined, 4, undefined], mas por que isso aconteceu? **Array.map sempre vai retornar um array com o mesmo tamanho do array original**, como não havia valor de retorno quando o número é impar ele entende que o valor dessa posição era undefined, logo, o melhor metodo nesse caso para retornarmos somente os números pares, seria Array.filter aprendido no dia 9.1.

#### Para fixar:
- Utilize map no array [10, 17, 26, 31, 7] para criar um array onde números impares tem seu valor multiplicado por 3, e números pares por 2;

Agora que você ja entendeu o basico de Array.map, ja pode avançar e entender um pouco mais do pontencial deste metodo, suponha que os arrays:
```javascript
const nomes = ['João', 'Augusto', 'Henrique'];
const valores = [10.99, 15.00, 24.59];
```
Estes arrays possuem o nome do cliente e quanto cada um gastou em compras, não precisamos de muito esforço para entender que guardar os dados dessa forma se mostra ineficaz, visto que o entendimento de quem gastou quanto se torna realmente difícil. O metodo map vem como uma solução para isso, observe o codigo abaixo onde é criado um **array de objetos** a partir destes dois arrays:

```javascript
  const valoresGastos = nomes.map((nome, index)=> ({ [nome]: valores[index] }));
```
valoresGastos representa o seguinte objeto:
```javascript
  valorsGastos= [{ João: 10.99 }, { Augusto: 15.00 } , { Henrique: 24.59 }];
```
#### Para fixar:
- Crie um array de objetos com os arrays ['Laranja', 'Banana', 'Maça'] e [3.39, 5.98 , 12.90] onde cada objeto deve ter o modelo { nome: 'Laranja', preço: 3.39 };
---
