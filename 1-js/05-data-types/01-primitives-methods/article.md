# Primitivlərin üsulları

JavaScript bizə primitivlərlə (sətirlər, rəqəmlər və s.) obyekt kimi işləməyə imkan verir. Onlar həmçinin çağırmaq üçün üsullar təqdim edirlər. Biz tezliklə bunları öyrənəcəyik, amma əvvəlcə gılin  bunun necə işlədiyini görək, çünki təbii ki, primitivlər obyekt deyillər (və burada bunu  biz daha da aydınlaşdıracağıq).

Primitivlər və obyektlər arasındakı əsas fərqlərə baxaq.

Bir primitiv

- Primitiv tipli bir dəyərdir.
- 7 primitiv tip var: `string`, `number`, `bigint`, `boolean`, `symbol`, `null` və `undefined`.

Bir obyekt

- Çoxsaylı dəyərləri xassələr kimi saxlamağı bacarır.
- `{}` ilə yaradıla bilir, məsələn: `{ad: "John", yaş: 30}`. JavaScript-də başqa növ obyektlər də var: məs. funksiyalarda  obyektlərdir.

Obyektlərlə bağlı ən yaxşı cəhətlərdən biri funksiyanı onun xassələrindən biri kimi saxlaya bilməyimizdir.

```js run
let john = {
  name: "John",
  sayHi: function() {
    alert("Salam buddy!");
  }
};

john.sayHi(); // Salam buddy!
```

Beləliklə, burada 'sayHi' metodu ilə 'john' obyekti yaratdıq.

Bir çox daxili obyektlər onsuzda mövcuddur, məsələn, tarixlər, xətalar, HTML elementləri və s. ilə işləyənlər. Onların müxtəlif xassələri və metodları var.

Ancaq bu xüsusiyyətlər bir xərclə gəlir!

Obyektlər primitivlərdən "ağırdır". Onlar daxili mexanizmləri dəstəkləmək üçün əlavə resurslar tələb edirlər.

Obyekt kimi bir primitiv

JavaScript yaradıcısının üzləşdiyi paradoks budur:

- String və ya rəqəm kimi primitivlərlə etmək istəyəcəyiniz bir çox şey var. Onlara metod kimi daxil olmaq əla olardı.
- Primitivlər mümkün qədər sürətli və yüngül olmalıdır.

Həll bir az qəribə  görünsədə, aşağıdakı kimidir:

1. Primitivlər hələ də primitivdir. İstədinildiyi  kimi tək bir dəyər.
2. Dil stringlərin, ədədlərin, booleanların və simvolların üsullarına və xassələrinə giriş imkanı verir.
3. Bunun işləməsi üçün əlavə funksionallığı təmin edən xüsusi "obyekt sarğı" yaradılır və sonra məhv edilir.

"Obyekt sarğıları" hər bir primitiv tip üçün fərqlidir və  `String`, `Number`, `Boolean` və `Symbol` olaraq adlandırılır. Beləliklə, onlar müxtəlif üsullar setini təmin edirlər.

Məsələn, [str.toUpperCase()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase) sətir metodu mövcuddur ki, bu da böyük hərflə yazılmış `str` qaytarır.

Bu necə işləyir:

```js run
let str = "Salam";

alert( str.toUpperCase() ); // Salam
```

Sadə, elə deyilmi? `str.toUpperCase()`-də  nə baş verir:

1. `str` stringi primitivdir. Beləliklə, onun xassəsinə daxil oln an sətrin dəyərini bilən və `toUpperCase()` kimi faydalı metodlara malik xüsusi obyekt yaradılır.
2. Bu üsul çalışır və yeni sətir qaytarır (`xəbərdarlıq` ilə göstərilir).
3. Primitiv `str` tək qalır və  xüsusi obyekt məhv edilir.

Beləliklə, primitivlər bəzi üsullar təmin etsə də, yenə də yüngül qalırlar.

JavaScript mühərriki bu prosesi yüksək dərəcədə optimallaşdırır. O, hətta əlavə obyektin yaradılmasını ümumiyyətlə atlaya bilər. Ancaq yenə də spesifikasiyaya riayət etməli və sanki onu yaradır kimi davranmalıdır.

Nömrənin özünəməxsus üsulları var, məsələn, [toFixed(n)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed) rəqəmi yuvarlaqlaşdırır verilmiş dəqiqlik:

```js run
let n = 1.23456;

alert( n.toFixed(2) ); // 1.23
```

Biz daha spesifik üsulları <info:number> və <info:string> fəsillərində görəcəyik.


````warn header="Konstruktorlar `String/Number/Boolean` yalnız daxili istifadə üçündür"
Java kimi bəzi dillər bizə `yeni Nömrə(1)` və ya `yeni Boolean(yanlış)` kimi sintaksisdən istifadə edərək primitivlər üçün açıq şəkildə "sarğı obyektləri" yaratmağa imkan verir.

JavaScript-də bu, tarixi səbəblərə görə də mümkündür, lakin çox **tövsiyə olunmur**. Bir neçə yerdə işlər çılğınlaşacaq.

Məsələn:

```js run
alert( typeof 0 ); // "nömrə"

alert( typeof new Number(0) ); // "obyekt"!
```

Obyektlər `if`-də həmişə doğrudur, ona görə də burada alert görünəcək:

```js run
let zero = new Number(0);

if (zero) { // sıfır doğrudur, çünki o, obyektdir
  alert( "sıfır doğrudur!?!" );
}
```

Digər tərəfdən, eyni `String/Number/Boolean` funksiyalarından `yeni` olmadan istifadə etmək tamamilə sağlam və faydalı bir şeydir. Onlar dəyəri müvafiq tipə çevirir: string, nömrə və ya booleana (ibtidai).

Məsələn, bu tamamilə etibarlıdır:
```js
let num = Number("123"); //stringi nömrəyə çevirin
```
````


````xəbərdarlıq başlığı="null/undefined heç bir metodu yoxdur"
`null` və `undefined` xüsusi primitivləri istisnadır. Onların müvafiq "sarğı obyektləri" yoxdur və heç bir üsul təqdim etmir. Onlar müəyyən mənada “ən primitivdirlər”.

Belə bir dəyərə malik bir xüsusiyyətə daxil olmaq cəhdi aşağıdakı xətanı verəcəkdir:

```js run
alert(null.test); // error
````

## Xülasə

- `null` və `undefined` istisna olmaqla primitivlər bir çox faydalı metodlar təmin edir. Gələcək fəsillərdə bunları öyrənəcəyik.
- Formal olaraq, bu üsullar müvəqqəti obyektlər vasitəsilə işləyir, lakin JavaScript mühərrikləri bunu daxili optimallaşdırmaq üçün yaxşı ayarlanıb, ona görə də onları çağırmaq  baha başa gəlmir.
