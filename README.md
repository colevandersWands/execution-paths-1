learning objectives
* learning to trace execution more abstractly in terms of lines executed rather than operations & values


you can complete these exercises directly from your fork by inspecting this page and copy-pasting the snippets into devtools console. fill in your solutions by editing this page, writing in the actual values for each challenge

for each piece of code you will be given several inputs to study, ie.
> a:3, b:4    -->   1:?, 2:?, 3:?
each entry on the right hand side of the arrow represents an assertion point in the snippet.  the exercise here is to correctly fill in each of the blanks.

### The Challenges
* no control flow
    * [dots vs. brackets](#dots-vs-brackets)
* single conditionals
    * [if, else if, else](#if-else-if-else)  
    * [nested conditionals](#nested-conditionals)
* sequential conditionals
    * [else if -> nested](#else-if-nested)
* iteration
    * [fixed length](#fixed-length)
    * [repeating until](#repeating-until)
* conditionals & iteration
    * [iterations inside conditional](#iterations-inside-conditional)
    * [conditional inside iteration](#conditional-inside-iteration)
    * [conditional inside iteration inside conditional](#conditional-inside-iteration-inside-conditional)

---
---


## No Control Flow

---

### Block Scope 'var'

[on pytut](https://goo.gl/rJaPQo)  
[hoisting](https://github.com/elewa-academy/hoisting) 
[hoisting & blocks](https://github.com/elewa-academy/hoisting-and-blocks)
[let vs var](https://github.com/elewa-academy/block-scope-let-vs-var)  


the code:
(refresh the page each time before running this exercise)  
```js
{
  const expected_path = ;              
                       
  let b = ;  
  let c = ;                       const path = [];

  {
    var a = b;                    path.push(1);
    {
       a = c;                     path.push(2);
    }
    a = a;                        path.push(3);
  }

  const assert_act = JSON.stringify(path);
  const assert_exp = JSON.stringify(expected_path);
  console.assert(assert_act === assert_exp, path);
}
```
the values:
```js
b:2, c:3         --> [ ? ]
b:0, c:false     --> [ ? ]
b:false, c:9     --> [ ? ]
```
your notes:  

---

### Dots vs Brackets

[on pytut](https://goo.gl/2G6nuu)  
[extra resource](https://github.com/elewa-academy/variables-and-types/tree/master/dots-vs-brackets) 

the code:
```js
{
  const expected_path = ;            

  const arr = [];
  const obj = {a: 1, b: 2};
  const a = ;
  const b = ;                     const path = [];

  arr.push(obj.a);                path.push(1);
  arr.push(obj.b);                path.push(2);

  arr.push(obj[a]);               path.push(3);
  arr.push(obj[b]);               path.push(4);
  
  const assert_act = JSON.stringify(path);
  const assert_exp = JSON.stringify(expected_path);
  console.assert(assert_act === assert_exp, path);
}
```
the values:
```js
a:'a', b:'b'      --> [ ? ]
a:'a', b:'a'      --> [ ? ]
a:1, b:2          --> [ ? ]
a:2, b:1          --> [ ? ]
```
your notes:  

---
---


## Single Conditionals


### if, else if, else  

[on pytut](https://goo.gl/zhTS2m)

the code:
```js
{
  const expected_path = ;            
                     
  const a = ;
  const b = ;
  const c = ;
  let result = null;                const path = [];
  
  const condition_1 = b && a;       path.push(1);
  const condition_2 = a || c;       path.push(2);
  if (condition_1) {
    result = condition_1;           path.push(3);
  } else if (condtion_2) {
    result = condition_2;           path.push(4);
  } else {
    result = 'else';                path.push(5);
  };
  
  const assert_act = JSON.stringify(path);
  const assert_exp = JSON.stringify(expected_path);
  console.assert(assert_act === assert_exp, path);
}
```
the values:
```js
a:true, b:'', c:1       -->  [ ? ]
a:false, b:'', c:0      -->  [ ? ]
a:true, b:'', c:0       -->  [ ? ]
a:false, b:'', c:1      -->  [ ? ]
a:false, b:' ', c:1     -->  [ ? ]
a:true, b:' ', c:1      -->  [ ? ]
```
your notes:  

---



### nested conditionals

[on pytut](https://goo.gl/D9R3HS)

the code:
```js
{
  const expected_path = ;            
                     
  const a = ;
  const b = ;
  let result = null;                const path = [];
  
  if (a) {
    if (b) {
      result = 'w: ' + a + b;       path.push(1);
    } else {
      result = 'x: ' + a + b;       path.push(2);
    };
  } else {
    if (b) {
      result = 'y: ' + a + b;       path.push(3);
    } else {
      result = 'z: ' + a + b;       path.push(4);
    };
  };
  
  const assert_act = JSON.stringify(path);
  const assert_exp = JSON.stringify(expected_path);
  console.assert(assert_act === assert_exp, path);
}
```
the values:
```js
a:0, b:0    -->  [ ? ]
a:0, b:1    -->  [ ? ]
a:1, b:0    -->  [ ? ]
a:1, b:1    -->  [ ? ]
```
your notes:  

---
---

## Sequential Conditionals


### else if -> nested 

[on pytut](https://goo.gl/v9yCQi)

the code:
```js
{
  const expected_path = ;            
                     
  let a = ;
  let b = 
  let c = ;
  let result = null;                const path = [];
  

  if (b && a) {
    a = a || c;                     path.push(1);
  } else if (a || c) {
    b = b && a;                     path.push(2);
  } else {
    c = !a && !b;                   path.push(3);
  };

  if (a) {
    if (b) {
      result = 'w: ' + a + b;       path.push(4);
    } else {
      result = 'x: ' + a + b;       path.push(5);
    };
  } else {
    if (b) {
      result = 'y: ' + a + b;       path.push(6);
    } else {
      result = 'z: ' + a + b;       path.push(7);
    };
  };
  
  const assert_act = JSON.stringify(path);
  const assert_exp = JSON.stringify(expected_path);
  console.assert(assert_act === assert_exp, path);
}
```
the values:
```js
a:true, b:'', c:1       -->  [ ? ]
a:false, b:'', c:0      -->  [ ? ]
a:true, b:'', c:0       -->  [ ? ]
a:false, b:'', c:1      -->  [ ? ]
a:false, b:' ', c:1     -->  [ ? ]
a:true, b:' ', c:1      -->  [ ? ]
```
your notes:  

---
---


## Iteration

### Fixed length

[on pytut](https://goo.gl/YFn6Zd)

the code:
```js
{
  const expected_path = ;            
             
  const things = ;
  let result = null;                const path = [];
             
  let i = 0;                        path.push(1);
  while (i < things.length) {       path.push(2);
    result += things[i];            path.push(3);
    ++i;                            path.push(4);
  };

  
  const assert_act = JSON.stringify(path);
  const assert_exp = JSON.stringify(expected_path);
  console.assert(assert_act === assert_exp, path);
}
```
the values:
```js
things:[-1, 0, 1]            --> [ ? ]
things:[-3, -2, -1]          --> [ ? ]
things:[true, false, 1, 0]   --> [ ? ]
things:['words', 5, 1e3]     --> [ ? ]
things:[]                    --> [ ? ]
```
your notes:  

---

### Repeating Until

[on pytut](https://goo.gl/jbvs2o)

the code:
```js
{
  const expected_path = ;            
                     
  let a = ;
  let b = ;
  const c = ;
  let steps = 0;                 const path = [];
  
  while (a !== b) {              path.push(1);
    a -= c;                      path.push(2);
    b += c;                      path.push(3);
    steps++;                     path.push(4);
  };

  
  const assert_act = JSON.stringify(path);
  const assert_exp = JSON.stringify(expected_path);
  console.assert(assert_act === assert_exp, path);
}
```
the values:
```js
a:10, b:0, c:1      --> [ ? ]
a:8, b:2, c:1       --> [ ? ]
a:7, b:5, c:1       --> [ ? ]
a:13, b:1, c:3      --> [ ? ]
a:0, b:-28, c:7     --> [ ? ]
a:15, b:-9, c:3     --> [ ? ]
```
your notes:  

---
---


## Conditionals & Iteration


todo:
* iterations inside conditional
* conditionals inside iteration
* conditional inside iteration inside conditional


---

_the end_

___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>
