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

## Type
Para não ficar sempre repetindo os tipos para todas as variáveis podemos criar Types para cada uma delas.

Veja o exemplo a seguir:
```ts
type IdType = string | number | undefined;

let userId: IdType;
let adminId: IdType;

userId = 1;
userId = '1';
userId = undefined;

adminId = 1;
adminId = '2';
adminId = undefined;
```

## Type Assertions
Asserção de tipo normalmente é utilizado quando o TypeScript não sabe qual é a tipagem em um determinado objeto.

Para contornarmos isso, podemos criar um type informando quais são as propriedades desse objeto.
```ts
type UserResponse = {
    id: number;
    name: string;
    avatar: string;
}

let userResponse = {} as UserResponse;
```

## Objetos
Nessa aula vamos aprendemos como criar tipagens utilizando objetos no TypeScript.

Segue o exemplo:
```ts
type Point = {
    x: number;
    y: number;
}

function printCoord(points: Point) {
    console.log(`O eixo x é: ${points.x}`)
    console.log(`O eixo y é: ${points.y}`)
}

printCoord({x: 101, y: 50})
Resultado do log:

[LOG]: "O eixo x é: 101"
------------------------
[LOG]: "O eixo y é: 50"
```
## Opcional
Para informamos que uma propriedade é opcional inserimos o sinal de ?

Veja o exemplo:
```ts
type User = {
    name: string;
    email: string;
    age: number;
    isAdmin?: boolean; // isAdmin não será obrigatória na sua declaração
}

let newUser: User = {
    name: 'João',
    email: 'joao@email.com',
    age: 18
}
```

## Intersecção de tipos
A intersecção de tipos como o próprio nome já diz, podemos unir dois tipos e usar as suas propriedades dentro de um objeto.

Segue o exemplo abaixo:
```ts
type User = {
    id: number,
    name: string,
}

type Char = {
    nickname: string,
    level: number
}

type PlayerInfo = User & Char;

let info: PlayerInfo = {
    id: 1,
    name: 'João Inácio',
    nickname: 'birobirobiro',
    level: 50
}
```
## Interface
Outra maneira de criar tipagens no TypeScript é utilizando a interface .

Segue o exemplo:
```ts
interface User {
    id: number
    name: string,
}

let newUser: User = {
    id: 1,
    name: "João"
}

function registerNewUser(newUser: User){
    newUser.id
    newUser.name
}
```

## Type e Interface
Descrição
Type e Interface
O objetivo de ambos serve para definir tipagens no TypeScript. O type é mais recomendado por ser mais simples, fácil de lidar com tipos primitivos, por ser mais flexível. Já as interfaces são utilizadas normalmente em criação de libs, para aqueles que gostam da programação orientada a objetos.

O exemplo abaixo mostra a diferença na sintaxe e união entre type e inteface:
```ts
type TUser = {
    id: number;
    name: string;
}

type TPayment = {
    method: string;
}

// Fazendo união com Type
type TAccount = TUser & TPayment

interface IUser {
    id: number;
    name: string;
}

interface IPayment {
    method: string;
}

// Fazendo união com interfaces
interface IAccount extends IUser, IPayment {}
```


