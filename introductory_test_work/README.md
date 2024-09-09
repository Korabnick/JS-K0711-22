# Ответы на вводную контрольную работу
## Часть 1: Теоретические вопросы

### 1. Что такое JavaScript и где он используется? Опишите основные области применения JavaScript.
- JavaScript - язык программирования используемый для создания интерактивных веб-страниц и приложений. Обычно используется в веб-разработке.

### 2. Объясните разницу между var, let и const. Когда следует использовать каждый из этих способов объявления переменных?
- var - имеет область видимости либо в функции либо глобальная. Переменная доступна до объявления. Переменную можно переобъявлять
- let - имеет область видимости внутри блока {}. Не доступна до объявления, повторно объявлять нельзя.
- const - имеет область видимости внутри блока {}. Не доступна до объявления. Повторно объявлять нельзя. Неизменяемая.

### 3. Что такое ECMAScript? Как ECMAScript связан с JavaScript, и почему его версии так важны для развития языка?
- ECMAScript - стандарт для JavaScript, его версии определяют новые функции и улучшения для JS.

### 4. Что такое замыкание (closure) в JavaScript? Приведите пример и объясните, как оно работает.
- Замыкание - функция, имеющая доступ к переменным из внешней функции, даже после того, как внешняя функция завершила выполнение. Пример:

```JavaScript
function outer() {
    let outerVar = 'I am outer';
    function inner() {
        console.log(outerVar);
    }
    return inner;
}
const innerFunc = outer();
innerFunc(); // Выведет 'I am outer'
```

### 5. Объясните, как работает this в JavaScript. Как контекст вызова влияет на значение this?
- this ссылается на объект, вызвавший текущую функцию. Контекст вызова влияет на значение this: в методе объекта this указывает на объект, в функции - на глобальный объект или undefined.

### 6. Какие методы работы с асинхронным кодом поддерживает JavaScript? Перечислите и кратко опишите их.
- 

### 7. Что такое объектно-ориентированное программирование (ООП) и как его поддерживает JavaScript? Упомяните ключевые концепции, такие как наследование, инкапсуляция, полиморфизм.
- 

### 8. Как в JavaScript работают массивы? Опишите несколько методов для работы с массивами (например, push, pop, map, filter, reduce).
- Массивы - это упорядоченные коллекции элементов, методами которого являются: push - добавляет элемент в конец массива, pop - удаляет последний элемент массива, map - создаёт новый массив с результатами вызова функции для каждого элемента, filter - создаёт новый массив с элементами, прошедшими проверку функции, reduce - применяет функции к элементам массива, чтобы получить одно значение.

## Часть 2: Практические задания
### 1. Напишите функцию, которая принимает строку и возвращает эту строку, написанную в обратном порядке. Например: "JavaScript" → "tpircSavaJ"
```JavaScript
function reverseString(str) {
    return str.split('').reverse().join('');
}

console.log(reverseString("JavaScript"));
```

### 2. Напишите программу, которая выводит все числа от 1 до 100, заменяя числа, кратные 3, на слово "Fizz", числа, кратные 5, на "Buzz", а числа, кратные и 3, и 5, на "FizzBuzz".
```JavaScript
for (let i = 1; i <= 100; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
        console.log("FizzBuzz");
    } else if (i % 3 === 0) {
        console.log("Fizz");
    } else if (i % 5 === 0) {
        console.log("Buzz");
    } else {
        console.log(i);
    }
}
```

### 3. Создайте объект person с полями name, age и методом introduce, который выводит в консоль строку вида: "Привет, меня зовут [имя], мне [возраст] лет". Создайте несколько экземпляров этого объекта с разными значениями и вызовите метод introduce для каждого из них.
```JavaScript
function Person(name, age) {
    this.name = name;
    this.age = age;
}

function getYearWord(age) {
    if (age % 10 === 1 && age % 100 !== 11) {
        return 'год';
    } else if ((age % 10 >= 2 && age % 10 <= 4) && !(age % 100 >= 12 && age % 100 <= 14)) {
        return 'года';
    } else {
        return 'лет';
    }
}

Person.prototype.introduce = function() {
    const yearWord = getYearWord(this.age);
    console.log(`Привет, меня зовут ${this.name}, мне ${this.age} ${yearWord}`);
}

const person1 = new Person("Альберт", 24);
const person2 = new Person("Иван", 25);
const person3 = new Person("Человек", 21);

person1.introduce();
person2.introduce();
person3.introduce();
```

### 4. Напишите функцию, которая принимает массив чисел и возвращает новый массив, содержащий только четные числа. Например: [1, 2, 3, 4, 5, 6] → [2, 4, 6]
```JavaScript
function filterEvenNumbers(numbers) {
    return numbers.filter(number => number % 2 === 0);
}

console.log(filterEvenNumbers([1, 2, 3, 4, 5, 6]));
```

### 5. Создайте класс Car с конструктором, принимающим параметры make, model и year. Добавьте метод getCarInfo, который возвращает строку с информацией о машине в формате "Машина: [make] [model], год выпуска: [year]". Создайте несколько объектов этого класса и вызовите метод для каждого из них.
```JavaScript
class Car {
    constructor(make, model, year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }

    getCarInfo() {
        return `Машина: ${this.make} ${this.model}, год выпуска: ${this.year}`;
    }
}

const car1 = new Car("Nissan", "GT-R R35 Nismo", 2013);
const car2 = new Car("Toyota", "Camry", 2020);
const car3 = new Car("Ford", "Mustang", 2021);

console.log(car1.getCarInfo());
console.log(car2.getCarInfo());
console.log(car3.getCarInfo());
```

### 6. Напишите функцию, которая принимает число и возвращает true, если оно простое, и false, если нет.
Число считается простым, если оно больше 1 и делится только на 1 и само на себя.
```JavaScript
function isPrime(num) {
    if (num <= 1) return false;
    if (num <= 3) return true;
    if (num % 2 === 0 || num % 3 === 0) return false;

    for (let i = 5; i * i <= num; i += 6) {
        if (num % i === 0 || num % (i + 2) === 0) return false;
    }

    return true;
}

console.log(isPrime(29));
console.log(isPrime(10));
```

### 7. Напишите асинхронную функцию, которая делает запрос к публичному API и выводит данные в консоль. В качестве примера можно использовать API JSONPlaceholder (https://jsonplaceholder.typicode.com/posts/1). В случае ошибки запроса функция должна вывести сообщение об ошибке.

### 8. Создайте функцию, которая генерирует случайный цвет в формате HEX (например, "#A3E12F"). Объясните, как работает генерация HEX-кода
```JavaScript
function generateRandomHexColor() {
    const letters = '0123456789ABCDEF';
    let color = '#';
    for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
    }
    return color;
}

console.log(generateRandomHexColor());
```
- Объяснение: HEX-код цвета состоит из символов 0-9 и A-F. Генерирую случайные символы и собираю их в строку. Строка начинается с #, за ним следуют 6 случайных символов.