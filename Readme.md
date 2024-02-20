# Recursion
## Функсияи Рекурсивӣ.
Функсияи рекурсивӣ функсияест,ки худро дар ҷое дар дохили функсия даъват мекунад.
Намунаи асосии функсияи рекурсивӣ:


````Javascript
function recursiveFunc() {
  // some code here... 
  recursiveFunc()
}
````
Тавре ки шумо мебинед, recursiveFuncфунксия худро дар дохили функсия даъват мекунад. То он даме, ки натиҷаи дилхоҳ ба даст ояд, он зангро такрор мекунад.

  Барои қатъ кардани занги функсия аз шарти асоси истифода мекунем.
_____


## Се қисми функсияи рекурсивӣ
Ҳар дафъае, ки шумо функсияи рекурсивиро менависед, се элемент бояд мавҷуд бошад. 
+ Таърифи функсия.
+ Ҳолати асосӣ.
+ Даъвати рекурсивӣ.


## Функсияи рекурсивиро чӣ гуна муайян кардан мумкин аст.
Шумо функсияи рекурсивиро ҳамон тавре муайян мекунед, 
ки функсияҳои муқаррарии JavaScript-ро муайян мекунед.

````Javascript
function recursiveFunc() {
  // some code here...
} 
````
Он чизе, ки функсияҳои рекурсивӣ аз функсияҳои муқаррарии JavaScript фарқ мекунад, шарти асосӣ ва занги рекурсивӣ мебошанд.
___
## Шарти асосӣ чист?
Ҳангоми истифодаи функсияи рекурсивӣ, ҳолати асосӣ он чизест, ки ба функсия имкон медиҳад,
 ки кай занги худро қатъ кунад. Вақте ки шарти асосӣ иҷро мешавад, рекурсия ба охир мерасад.


````Javascript
function recursiveFunc() {
  if(base condition) {
    // stops recursion if condition is met
  }
  // else recursion continues
  recurse();
}
````
___
## Чаро шарти асосӣ лозим аст?
Бе шарти асосӣ, шумо ба рекурсияи беохир дучор мешавед. Ҳолате, ки функсияи шумо занги худро бидуни таваққуф идома медиҳад, масалан:


````Javascript
function doSomething(action) {
  console.log(`I am ${action}.`)
  doSomething(action)
}

doSomething("running")
````

____
## Намунаи функсияи рекурсивӣ.
  
````Javascript
function doSomething(n) {
  if(n === 0) {
    console.log("TASK COMPLETED!")
    return
  }
  console.log("I'm doing something.")
  doSomething(n - 1)
}
doSomething(3)
````
Ин аст натиҷа вақте ки шумо рақамро 3ба doSomethingфунксия мегузоред.
Шарти асосии функсия doSomethingин аст n === 0. Ҳар дафъае, ки функсия даъват карда мешавад, он аввал тафтиш мекунад, ки оё шарти асосӣ иҷро шудааст.

Агар ҳа, он чоп мекунад TASK COMPLETED!. Агар не, он бо қисми боқимондаи код дар функсия идома меёбад. Дар ин ҳолат, он чоп мекунад I'm doing something.ва боз функсияро даъват мекунад.
___

## Даъвати рекурсивӣ.
Даъвати рекурсивӣ он чизест, ки функсияро аз нав даъват мекунад. Дар doSomethingфунксия занги рекурсивӣ сатри зер аст.

````Javascript
doSomething(n-1)
````
Аҳамият диҳед, ки вақте ки функсия худашро даъват мекунад, чӣ мешавад. Параметри нав   n - 1ба функсия интиқол дода мешавад. Дар ҳар як такрори занги рекурсивӣ, параметр аз занги қаблӣ фарқ мекунад.

То он даме, ки параметри нав шарти асосиро қонеъ накунад, функсия худашро даъват мекунад.
____


## Чӣ тавр факториалро бо ҳалқа пайдо кардан мумкин аст:


````Javascript
function findFactorial(num) {
  let factorial = 1
  for (let i = num; i > 0; i--) {
    factorial *= i
  }
  return factorial
}

findFactorial(5) // 120
````
Барои пайдо кардани факториал бо истифода аз давра, шумо аввал тағирёбандаро factorialбо арзиши 1.

Пас шумо давраро бо рақами додашуда оғоз мекунед num. Давра то даме идома хоҳад дод i > 0.


Барои ҳар як такрор, шумо арзиши ҷории онро factorialбо зарб кунед i. Ва шумо арзиши i1-ро то он даме ки iаз сифр зиёд набошад, кам мекунед.

Дар ниҳоят, шумо арзиши факториалиро ҳангоми ба итмом расидани ҳалқа бармегардонед.

____

## JavaScript Closures.
Before you learn about closures, you need to understand two concepts:
+ Nested Function.
+ Returning a function.
 
 ### JavaScript Nested Function.
```` Javascript
// nested function example

// outer function
function greet(name) {

    // inner function
    function displayName() {
        console.log('Hi' + ' ' + name);
    }

    // calling inner function
    displayName();
}

// calling outer function
greet('John'); // Hi John
````
Дар барномаи дар боло зикршуда, greet()функсия дорои displayName()функсияи дохили он мебошад.


## Бозгашти функсия.
Дар JavaScript, шумо инчунин метавонед функсияро дар дохили функсия баргардонед. Барои намуна


````Javascript
function greet(name) {
    function displayName() {
        console.log('Hi' + ' ' + name);
    }

    // returning a function
    return displayName;
}

const g1 = greet('John');
console.log(g1); // returns the function definition
g1(); // calling the function
````
Натиҷа 
````Javascript
function displayName() { 
      console.log('Салом' + ' ' + ном); 
  } 
Салом Ҷон
````

## What is this closure in Java Script?

Closure Java Script хусусиятест, ки ба функсияӣ дохили имкон медиҳад, ки ба доираи берунии функсия дастрасӣ пайдо кунад.
 Closure   дар пайваст кардани функсия ба сарҳади берунии он кӯмак мекунад ва вақте ки функсия эҷод мешавад, ба таври худкор сохта мешавад. Аз ES6 блок инчунин ҳамчун миқёс баррасӣ карда мешавад. Азбаски JavaScript ба рӯйдодҳо асос ёфтааст, бинобар ин басташавӣ муфид аст, зеро он барои нигоҳ доштани ҳолати байни рӯйдодҳо кӯмак мекунад.

Қобилияти доираи функсия барои дастрасӣ ба тағирёбандаҳо аз доираи волидайн ҳамчун доираи лексикӣ маълум аст. Мо пайвастагии лексикии функсияи волидайнро ба функсияи кӯдак ҳамчун "пайвандии лексикӣ" меномем.


````Javascript
function foo() {
    let b = 1;
    function inner() {
        return b;
    }
    return inner;
}
let get_func_inner = foo();
 
console.log(get_func_inner());
console.log(get_func_inner());
console.log(get_func_inner());
````

Натиҷа:

Мо метавонем ба тағирёбандаи b , ки дар функсияи foo() тавассути функсияи inner() муайян шудааст, дастрас шавем, зеро баъдтар занҷири доираи функсияи иҳотакунандаро ҳангоми иҷрои функсияи иҳотакунанда нигоҳ медорад, яъне функсияи дохилӣ арзиши b -ро тавассути занҷири доираи он. Ин басташавӣ дар амал аст, ки функсияи дохилӣ метавонад ба тағирёбандаҳои функсияи беруна ва инчунин ҳама тағирёбандаҳои глобалӣ дастрасӣ дошта бошад.



