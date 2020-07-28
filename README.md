# My Javascript Guide

## Create promise with XMLHttpRequest

```javascript

var myPromise = function() {
  return new Promise(function(resolve, reject){
    var xhr = new XMLHttpRequest();
    
    xhr.open('GET', 'https://api.github.com/users/higosampaio');
    xhr.send(null);
    xhr.onreadystatechange = function() {
      if (xhr.readyState === 4) {
        if (xhr.status === 200) {
          resolve(JSON.parse(xhr.responseText));
        } else {
          reject('Erro na requisição');
        }
      }
    }
  });
}

myPromise()
  .then(function(response) {
    console.log(response);
  })
  .catch(function(error) {
    console.warn(error);
  })

```

## A simple requisition with Axios

```javascript

axios.get('https://api.github.com/users/higosampaio')
  .then(function(response) {
    console.log(response);
  })
  .catch(function(error) {
    console.warn(error);
  })

```

## Working with classes and extends

```javascript

class List {
  constructor() {
    this.data = [];
  }

  add(todo) {
    this.data.push(todo);
    console.log(this.data);
  }
}

class TodoList extends List {
  constructor() {
    super();

    this.nome = 'Higo Sampaio';
  }

  showNome() {
    console.log(this.nome);
  }
}

const MyTodoList = new TodoList();

document.querySelector('#todos').onclick = function() {
  MyTodoList.add('Meu novo todo');
};

MyTodoList.showNome();

```

## Array operations

### Maps all items in the array with value and position

```javascript

const arr = [1, 2, 3, 4, 5, 6, 7];

const newArr = arr.map(function(item, index){
  return item + index;
});

```

### Reduces the array to just one value

```javascript

const arr = [1, 2, 3, 4, 5, 6, 7];

const sum = arr.reduce(function(total, next) {
  return total + next;
});

```

### Filters values ​​in an array and returns a boolean

```javascript

const arr = [1, 2, 3, 4, 5, 6, 7];

const filter = arr.filter(function(item) {
  return item % 2 === 0;
});

```
 
### Finds a value in the array

```javascript

const arr = [1, 2, 3, 4, 5, 6, 7];

const find = arr.find(function(item) {
  return item === 10;
});

```

## Arrow function

### Default syntax

```javascript

const arr = [1, 2, 3, 4];

const newArr = arr.map((item) => {
  return item * 2;
});

```

### Only one param

```javascript

const arr = [1, 2, 3, 4];

const newArr = arr.map(item => {
  return item * 2;
});

```

### Only one operation

```javascript

const arr = [1, 2, 3, 4];

const newArr = arr.map(item => item * 2);

```

### Creating functions with different returns

```javascript

const functionTest = () => 'teste';

const test = () => [1, 2, 3];

const test = () => ({ nome: 'Higo' });

```

## Object destructuring

### Object destructuring in constant

```javascript

const usuario = {
  nome: 'Higo',
  idade: 29,
  endereco: {
    cidade: 'São Luís',
    uf: 'MA'
  }
};

const { nome, idade, endereco: { cidade } } = usuario;

console.log(nome);
console.log(idade);
console.log(cidade);

```

### Object destructuring in function

```javascript

const usuario = {
  nome: 'Higo',
  idade: 29,
  endereco: {
    cidade: 'São Luís',
    uf: 'MA'
  }
};

function mostrar({ endereco: { uf }, idade }) {
  console.log(uf, idade);
}

mostrar(usuario);

```

## Rest operator

### Rest with array destructuring

```javascript

const arr = [1, 2, 3, 4, 5];
const [a, b, ...c] = arr;

console.log(a);
console.log(b);
console.log(c);

```

### Return the rest of the params

```javascript

function soma(a, b, ...c) {
  return c;
}

console.log(soma(1, 2, 3, 4, 5, 6));

```

### Rest with reduce

```javascript

function newSoma(...params) {
  return params.reduce((total, next) => total + next);
}

console.log(newSoma(1, 2, 3, 4, 5, 6, 7, 8));

```

## Spread operator

### Array propagation

```javascript

const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const arr3 = [...arr1, ...arr2];

console.log(arr3);

```

### Reuse of objects

```javascript

const usuario1 = {
  nome: 'Higo',
  sobrenome: 'Sampaio',
  idade: 29
}
const usuario2 = { ...usuario1, sobrenome: 'Lobato', uf: 'MA' };

console.log(usuario2);

```

## Template literals

```javascript

const nome = 'Higo';
const idade = 29;

console.log(`Meu nome é ${nome} e tenho ${idade}`);

```

## Object Short Syntax

```javascript

const nome = 'Higo';
const idade = 29;
const usuario = {
  nome,
  idade,
  uf: 'MA'
};

console.log(usuario);

```
