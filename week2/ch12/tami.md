# π12- ν¨μ
μΌλ ¨μ κ³Όμ μ λ¬Άμ μ€ν λ¨μλ‘ μ€λ³΅μ μ κ±°νκ³  μ½λ μ¬μ¬μ©μ±μ λμΈλ€.
ν¨μλ νΈμΆν  μ μλ κ°μ²΄

### ν¨μμ μΈλ¬Έκ³Ό ν¨μ ννμ
```javascript=
//ν¨μμ μΈλ¬Έ 
function foo (x){ }

//ν¨μ ννμ
var a = function foo(x){}
```

#### ν¨μμ μΈλ¬Έ
- ν¨μ μ μΈλ¬Έμ μ€νλλ©΄μ μλ°μ€ν¬λ¦½νΈ μμ§μ΄ μλμΌλ‘ ν¨μ μ΄λ¦κ³Ό λμΌν κ°μ²΄(foo)λ₯Ό μμ±νλ€.
- μ¦ ν¨μμ μΈλ¬Έμ΄ μ μλλ©΄ ,ν¨μ ννμκ³Ό κ°μ΄ ν¨μκ° μ μΈλλ©΄ `var foo = function foo(x)` μ²λΌ μλνκ² λ§λλ κ²μ΄λ€
 - λ°νμ μ΄μ μ μ€νλλ€ -> ν¨μ νΈμ΄μ€νμ΄ μΌμ΄λλ€

### μΈμ νμΈ
JavaScript λ ν¨μ νΈμΆ μ λ§€κ°λ³μμ μΈμμ κ°μλ₯Ό νμΈνμ§ μλλ€.
- ν¨μνΈμΆ μ λ§€κ°λ³μμ κ°μλ μλ§μλ λλ€ (μλ€μ΄μ¨κ±΄ `undefined` μ΄κ³ νκ±΄ λ¬΄μ(argumentsκ°μ²΄μ λ€μ΄κ°))
- x+undefined = NaN



λ°λΌμ μ΄λ₯Ό μν μλ¬μ²λ¦¬κ° νμνλ°,


```javascript=
// νμμ²λ¦¬νκΈ°
function foo(x,y){
    if(typeof x !== string || typeof y !== string){
        throw new TypeError('μΈμλ λͺ¨λ μ«μμ¬μΌ ν©λλ€.')
    }
}

//λ¨μΆνκ°λ‘ λ§€κ°λ³μμ κΈ°λ³Έκ° ν λΉ
function foo(x,y){
    x == x||0
    y == y||0
}

```


## ν¨μν νλ‘κ·Έλλ°
- ν λ²μ νκ°μ§ μΌλ§ νλ ν¨μ
- λμΌν μλ ₯μ λμΌν μΆλ ₯μ λ³΄μ₯νλ€
μ¬κ·ν¨μ
- μμ μ κ³μ λΆλ₯΄λ ν¨μ
- νμΆ μ‘°κ±΄μ΄ μμ΄μΌ ν¨

κ³ μ°¨ν¨μ
- λ§€κ°λ³μλ‘ ν¨μλ₯Ό λ°κ±°λ ν¨μλ₯Ό returnνλ ν¨μ
- μ½λ°±ν¨μλ₯Ό μμ μ μΌλΆλΆμΌλ‘ ν©μ±
- `reduce`, `filter`, `map` ...
- 
μ½λ°±ν¨μ
- λ§€κ°λ³μλ‘ μλ ₯λλ ν¨μ
- κ³ μ°¨ν¨μ λ΄λΆμμλ§ μ€νλλ©΄ λ³΄ν΅ μ΅λͺ ν¨μλ¦¬ν°λ΄λ‘ κ³ μ°¨ν¨μμ μ λ¬λλ€.
- κ³ μ°¨ν¨μκ° μ€νλ λλ§λ€ μμ±
- λΉλκΈ° μ²λ¦¬ (Ajax, μ΄λ²€νΈ μ²λ¦¬ , νμ΄λ¨Έ ν¨μ)
```javascript=
foo(a, function (x){
    console.log(x)
})
```

μμν¨μ
- μΈλΆμ μν₯μ λ°κ±°λ λΌμΉμ§ μκ³  λμΌν κ°μ λ°ννλ ν¨μ

### ν¨μν νλ‘κ·Έλλ°
λΆλ³μ±μ μ§ν₯νλ νλ‘κ·Έλλ°
μμν¨μλ₯Ό ν΅ν΄ λΆμν¨κ³Όλ₯Ό μ΅λν μ΅μ νκ³  νλ‘κ·Έλλ°μ μμ μ±μ λμ΄λ κ³Όμ 
