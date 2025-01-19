# Verilən tipləri

JavaScript-də bir dəyişən istənilən veriləni ehtiva edə bilər. Bir dəyişən əvvəl `string` tipində ola bilər, sonra isə `number` tipinə çevrilə bilər.

```js
// xəta yoxdur
let message = "salam";
message = 123456;
```

Bu cür hallara icazə verən proqramlaşdırma dillərinə "dinamik tipli dillər" deyilir. Bu o deməkdir ki, verilən tipləri mövcuddur, lakin dəyişənlər həmin tiplərə bağlı deyil.

JavaScript-də 8 əsas verilən tipi mövcuddur. Bu fəsildə onları ümumi olaraq nəzərdən keçirəcəyik, növbəti fəsillərdə isə hər biri haqqında daha ətraflı danışacağıq.

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

  `NaN` "yapışqan" kimidir. Üzərində aparılan hər hansı bir əməliyyat yenə `NaN` qaytarır:

    ```js run
    alert( "rəqəm deyil" / 2 + 5 ); // NaN
    ```

  Yəni, əgər bir riyazi ifadədə `NaN` varsa, bu, nəticənin hamısına təsir edir.

```smart header="Riyazi əməliyyatlar təhlükəsizdir"
JavaScript-də riyazi əməliyyatlar "təhlükəsizdir". 0-a bölmə, ədədi olmayan sətirləri rəqəm kimi istifadə etmək və s. edə bilərik.

Ssenari heç vaxt ölümcül bir xəta ("fatal error") ilə sonlanmaz. Ən pis halda, nəticə olaraq `NaN` alarıq.
```

Xüsusi ədədi dəyərlər formal olaraq "rəqəm" (`number`) tipinə aiddir. Amma bu, onların həmişə adi ədədlər olduğu anlamına gəlmir.

Biz <info:number> fəslində rəqəmlərlə işləməyi daha ətraflı öyrənəcəyik.

## BigInt

JavaScript-də "rəqəm" (`number`) tipi <code>2<sup>53</sup></code>-dən böyük (və ya <code>-2<sup>53</sup></code>-dən kiçik) tam ədədləri ifadə edə bilmir. Bu, onların daxili təqdimatındakı texniki məhdudiyyətdir. Bu, təxminən 16 onluq rəqəmə bərabərdir və əksər hallarda bu məhdudiyyət problem yaratmır. Lakin bəzən, məsələn, kriptoqrafiya və ya mikro-saniyə dəqiqliyi ilə vaxt ölçmələri üçün çox böyük ədədlərə ehtiyac duyula bilər.

Dilə yaxın zamanda əlavə edilmiş `BigInt` tipi istənilən uzunluqda tam ədədləri təmsil etmək üçün istifadə olunur.

`BigInt` yaratmaq üçün tam ədədin sonuna `n` əlavə olunur:

```js
// sondakı "n" onun bir `BigInt` olduğunu bildirir
const bigInt = 1234567890123456789012345678901234567890n;
```

`BigInt` rəqəmlərə nadir hallarda ehtiyac duyulduğundan, bu mövzuya xüsusi bir fəsil (<info:bigint>) həsr etmişik.

```smart header="Uyğunluq problemləri"
Hal-hazırda `BigInt` Firefox və Chrome-da dəstəklənir, lakin Safari, IE və Edge-də dəstəklənmir.
```

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

JavaScript-də belə bir tip yoxdur. Yalnız bir verilən tipi var: `string`. Bir `string` bir və ya daha çox simvoldan ibarət ola bilər.
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

Yuxarıdakı kod, `age` dəyişənin dəyərinin nə üçünsə bilinməyən və ya boş olduğunu bildirir.

## The "undefined" value

The special value `undefined` also stands apart. It makes a type of its own, just like `null`.

The meaning of `undefined` is "value is not assigned".

If a variable is declared, but not assigned, then its value is `undefined`:

```js run
let x;

alert(x); // shows "undefined"
```

Technically, it is possible to assign `undefined` to any variable:

```js run
let x = 123;

x = undefined;

alert(x); // "undefined"
```

...But we don't recommend doing that. Normally, we use `null` to assign an "empty" or "unknown" value to a variable, and we use `undefined` for checks like seeing if a variable has been assigned.

## Objects and Symbols

The `object` type is special.

All other types are called "primitive" because their values can contain only a single thing (be it a string or a number or whatever). In contrast, objects are used to store collections of data and more complex entities. We'll deal with them later in the chapter <info:object> after we learn more about primitives.

The `symbol` type is used to create unique identifiers for objects. We mention it here for completeness, but we'll study it after objects.

## The typeof operator [#type-typeof]

The `typeof` operator returns the type of the argument. It's useful when we want to process values of different types differently or just want to do a quick check.

It supports two forms of syntax:

1. As an operator: `typeof x`.
2. As a function: `typeof(x)`.

In other words, it works with parentheses or without them. The result is the same.

The call to `typeof x` returns a string with the type name:

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

The last three lines may need additional explanation:

1. `Math` is a built-in object that provides mathematical operations. We will learn it in the chapter <info:number>. Here, it serves just as an example of an object.
2. The result of `typeof null` is `"object"`. That's wrong. It is an officially recognized error in `typeof`, kept for compatibility. Of course, `null` is not an object. It is a special value with a separate type of its own. So, again, this is an error in the language.
3. The result of `typeof alert` is `"function"`, because `alert` is a function. We'll study functions in the next chapters where we'll also see that there's no special "function" type in JavaScript. Functions belong to the object type. But `typeof` treats them differently, returning `"function"`. That's not quite correct, but very convenient in practice.

## Summary

There are 8 basic data types in JavaScript.

- `number` for numbers of any kind: integer or floating-point, integers are limited by ±2<sup>53</sup>.
- `bigint` is for integer numbers of arbitrary length.
- `string` for strings. A string may have one or more characters, there's no separate single-character type.
- `boolean` for `true`/`false`.
- `null` for unknown values -- a standalone type that has a single value `null`.
- `undefined` for unassigned values -- a standalone type that has a single value `undefined`.
- `object` for more complex data structures.
- `symbol` for unique identifiers.

The `typeof` operator allows us to see which type is stored in a variable.

- Two forms: `typeof x` or `typeof(x)`.
- Returns a string with the name of the type, like `"string"`.
- For `null` returns `"object"` -- this is an error in the language, it's not actually an object.

In the next chapters, we'll concentrate on primitive values and once we're familiar with them, we'll move on to objects.
