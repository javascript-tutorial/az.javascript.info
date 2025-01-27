# Verilən tipləri

<<<<<<< HEAD
JavaScript-də bir dəyişən istənilən veriləni ehtiva edə bilər. Bir dəyişən əvvəl `string` tipində ola bilər, sonra isə `number` tipinə çevrilə bilər.
=======
A value in JavaScript is always of a certain type. For example, a string or a number.

There are eight basic data types in JavaScript. Here, we'll cover them in general and in the next chapters we'll talk about each of them in detail.

We can put any type in a variable. For example, a variable can at one moment be a string and then store a number:
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

```js
// xəta yoxdur
let message = "salam";
message = 123456;
```

<<<<<<< HEAD
Bu cür hallara icazə verən proqramlaşdırma dillərinə "dinamik tipli dillər" deyilir. Bu o deməkdir ki, verilən tipləri mövcuddur, lakin dəyişənlər həmin tiplərə bağlı deyil.

JavaScript-də 8 əsas verilən tipi mövcuddur. Bu fəsildə onları ümumi olaraq nəzərdən keçirəcəyik, növbəti fəsillərdə isə hər biri haqqında daha ətraflı danışacağıq.
=======
Programming languages that allow such things, such as JavaScript, are called "dynamically typed", meaning that there exist data types, but variables are not bound to any of them.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

## Rəqəm

```js
let n = 123;
n = 12.345;
```

*Number* tipi həm tam ədədləri, həm də onluq kəsirli ədədləri təmsil edir.

Rəqəmlər üçün vurma (`*`), bölmə (`/`), toplama (`+`), çıxma (`-`) və s. kimi bir çox əməliyyat mövcuddur.

Adi ədədlərlə yanaşı, bu verilən tipinə aid olan "xüsusi ədədi dəyərlər" də var: `Infinity`, `-Infinity` və `NaN`.

- `Infinity` riyaziyyatdakı [sonsuzluğu](https://en.wikipedia.org/wiki/Infinity) (`∞`) ifadə edir. Bu, xüsusi bir dəyərdir və hər hansı bir ədəddən böyükdür.

  Biz onu bir ədədi sıfıra bölməklə əldə edə bilərik:

    ```js run
    alert( 1 / 0 ); // Infinity
    ```

  Və ya birbaşa ona müraciət edə bilərik:

    ```js run
    alert( Infinity ); // Infinity
    ```

- `NaN` hesablama xətasını ifadə edir. Bu, səhv və ya qeyri-müəyyən bir riyazi əməliyyatın nəticəsidir. Məsələn:

    ```js run
    alert( "rəqəm deyil" / 2 ); // NaN, bu cür əməliyyat yanlışdır
    ```

<<<<<<< HEAD
  `NaN` "yapışqan" kimidir. Üzərində aparılan hər hansı bir əməliyyat yenə `NaN` qaytarır:

    ```js run
    alert( "rəqəm deyil" / 2 + 5 ); // NaN
    ```

  Yəni, əgər bir riyazi ifadədə `NaN` varsa, bu, nəticənin hamısına təsir edir.
=======
    `NaN` is sticky. Any further mathematical operation on `NaN` returns `NaN`:

    ```js run
    alert( NaN + 1 ); // NaN
    alert( 3 * NaN ); // NaN
    alert( "not a number" / 2 - 1 ); // NaN
    ```

    So, if there's a `NaN` somewhere in a mathematical expression, it propagates to the whole result (there's only one exception to that: `NaN ** 0` is `1`).
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

```smart header="Riyazi əməliyyatlar təhlükəsizdir"
JavaScript-də riyazi əməliyyatlar "təhlükəsizdir". 0-a bölmə, ədədi olmayan sətirləri rəqəm kimi istifadə etmək və s. edə bilərik.

Ssenari heç vaxt ölümcül bir xəta ("fatal error") ilə sonlanmaz. Ən pis halda, nəticə olaraq `NaN` alarıq.
```

Xüsusi ədədi dəyərlər formal olaraq "rəqəm" (`number`) tipinə aiddir. Amma bu, onların həmişə adi ədədlər olduğu anlamına gəlmir.

Biz <info:number> fəslində rəqəmlərlə işləməyi daha ətraflı öyrənəcəyik.

## BigInt [#bigint-type]

In JavaScript, the "number" type cannot safely represent integer values larger than <code>(2<sup>53</sup>-1)</code> (that's `9007199254740991`), or less than <code>-(2<sup>53</sup>-1)</code> for negatives.

To be really precise, the "number" type can store larger integers (up to <code>1.7976931348623157 * 10<sup>308</sup></code>), but outside of the safe integer range <code>±(2<sup>53</sup>-1)</code> there'll be a precision error, because not all digits fit into the fixed 64-bit storage. So an "approximate" value may be stored.

For example, these two numbers (right above the safe range) are the same:

```js
console.log(9007199254740991 + 1); // 9007199254740992
console.log(9007199254740991 + 2); // 9007199254740992
```

So to say, all odd integers greater than <code>(2<sup>53</sup>-1)</code> can't be stored at all in the "number" type.

<<<<<<< HEAD
JavaScript-də "rəqəm" (`number`) tipi <code>2<sup>53</sup></code>-dən böyük (və ya <code>-2<sup>53</sup></code>-dən kiçik) tam ədədləri ifadə edə bilmir. Bu, onların daxili təqdimatındakı texniki məhdudiyyətdir. Bu, təxminən 16 onluq rəqəmə bərabərdir və əksər hallarda bu məhdudiyyət problem yaratmır. Lakin bəzən, məsələn, kriptoqrafiya və ya mikro-saniyə dəqiqliyi ilə vaxt ölçmələri üçün çox böyük ədədlərə ehtiyac duyula bilər.
=======
For most purposes <code>±(2<sup>53</sup>-1)</code> range is quite enough, but sometimes we need the entire range of really big integers, e.g. for cryptography or microsecond-precision timestamps.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

Dilə yaxın zamanda əlavə edilmiş `BigInt` tipi istənilən uzunluqda tam ədədləri təmsil etmək üçün istifadə olunur.

<<<<<<< HEAD
`BigInt` yaratmaq üçün tam ədədin sonuna `n` əlavə olunur:
=======
A `BigInt` value is created by appending `n` to the end of an integer:
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

```js
// sondakı "n" onun bir `BigInt` olduğunu bildirir
const bigInt = 1234567890123456789012345678901234567890n;
```

<<<<<<< HEAD
`BigInt` rəqəmlərə nadir hallarda ehtiyac duyulduğundan, bu mövzuya xüsusi bir fəsil (<info:bigint>) həsr etmişik.

```smart header="Uyğunluq problemləri"
Hal-hazırda `BigInt` Firefox və Chrome-da dəstəklənir, lakin Safari, IE və Edge-də dəstəklənmir.
```
=======
As `BigInt` numbers are rarely needed, we don't cover them here, but devoted them a separate chapter <info:bigint>. Read it when you need such big numbers.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

## String

JavaScript-də bir [`string`](https://en.wikipedia.org/wiki/String_(computer_science)) mütləq dırnaqlar ilə əhatə olunmalıdır.

```js
let str = "Salam";
let str2 = 'Tək dırnaqlar da uyğundur';
let phrase = `başqa bir ${str} ehtiva edə bilər`;
```

JavaScript-də `string`-i ifadə etməyin 3 yolu mövcuddur.

1. Cüt dırnaq: `"Hello"`.
2. Tək dırnaq: `'Hello'`.
3. Tərs dırnaq: <code>&#96;Salam&#96;</code>.

Cüt dırnaq və tək dırnaqlar "sadə" dırnaqlar adlanır. JavaScript-də onların arasında demək olar ki, heç bir fərq yoxdur.

Tərs dırnaqlar "genişləndirilmiş funksionallıq" təklif edən dırnaqlardır. Onlar bizə dəyişənləri və ifadələri `${...}` arasına alaraq bir `string`-ə daxil etməyə imkan verir, məsələn:

```js run
let name = "Eldar";

// bir dəyişən daxil edin
alert( `Salam, *!*${name}*/!*!` ); // Salam, Eldar!

// bir ifadə daxil edin
alert( `nəticə: *!*${1 + 2}*/!*` ); // nəticə: 3
```

`${...}` arasındakı ifadə JavaScript mühərriki tərəfindən dəyərləndirilir və nəticə `string`-in bir hissəsinə çevrilir. Biz burada istənilən şeyi yaza bilərik: məsələn, `name` adlı bir dəyişən, `1 + 2` kimi riyazi bir ifadə və ya daha kompleks bir şey.

Qeyd edək ki, bu yanlız tərs dırnaqlar (backtricks: ``) üçün keçərlidir. Digər dırnaqlarda bu funksionallıq mövcud deyil.
```js run
alert( "nəticə: ${1 + 2}" ); // nəticə: ${1 + 2} (cüt dırnaqlar heç nə etmir)
```

Biz `string`-ləri <info:string> fəslində daha ətraflı izah edəcəyik.

```smart header="*character* tipi mövcud deyil."
Bəzi proqramlaşdırma dillərində yalnız bir simvolu saxlamaq üçün xüsusi bir verilənlər tipi mövcuddur. Məsələn, C və Java dillərində bu tip "char" adlanır.

<<<<<<< HEAD
JavaScript-də belə bir tip yoxdur. Yalnız bir verilən tipi var: `string`. Bir `string` bir və ya daha çox simvoldan ibarət ola bilər.
=======
In JavaScript, there is no such type. There's only one type: `string`. A string may consist of zero characters (be empty), one character or many of them.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3
```

## Boolean (məntiqi tip)

`boolean` tipi sadəcə 2 mümkün dəyərə sahibdir: `true` və `false`.

Bu tip ümumi olaraq hə/yox dəyərlərini saxlamaq üçün istifadə olunur: `true`, "bəli, doğrudur", `false` "xeyr, yanlışdır" mənasına gəlir.

Məsələn:

```js
let nameFieldChecked = true; // bəli, ad sahəsi yoxlandı
let ageFieldChecked = false; // xeyr, yaş sahəsi yoxlanmadı
```

`boolean` tipi həm də nəticələrin müqayisəsində istifadə edilir:

```js run
let isGreater = 4 > 1;

alert( isGreater ); // true (müqayisənin nəticəsi "doğru"dur)
```

Biz `boolean` tipini <info:logical-operators> fəslində daha dərindən izah edəcəyik.

## "null" dəyəri

Xüsusi bir dəyər olan `null`, yuxarıda təsvir edilən tiplərdən heç birinə aid deyil.

Bu dəyər yalnız özünə məxsus ayrıca bir tipdir və bu tip sadəcə `null` dəyərindən ibarətdir.

```js
let age = null;
```

JavaScript-də `null`, "mövcud olmayan bir obyektə referans" və ya digər dillərdə olduğu kimi "null göstərici (null pointer)" anlamına gəlmir.

Bu sadəcə xüsusi bir dəyərdir və "heç nə", "boş" və ya "bilinməyən dəyər"i ifadə edir.

<<<<<<< HEAD
Yuxarıdakı kod, `age` dəyişənin dəyərinin nə üçünsə bilinməyən və ya boş olduğunu bildirir.
=======
The code above states that `age` is unknown.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

## "undefined" dəyəri

Xüsusi bir dəyər olan `undefined` da ayrıca bir mövqeyə malikdir. Bu, özünəməxsus bir tip meydana gətirir.

`undefined` dəyəri, "dəyər təyin edilməyib" anlamına gəlir.

Əgər bir dəyişən elan olunubsa, lakin onun üçün heç bir dəyər təyin edilməyibsə, onun dəyəri `undefined` olacaq:

```js run
let age;

<<<<<<< HEAD
alert(x); // "undefined" göstərir
```

Texniki olaraq, `undefined` istənilən dəyişənə mənimsədilə bilər:
=======
alert(age); // shows "undefined"
```

Technically, it is possible to explicitly assign `undefined` to a variable:
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

```js run
let age = 100;

// change the value to undefined
age = undefined;

alert(age); // "undefined"
```

<<<<<<< HEAD
... Amma biz bunu etməyi tövsiyə etmirik. Normalda "boş" və ya "bilinməyən" bir dəyəri ifadə etmək üçün `null` istifadə olunur. `undefined` isə əsasən dəyişənin dəyərinin mənimsədildiyini yoxlamaq üçün istifadə edilir.
=======
...But we don't recommend doing that. Normally, one uses `null` to assign an "empty" or "unknown" value to a variable, while `undefined` is reserved as a default initial value for unassigned things.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

## Obyektlər (Objects) və Simvollar (Symbols)

`object` xüsusi bir tipdir.

<<<<<<< HEAD
Bütün digər tiplər "primitiv (primitive)" tip adlanır, çünki, onların dəyərləri yalnız bir şey (məsələn, bir `string`, `number` və ya başqa bir şey) ehtiva edə bilər. Bunun əksinə olaraq, obyektlər verilən kolleksiyalarını və daha mürəkkəb quruluşları saxlamaq üçün istifadə olunur. Primitiv tipləri daha yaxşı öyrəndikdən sonra obyektlər mövzusuna <info:object> fəslində toxunacağıq.

`symbol` tipi obyektlər üçün unikal identifikatorlar yaratmaqda istifadə olunur. Onu burada tamlıq üçün qeyd edirik, lakin obyektləri öyrəndikdən sonra bu mövzuya qayıdacağıq.

### `typeof` operatoru [#type-typeof]

`typeof` operatoru arqumentin tipini qaytarır. Fərqli tipləri müxtəlif üsullarla işləmək lazım olduqda və ya sadəcə sürətli bir yoxlama aparmaq istədikdə çox faydalıdır.

Bu operator iki sintaksisi dəstəkləyir:

1. Operator kimi: `typeof x`.
2. Funksiya kimi: `typeof(x)`.

Başqa sözlə, mötərizələrlə və ya mötərizəsiz istifadə edilə bilər. Hər iki halda nəticə eyni olur.

`typeof x` ifadəsi arqumentin tipini `string` formatında qaytarır:
=======
All other types are called "primitive" because their values can contain only a single thing (be it a string or a number or whatever). In contrast, objects are used to store collections of data and more complex entities.

Being that important, objects deserve a special treatment. We'll deal with them later in the chapter <info:object>, after we learn more about primitives.

The `symbol` type is used to create unique identifiers for objects. We have to mention it here for the sake of completeness, but also postpone the details till we know objects.

## The typeof operator [#type-typeof]

The `typeof` operator returns the type of the operand. It's useful when we want to process values of different types differently or just want to do a quick check.

A call to `typeof x` returns a string with the type name:
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

```js
typeof undefined // "undefined"

typeof 0 // "number"

typeof 10n // "bigint"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

*!*
typeof Math // "object"  (1)
*/!*

*!*
typeof null // "object"  (2)
*/!*

*!*
typeof alert // "function"  (3)
*/!*
```

Son üç sətir əlavə izah tələb edə bilər:

<<<<<<< HEAD
1. `Math` riyazi əməliyyatlar təqdim edən daxili obyektlərdən biridir. Biz onu <info:number> fəsilində daha ətraflı öyrənəcəyik. Burada isə, sadəcə obyektin bir nümunəsi kimi istifadə olunub.
2. `typeof null` nəticəsi `"object"` olaraq qaytarılır. Bu, səhvdir. Bu, `typeof` operatorunun rəsmi olaraq tanınmış bir xətasıdır və uyğunluq səbəbilə saxlanılıb. Əslində, `null` bir obyekt deyil. O, ayrıca bir tipə malik xüsusi bir dəyərdir. Beləliklə, bu, JavaScript dilində mövcud olan bir qüsurdur.
3. `typeof alert` nəticəsi `"function"` olur, çünki, `alert` bir funksiyadır. Biz funksiyaları növbəti fəsillərdə öyrənəcəyik. Orada görəcəyik ki, əslində JavaScript-də xüsusi bir "function" tipi yoxdur. Funksiyalar `object` tipinə daxildir. Lakin, `typeof` funksiyalara fərqli davranaraq `"function"` kimi qaytarır. Bu tam doğru deyil, lakin praktikada çox rahatdır.
=======
1. `Math` is a built-in object that provides mathematical operations. We will learn it in the chapter <info:number>. Here, it serves just as an example of an object.
2. The result of `typeof null` is `"object"`. That's an officially recognized error in `typeof`, coming from very early days of JavaScript and kept for compatibility. Definitely, `null` is not an object. It is a special value with a separate type of its own. The behavior of `typeof` is wrong here.
3. The result of `typeof alert` is `"function"`, because `alert` is a function. We'll study functions in the next chapters where we'll also see that there's no special "function" type in JavaScript. Functions belong to the object type. But `typeof` treats them differently, returning `"function"`. That also comes from the early days of JavaScript. Technically, such behavior isn't correct, but can be convenient in practice.

```smart header="The `typeof(x)` syntax"
You may also come across another syntax: `typeof(x)`. It's the same as `typeof x`.

To put it clear: `typeof` is an operator, not a function. The parentheses here aren't a part of `typeof`. It's the kind of parentheses used for mathematical grouping.

Usually, such parentheses contain a mathematical expression, such as `(2 + 2)`, but here they contain only one argument `(x)`. Syntactically, they allow to avoid a space between the `typeof` operator and its argument, and some people like it.

Some people prefer `typeof(x)`, although the `typeof x` syntax is much more common.
```
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

## Xülasə

JavaScript-də 8 sadə verilən tipi mövcuddur:

<<<<<<< HEAD
- **`number`**: İstənilən növ rəqəmlər üçün, tam və ya onluq kəsr dəyərləri daxildir. Tam ədədlər ±2<sup>53</sup> həddində məhdudlaşdırılıb.
- **`bigint`**: İxtiyari uzunluqlu tam ədədlər üçündür.
- **`string`**: "mətn" tipidir. Bir `string` bir və ya daha çox simvolu ehtiva edə bilər. Tək simvol üçün ayrıca bir tip mövcud deyil.
- **`boolean`**: `true` və `false` məntiqi dəyərləri üçün istifadə olunur.
- **`null`**: Naməlum dəyərlər üçün nəzərdə tutulmuş ayrıca bir tipdir, yalnız `null` dəyərinə sahibdir.
- **`undefined`**: Mənimsədilməmiş dəyərlər üçün ayrıca bir tipdir, yalnız `undefined` dəyərinə sahibdir.
- **`object`**: Daha mürəkkəb verilən strukturlarını saxlamaq üçün istifadə olunur.
- **`symbol`**: Unikal identifikatorlar yaratmaq üçün istifadə olunur.
=======
- Seven primitive data types:
    - `number` for numbers of any kind: integer or floating-point, integers are limited by <code>±(2<sup>53</sup>-1)</code>.
    - `bigint` for integer numbers of arbitrary length.
    - `string` for strings. A string may have zero or more characters, there's no separate single-character type.
    - `boolean` for `true`/`false`.
    - `null` for unknown values -- a standalone type that has a single value `null`.
    - `undefined` for unassigned values -- a standalone type that has a single value `undefined`.
    - `symbol` for unique identifiers.
- And one non-primitive data type:
    - `object` for more complex data structures.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

`typeof` dəyişənin tipini müəyyənləşdirməyə imkan verir:

<<<<<<< HEAD
- İki sintaksis mövcuddur: `typeof x` və ya `typeof(x)`.
- `string` olaraq tipin adını qaytarır, məsələn, `"string"`.
- `null` dəyəri üçün `"object"` qaytarır -- bu, dilin daxilində olan bir səhvdir. Əslində, `null` bir obyekt deyil.
=======
- Usually used as `typeof x`, but `typeof(x)` is also possible.
- Returns a string with the name of the type, like `"string"`.
- For `null` returns `"object"` -- this is an error in the language, it's not actually an object.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

Növbəti fəsillərdə, əvvəlcə ibtidai (primitive) dəyərləri öyrənəcəyik və onlarla tanış olduqdan sonra obyektlərə keçəcəyik.