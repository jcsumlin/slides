# TypeScript

## TypeScript

= superset of JavaScript with extensions:

- **static typing**
- public / private properties
- decorators

## static typing

data types may be specified in order to support the development environment:

- auto completion
- errors when types mismatch

## static typing

when building: TypeScript is translated to JavaScript, all type information is discarded

## type system: variables

```ts
let age: number = 32;
let name: string = 'Andreas';
```

## type system: arrays

```js
let names: Array = ['Anna', 'Bernhard'];
```

more detailed:

```js
let names: Array<string> = ['Anna', 'Bernhard'];
```

alternative Syntax:

```ts
let names: string[] = ['Anna', 'Bernhard'];
```

## type system: functions

```ts
function repeatString(
    text: string,
    times: number): string {
  return ...;
}
```

```ts
const repeatString = (
  text: string,
  times: number
): string => {...};
```

## type system: void

Void: can either be _undefined_ or _null_ - is often used with functions that don't return anything

```ts
function warnUser(): void {
  alert('warning!');
}
```

## type system: any

Any: variable can be of any type - disables the typechecker for this variable

```ts
let ib: any = document.getElementById('myinput');
console.log(ib.value);
```

## type system: type assertions

```ts
let someValue = jsonData.name;

let strLength = (someValue as string).length;
```

## type system: types & interfaces

Interfaces describe the structure of an object / of a class in Detail  
e.g.: `TodoInterface`, `PersonInterface`

Types are similar to interface, but are also applicable to strings, arrays, ...

Essentialy types offer more functionality than interfaces

https://stackoverflow.com/a/52682220/

## type system: types

```ts
type TodoType = {
  id: number;
  title: string;
  completed: boolean;
};

type TodoCollection = Array<TodoType>;
```

## Types and objects

```ts
type TodoType = {
  id: number;
  title: string;
  completed: boolean;
  // optional
  description?: string;
  // Methode
  toggle: (id: number) => void;
};
```

## Types and objects

```ts
class AdvancedTodo implements TodoType {
  ...
}
```

## Extends

Via `&`:

```ts
type ActionType = {
  type: string;
  payload?: object;
};

type AddTodoActionType = ReduxActionType & {
  type: 'ADD_TODO';
  payload: {
    title: string;
  };
};
```

## Union Types

```ts
type TodoActionType =
  | AddTodoActionType
  | ToggleTodoActionType;
```

## type system: generics

Generic type declarations that can receive more specific type information when called

```ts
function reducer<MyState, MyAction>(
  state: MyState,
  action: MyAction
): MyState {
  ...
}
```

usage:

```ts
// newState will automatically have the correct type
const newState = reducer<TodoState, TodoAction>(
  myTodoState,
  myTodoAction
);
```

## Generics

```ts
class Component<Props, State> {
  props: Props;
  state: State;

  setState: (newState: Partial<State>) => void;
}
```

usage:

```ts
class MyComp extends Component<MyProps, MyState> {
  ...
}
```

## private & public properties

```ts
class Clock {
  private formatTime(time) {
    return ...
  }
  public start() {
    ...
  }
}
```