# Typescript

## Types

```ts
let character: string = 'mario';
let age: number = 30;
let isBlackBelt: boolean = false;
let age: any = 25;
// MIXED
let age: (string| number) = 25
age = "five"
// ARRAY
let names: string[] = ["luigi", "mario", "yoshi"];
names.push("toad");
let numbers: number[] = [10, 20, 12, 15];
let mixed: (string | number)[] = ["ken", 4, "chun-li", 8, 9];

// objects
let ninja: {
  name: string;
  belt: string;
  age: number;
} = {
  name: "mario",
  belt: "black",
  age: 30,
};
```

## Function

```ts
const minus = (a: number, b: number): number => {
  return a + b;
}
function add(a: number, b: number): number {
  return a + b;
}
// functional params
function add(a: number, b: number, c?: number): number {
  return a + b;
}
// default params
function add(a: number, b: number, c: number = 20): number {
  return a + b;
}
```

## DOM

```ts
const form = document.querySelector('form')!;
const form = document.querySelector('.new-item-form') as HTMLFormElement;
console.log(form.children);

// inputs
const type = document.querySelector('#type') as HTMLInputElement;
const tofrom = document.querySelector('#tofrom') as HTMLInputElement;
const details = document.querySelector('#details') as HTMLInputElement;
const amount = document.querySelector('#amount') as HTMLInputElement;
form.addEventListener('submit', (e: Event) => {
  e.preventDefault();

  console.log(
    type.value, 
    tofrom.value, 
    details.value, 
    amount.valueAsNumber
  );
});
```

## Class

```ts
class Invoice {
  client: string;
  details: string;
  amount: number;

  constructor(c: string, d: string, a: number){
    this.client = c;
    this.details = d;
    this.amount = a;
  }
// can be written as 
 constructor(
    client: string, 
    details: string, 
    amount: number,
  ){}

  format() {
    return `${this.client} owes £${this.amount} for ${this.details}`;
  }
}
```

### Access modifiers

- public

- private

- protected

- readonly

```ts
 constructor(
    readonly client: string, 
    private details: string, 
    public amount: number,
  ){}
```

## Interface

its more like structure in c than an interface

```ts
 interface IsPerson {
  name: string;
  age?: number;
  speak(a: string): void;
  spend(a: number): number;
}
```


