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

## "undefined" dəyəri

Xüsusi bir dəyər olan `undefined` da ayrıca bir mövqeyə malikdir. Bu, özünəməxsus bir tip meydana gətirir.

`undefined` dəyəri, "dəyər təyin edilməyib" anlamına gəlir.

Əgər bir dəyişən elan olunubsa, lakin onun üçün heç bir dəyər təyin edilməyibsə, onun dəyəri `undefined` olacaq:

```js run
let x;

alert(x); // "undefined" göstərir
```

Texniki olaraq, `undefined` istənilən dəyişənə mənimsədilə bilər:

```js run
let x = 123;

x = undefined;

alert(x); // "undefined"
```

... Amma biz bunu etməyi tövsiyə etmirik. Normalda "boş" və ya "bilinməyən" bir dəyəri ifadə etmək üçün `null` istifadə olunur. `undefined` isə əsasən dəyişənin dəyərinin mənimsədildiyini yoxlamaq üçün istifadə edilir.

## Obyektlər (Objects) və Simvollar (Symbols)

`object` xüsusi bir tipdir.

Bütün digər tiplər "primitiv (primitive)" tip adlanır, çünki, onların dəyərləri yalnız bir şey (məsələn, bir `string`, `number` və ya başqa bir şey) ehtiva edə bilər. Bunun əksinə olaraq, obyektlər verilən kolleksiyalarını və daha mürəkkəb quruluşları saxlamaq üçün istifadə olunur. Primitiv tipləri daha yaxşı öyrəndikdən sonra obyektlər mövzusuna <info:object> fəslində toxunacağıq.

`symbol` tipi obyektlər üçün unikal identifikatorlar yaratmaqda istifadə olunur. Onu burada tamlıq üçün qeyd edirik, lakin obyektləri öyrəndikdən sonra bu mövzuya qayıdacağıq.

### `typeof` operatoru [#type-typeof]

`typeof` operatoru arqumentin tipini qaytarır. Fərqli tipləri müxtəlif üsullarla işləmək lazım olduqda və ya sadəcə sürətli bir yoxlama aparmaq istədikdə çox faydalıdır.

Bu operator iki sintaksisi dəstəkləyir:

1. Operator kimi: `typeof x`.
2. Funksiya kimi: `typeof(x)`.

Başqa sözlə, mötərizələrlə və ya mötərizəsiz istifadə edilə bilər. Hər iki halda nəticə eyni olur.

`typeof x` ifadəsi arqumentin tipini `string` formatında qaytarır:

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

1. `Math` riyazi əməliyyatlar təqdim edən daxili obyektlərdən biridir. Biz onu <info:number> fəsilində daha ətraflı öyrənəcəyik. Burada isə, sadəcə obyektin bir nümunəsi kimi istifadə olunub.
2. `typeof null` nəticəsi `"object"` olaraq qaytarılır. Bu, səhvdir. Bu, `typeof` operatorunun rəsmi olaraq tanınmış bir xətasıdır və uyğunluq səbəbilə saxlanılıb. Əslində, `null` bir obyekt deyil. O, ayrıca bir tipə malik xüsusi bir dəyərdir. Beləliklə, bu, JavaScript dilində mövcud olan bir qüsurdur.
3. `typeof alert` nəticəsi `"function"` olur, çünki, `alert` bir funksiyadır. Biz funksiyaları növbəti fəsillərdə öyrənəcəyik. Orada görəcəyik ki, əslində JavaScript-də xüsusi bir "function" tipi yoxdur. Funksiyalar `object` tipinə daxildir. Lakin, `typeof` funksiyalara fərqli davranaraq `"function"` kimi qaytarır. Bu tam doğru deyil, lakin praktikada çox rahatdır.

## Xülasə

JavaScript-də 8 sadə verilən tipi mövcuddur:

- **`number`**: İstənilən növ rəqəmlər üçün, tam və ya onluq kəsr dəyərləri daxildir. Tam ədədlər ±2<sup>53</sup> həddində məhdudlaşdırılıb.
- **`bigint`**: İxtiyari uzunluqlu tam ədədlər üçündür.
- **`string`**: "mətn" tipidir. Bir `string` bir və ya daha çox simvolu ehtiva edə bilər. Tək simvol üçün ayrıca bir tip mövcud deyil.
- **`boolean`**: `true` və `false` məntiqi dəyərləri üçün istifadə olunur.
- **`null`**: Naməlum dəyərlər üçün nəzərdə tutulmuş ayrıca bir tipdir, yalnız `null` dəyərinə sahibdir.
- **`undefined`**: Mənimsədilməmiş dəyərlər üçün ayrıca bir tipdir, yalnız `undefined` dəyərinə sahibdir.
- **`object`**: Daha mürəkkəb verilən strukturlarını saxlamaq üçün istifadə olunur.
- **`symbol`**: Unikal identifikatorlar yaratmaq üçün istifadə olunur.

`typeof` dəyişənin tipini müəyyənləşdirməyə imkan verir:

- İki sintaksis mövcuddur: `typeof x` və ya `typeof(x)`.
- `string` olaraq tipin adını qaytarır, məsələn, `"string"`.
- `null` dəyəri üçün `"object"` qaytarır -- bu, dilin daxilində olan bir səhvdir. Əslində, `null` bir obyekt deyil.

Növbəti fəsillərdə, əvvəlcə ibtidai (primitive) dəyərləri öyrənəcəyik və onlarla tanış olduqdan sonra obyektlərə keçəcəyik.