## TypeScript

O TypeScript foi criado pela Microsoft para trazer um superset de tipagem para o JavaScript.

A diferença entre o JavaScript para o TypeScript é um tipagem que no JS não é obrigatório, já no TS é obrigatório, mas nem para todos os casos. Algumas vantagens de utilizar o TS é que sua adoção pode ocorrer de forma gradual em um projeto JavaScript.


## Varificação de tipos estáticos

- Ts verifica erros antes da execução 

```ts

const userName = 'Lucas alves'

userName() // aqui o ts apresenta erro porque userName não é função mas sim string
```

## Compilação
O TypeScript é sempre compilado para o JavaScript, mas normalmente não estamos vendo isso.

## Tipagem explícita
Aqui especificamos o qual será o tipo para cada variável.

```ts
   // user: string, ticket: string

function showTicket(user: string, ticket: string) {
    console.log(`Olá ${user}. Seu número de bilhete é: ${ticket}`)
}

// O TypeScript nos ajuda a identificar o tipo da variável ao invocá-las
```

## Tipagem Any

Ao declarar uma variável por padrão o seu tipo é ```any```
Porém não é muito recomendado a sua utilização.

```ts
let info: any; 

info = [123]
info = 'joão'
info = true
info = 10.50

// com o tipo any a variável aceitará qualquer valor.
```

## Inferência de tipos 
O Ts reconhece automaticamente o tipo de variável ao passar algum valor para ela.

```ts
let user = 'João'

user = 10 // identificara automaticamente o erro
```
## Tipos primitivos

```ts
let loading: boolean
loading = false 


let email: string
email = 'lucas.alves@email.com'

let price: number
price = 10.50
price = 10
```

## Matrizes

Existem duas meneiras de tipar arrays no TypeScript

```ts 

let number: number[]
number = [1, 2, 3, 4, 5]


let users: array<string>
users = ['Lucas', 'Henrique']

```

## Funções

Uma função pode ter ou não um retorno, quando ela não tem um retorno ela é do tipo void

Dessa maneira, tipamos dessa forma no TypeScript:
```ts
function showMessages(message: string):void {
    console.log(message)
}
console.log(showMessages("Oi, João"))
```

Já quando a função tem um retorno, a tipagem é inferida automaticamente na função.
```ts
function showMessages(message: string) {
   return message;
}

console.log(showMessages("Oi, João"))
```

## Union
O Operador Union, representado pelo pipe | nos permite adicionar mais de um tipo na variável. Vamos ao exemplo:
```ts
function printUserId(id: number | string) {
    console.log(`O ID do usuário é: ${id}`);
}

printUserId(101);
printUserId("101");

// Dessa forma, podemos passar tanto number quanto string
```

## Generics
O generic no TypeScript nos permite reutilizar uma determinada implementação de código, de forma tipada. Para representar um generic, nós declaramos ele dessa forma <T> (podendo ser utilizado qualquer outra letra, existem as convenções que podemos seguir:

- S → Representando State 
- T → Representando Type 
- K → Representando Key 
- V → Representando Value 
- E → Representando Element

Exemplo de um trecho de código utilizando generics:
```ts
function useState<T>() {
    let state: T;

    function get(){
        return state;
    }

    function set(newValue: T){
        state = newValue;
    }

    return { get, set}
}

let newState = useState();
newState.get();
newState.set("João");
newState.set(123);
```


