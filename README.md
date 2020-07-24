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

console.log(newArr);

```

### Reduces the array to just one value

```javascript

const arr = [1, 2, 3, 4, 5, 6, 7];

const sum = arr.reduce(function(total, next) {
  return total + next;
});

console.log(sum);

```

### Filters values ​​in an array and returns a boolean

```javascript

const arr = [1, 2, 3, 4, 5, 6, 7];

const filter = arr.filter(function(item) {
  return item % 2 === 0;
});

console.log(filter);

```
 
### Finds a value in the array

```javascript

const arr = [1, 2, 3, 4, 5, 6, 7];

const find = arr.find(function(item) {
  return item === 10;
});

console.log(find);

```
