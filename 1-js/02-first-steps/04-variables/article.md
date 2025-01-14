# Dəyişənlər

Çox vaxt JavaScript tətbiqləri məlumatlarla işləməlidir. Məsələn:
1. Onlayn mağaza -- məlumatlar satılan məhsulları və alış-veriş səbətini əhatə edə bilər.
2. Çat tətbiqi -- məlumatlar istifadəçiləri, mesajları və daha çoxunu ehtiva edə bilər.

Dəyişənlər bu məlumatları saxlamaq üçün istifadə olunur.

## Dəyişən

[Dəyişən (variable)](https://en.wikipedia.org/wiki/Variable_(computer_science)), məlumatlar üçün "adlandırılmış yaddaş" yeridir. Biz dəyişənlərdən məhsulları, ziyarətçiləri və digər məlumatları yadda saxlamaq üçün istifadə edə bilərik.

JavaScript-də dəyişən yaratmaq üçün `let` açar sözündən istifadə edin.

Aşağıdakı ifadə "message" adlı bir dəyişən yaradır (başqa sözlə "elan edir"):

```js
let message;
```

İndi biz mənimsətmə operatorundan (`=`) istifadə edərək bu dəyişənə bəzi məlumatlar yerləşdirə bilərik:

```js
let message;

*!*
message = 'Salam'; // Mətni saxla
*/!*
```

İndi, mətn dəyəri dəyişənə bağlı olan yaddaş sahəsində saxlanılır. Biz, dəyişənin adından istifadə edərək bu dəyəri oxuya bilərik:

```js run
let message;
message = 'Salam!';

*!*
alert(message); // dəyişənin kontentini göstər
*/!*
```

Yığcam kod yazmaq üçün biz dəyişənin yaranmasını və təyinatını bir sətirdə birləşdirə bilərik:

```js run
let message = 'Salam!'; // Dəyişəni müəyyənləşdir və dəyəri təyin et

alert(message); // Salam!
```

Biz, həmçinin bir neçə dəyişəni eyni sətirdə müəyyənləşdirə bilərik:

```js no-beautify
let user = 'Orxan', age = 25, message = 'Salam';
```

Bunun daha qısa olmasına baxmayaraq biz belə kod yazmağı tövsiyə etmirik. Oxunaqlığı çoxaltmaq üçün hər dəyişən üçün ayrı sətir istifadə edin.

Çox sətirli variantın bir az uzun olmasına baxmayaraq bunu oxumaq daha asandır:

```js
let user = 'Orxan';
let age = 25;
let message = 'Salam';
```

Bəzi proqramçılar bir neçə dəyişəni aşağıdakı formada:
```js no-beautify
let user = 'Orxan',
  age = 25,
  message = 'Salam';
```

...və ya "vergül-birinci" stilində də müəyyənləşdirirlər:

```js no-beautify
let user = 'Orxan'
  , age = 25
  , message = 'Salam';
```

Texniki olaraq yuxarıdakı bütün variantlar eyni nəticəni verəcək. Bu səbəbdən, burada vacib olan proqramçıların şəxsi zövqüdür.


````smart header="`let` əvəzinə `var`"
Siz, köhnə skriptlərdə `let` əvəzinə `var` açar sözünün işlədildiyini görə bilərsiniz:

```js
*!*var*/!* message = 'Salam';
```

`var` açar sözü `let` açar sözü ilə *demək olar ki* eynidir. O da dəyişən elan edir, lakin bir qədər fərqli, "köhnə üsulla".

`let` və `var` arasında olan hiss edilməyən fərqlər var. Lakin, indi bu fərqlər bizi maralandırmır. Biz, bu fərqlər haqqında <info:var> bölməsində detallı danışacağıq.
````

## Real dünyada analogiya

Dəyişən anlayışını asanlıqla qavraya bilərik, əgər onu üzərində unikal ad yazılmış bir "etiket" olan məlumatlar üçün bir "qutu" kimi təsəvvür etsək.

Məsələn, `message` dəyişəni daxilində "Salam!" dəyəri olan və `"message"` adı ilə etiketlənən qutudur:

![](variable.svg)

Biz qutuda istənilən dəyəri yerləşdirə bilərik.

Əlavə olaraq, biz bu dəyəri istədiyimiz qədər dəyişə bilərik:
```js run
let message;

message = 'Salam!';

message = 'Dünya!'; // dəyər dəyişdi

alert(message);
```

Dəyər dəyişdikdə dəyişəndə olan köhnə məlumat silinir:

![](variable-change.svg)

Biz həmçinin iki dəyişən elan edib, məlumatı birindən digərinə köçürə bilərik.

```js run
let hello = 'Salam dünya!';

let message;

*!*
// 'Salam dünya' dəyərini hello dəyişənindən message dəyişəninə kopyala
message = hello;
*/!*

// indi, hər iki dəyişəndə eyni dəyər saxlanılır
alert(hello); // Salam dünya!
alert(message); // Salam dünya!
```

```smart header="Funksional dillər"
Nəzərinizə çatdırmaq istəyirik ki, [Scala](http://www.scala-lang.org/) və [Erlang](http://www.erlang.org/) kimi [funksional](https://en.wikipedia.org/wiki/Functional_programming) proqramlaşdırma dillərində dəyişənin dəyişilməsinə icazə verilmir.

Belə dillərdə, dəyər "qutunun içinə" bir dəfə yerləşdirildikdən sonra, o, orada əbədi qalır. Əgər başqa bir şey saxlamağımız lazım olarsa, dil bizi yeni bir qutu (yeni dəyişən elan etməyi) yaratmağa məcbur edir. Köhnəsini yenidən istifadə edə bilmirik.

İlk baxışda bunun bir az qəribə olmasına baxmayaraq bu dillərdə çox ciddi təkmilləşdirmə etmək mümkündür. Bundan əlavə, paralel hesablamalar kimi bəzi tapşırıqlarda bu məhdudiyyətin olmasının faydası var. Fikrinizi genişləndirmək üçün bu formalı dili öyrənməyi (hətta bunu istifadə etməyi planlaşdırmasanız belə) tövsiyə edirik.
```

## Dəyişənlərin adlandırılması [#variable-naming]

JavaScript-də dəyişənlərin adlandırılmasında iki məhdudiyyət var:

1. Dəyişən adında yalnız hərflər, rəqəmlər və ya `$` və `_` kimi simvollar ola bilər.
2. Dəyişən adının ilk hərfi rəqəm ola bilməz.

Etibarlı adlar üçün nümunələr:

```js
let userName;
let test123;
```

Dəyişən adı bir neçə sözdən ibarət olduqda çox zaman [camelCase](https://en.wikipedia.org/wiki/CamelCase) formatından istifadə olunur. Bu formatında ilk sözdən başqa bütün sözlər böyük hərf ilə başlayır: `myVeryLongName`.

Dəyişən adlarında dollar (`'$'`), altdan xətt (`'_'`) simvollarının da istifadə edilə bilməsi maraqlıdır. Bu simvollar, hərflər kimi xüsusi mənası olmayan sadə simvollardır.

Aşağıdakı adlar keçərlidir:

```js run untrusted
let $ = 1; // "$" adlı dəyişən təyin et
let _ = 2; // "_" adlı dəyişən təyin et

alert($ + _); // 3
```

Yanlış dəyişən adlarına nümunələr:

```js no-beautify
let 1a; // dəyişən adı rəqəm ilə başlaya bilməz

let my-name; // dəyişən adında '-' kimi simvollar ola bilməz
```

```smart header="Böyük-kiçik hərflər fərq yaradır"
`apple` və `AppLE` adları fərqli dəyişənlərə istinad edir.
```

````smart header="Qeyri-latin hərflər istifadə etmək mümkündür, lakin tövsiyə edilmir"
Hər hansı bir dildən, o cümlədən kiril hərflərindən və hətta heroqliflərdən istifadə etmək mümkündür, məsələn:

```js
let имя = '...';
let 我 = '...';
```

Texniki olaraq, burada heç bir səhv yoxdur, belə adlar uyğundur, lakin dəyişən adlarında ingilis dilindən istifadə etmək beynəlxalq bir ənənədir. Hətta kiçik bir skript yazsaq belə, onun uzun bir ömrü ola bilər. Başqa ölkələrdən olan insanlar bir gün onu oxumağa ehtiyac duya bilərlər.
````

````warn header="Qorunan adlar"
JavaScript dilində istifadə edilən bəzi [qorunan sözləri](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords) dəyişən adı kimi istifadə etmək olmaz.

Məsələn: `let`, `class`, `return` və `function` sözləri qorunur.

Aşağıdakı kodda sintaksis xətası baş verəcək:

```js run no-beautify
let let = 5; // xəta! "let" adlı dəyişən istifadə etmək olmaz!
let return = 5; // xəta! "return" adlı dəyişən istifadə etmək olmaz!
```
````

````warn header="`use strict`-siz təyinat"

Adətən, dəyişəni istifadə etməzdən əvvəl elan etməliyik. Lakin keçmişdə, sadəcə dəyəri təyin etməklə `let` istifadə etmədən də dəyişən yaratmaq texniki olaraq mümkün idi. Bu, hələ də köhnə skriptlərlə uyğunluğu qorumaq üçün skriptlərimizdə `use strict` istifadə etmədiyimiz təqdirdə mümkündür.

```js run no-strict
// qeyd: bu nümunədə "use strict" direktivi istifadə edilmir

num = 5; // "num" dəyişəni olmadıqda dəyişən yaranacaq

alert(num); // 5
```

Bu pis bir praktika hesab olunur və sıx rejimdə xətaya səbəb olacaq:

```js
"use strict";

*!*
num = 5; // xəta: num təyin edilməyib
*/!*
```
````

## Sabit dəyişənlər

Sabit (dəyişməyən) dəyişən yaratmaq istəyirsinizsə, `let` əvəzinə `const` istifadə edin:

```js
const myBirthday = '18.04.1982';
```

`const` istifadə edilərək elan edilmiş dəyişənlər "konstantlar/sabit dəyişənlər" adlanır. Onlar yenidən təyin edilə bilməz. Bunu etməyə cəhd edilsə, xəta yaranacaq:

```js run
const myBirthday = '18.04.1982';

myBirthday = '01.01.2001'; // xəta, sabit dəyişəni dəyişmək olmaz!
```

Proqramçı bir dəyişənin heç vaxt dəyişməyəcəyinə əmin olduqda, bunu `const` ilə elan edə bilər ki, bunu təmin etsin və hər kəsə açıq şəkildə bildirsin.


### Böyük hərf ilə yazılmış sabit dəyişənlər

İcra edilmədən əvvəl məlum olan və yadda saxlamaq çətin olan dəyərlər üçün sabit dəyişənlərdən ləqəb (alias) kimi istifadə etmək geniş yayılmış bir praktikadır.

Bu formalı sabit dəyişənlər böyük hərf və altdan xətt ilə adlandırılırlar.

Məsələn, gəlin "veb" (16-lı rəqəm) formatında olan rənglər üçün sabit dəyişənlər yaradaq:

```js run
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...rəngdən istifadə etdikdə
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```

Faydaları:

- `COLOR_ORANGE` dəyəri yadda saxlamaq `"#FF7F00"` dəyərini yadda saxlamaqdan daha asandır.
- `"#FF7F00"` dəyərində səhv etmək `COLOR_ORANGE` dəyərində səhv etməkdən daha asandır.
- Kodu oxuduqda `COLOR_ORANGE` dəyərinin mənası `#FF7F00` dəyərinin mənasından daha çoxdur.

Sabit dəyişənləri nə zaman normal formada, nə zaman isə böyük hərflər ilə yazmaq lazımdır? Gəlin bunun açıqlamasını verək.

Dəyişənin "sabit" olması, bu dəyişənin heç vaxt dəyişməməsi deməkdir. Lakin, bəzi sabit dəyişənlər skript icra olunmamışdan öncə (qırmızı rəngin 16-lıq rəqəmi kimi) , bəziləri isə icra zamanı *hesablanır* və sabit qalır.

Məsələn:
```js
const pageLoadTime = /* veb səhifənin yüklənməsinə xərclənən zaman */;
```

`pageLoadTime` dəyəri səhifə yüklənməmişdən öncə bilinmədiyindən bu, normal adlandırılır. Lakin, bu dəyər təyin edildikdən sonra dəyişmədiyindən sabit qalır.

Digər sözlə, böyük hərf ilə yazılan sabit dəyişənləri yalnız "əl ilə" yazılan dəyərlər üçün istifadə edin. 

## Dəyişənləri düzgün adlandırın

Dəyişənləri adlandırdıqda çox vacib məqam var.

Dəyişən adı, saxladığı məlumatı təsvir edən, aydın və konkret bir mənaya sahib olmalıdır.

Dəyişənləri adlandırmaq proqramlaşdırmada çox vacib və mürəkkəb bacarıqlardan biridir. Dəyişən adlarına tez bir nəzər salmaqla, kodun başlanğıc səviyyəli bir proqramçı tərəfindən yoxsa təcrübəli bir proqramçı tərəfindən yazıldığını müəyyən etmək mümkündür.

Real bir layihədə, vaxtın böyük hissəsi sıfırdan tamamilə ayrı bir şey yazmaqdan daha çox mövcud kod bazasını dəyişdirmək və genişləndirməyə sərf olunur. Bir müddət başqa bir işlə məşğul olduqdan sonra koda qayıtdığımızda, yaxşı işarələnmiş məlumatları tapmaq daha asan olur. Başqa sözlə, dəyişənlər yaxşı adlara sahib olduqda bu daha rahat olur.

Dəyişəni müəyyənləşdirməmişdən öncə yaxşı ad haqqında bir az fikirləşin. Bunu etdikdə faydasını görəcəksiniz.

Bəzi əməl edə biləcəyiniz yaxşı qaydalar:

- `userName` və ya `shoppingCart` kimi insanların başa düşə biləcəyi adlardan istifadə edin.
- Qısaldılmış adlardan və ya `a`, `b`, `c` kimi adlardan uzaq durun.
- Adları maksimal dərəcədə təsvirli və dəqiq edin. `data` və `value` kimi adlar pisdir. Bu adlar nəyin baş verdiyi haqqda heç nə təsvir etmir. Əgər kodun konteksti dəyişənin hansı məlumat və ya dəyərə istinad etdiyini göstərirsə, belə adlardan istifadə etmək olar.
- Komandanızda və beyninizdə terminlər haqqında razılığıa gəlin. Əgər sayt ziyatətçisi "user" adlanırsa, buna aid dəyişənləri `currentVisitor` və ya `newManInTown` adlandırmaq əvəzinə `currentUser` və ya `newUser` adlandırın.

Sadə görünür? Bunun sadə görünməyinə baxmayaraq praktikada təsvirli və dəqiq dəyişən adları düzəltmək çətindir.

```smart header="Yenidən istifadə et yoxsa yarat?"
Son olaraq, bəzi tənbəl proqramçılar, yeni dəyişənlər elan etmək əvəzinə, mövcud dəyişənləri yenidən istifadə etməyə meyillidirlər.

Nəticədə, bu dəyişənlər etiketi dəyişməyən, amma daxili dəyişən qutulara bənzəyirlər. Qutunun içində nəyin olduğunu heç kim bilmir. Bu səbəbdən, biz bu kodlara yaxından baxıb yoxlamalıyıq.

Bu proqramçılar dəyişən yaratmaqda az vaxt, amma debaq zamanı on dəfə çox vaxt xərcləyirlər.

Yeni dəyişən yaratmaq pis deyil.

Müasir JavaScript minifikasiya alətləri və brauzerlər kodu kifayət qədər yaxşı optimallaşdırır, buna görə performans problemləri yaratmayacaq. Fərqli dəyərlər üçün fərqli dəyişənlərdən istifadə etmək hətta mühərrikin kodunuzu daha yaxşı optimallaşdırmasına kömək edə bilər.
```

## Xülasə

Dəyişənləri  `var`, `let` və ya `const` açar sözləri ilə yaratmaq mümkündür.

- `let` — müasir dəyişən elanıdır.  
- `var` — köhnə üsulla dəyişən elanıdır. Adətən, ondan ümumiyyətlə istifadə etmirik, lakin <info:var> <info:var> bölməsində `let` və `var` arasında olan fərqlərdən danışacağıq.
- `const` — `let` kimidir, amma dəyişənin dəyəri dəyişdirilə bilməz.

Dəyişənlər elə adlandırılmalıdır ki, onların içində nə olduğunu asanlıqla anlaya bilək.
