# Kod Strukturu

Biz ilk olaraq kod bloklarını yaratmağı öyrənəcəyik.

## İfadələr

İfadələr fəaliyyəti əks etdirən sintaksis quruluşları və əmrlərdir.

Biz artıq "Salam, dünya!" ismarıcını göstərən `alert('Salam, dünya!')` ifadəsi ilə tanışıq.

Biz kodumuzda istədiyimiz qədər ifadələri əlavə edə bilirik. İfadələr öz növbəsində nöqtəli vergül ilə ayrıla bilərlər.

Məsələn, burada biz "Salam Dünya"-nı iki xəbərdarlığa bölürük:

```js run no-beautify
alert('Salam'); alert('Dünya');
```

Adətən kodu daha rahat oxunabilən etmək üçün ifadələr ayrı sətirdə yazılır:

```js run no-beautify
alert('Salam');
alert('Dünya');
```

## Nöqtəli vergül [#semicolon]

Sətir bittiyi halda nöqtəli vergül buraxıla bilər.

Bu həmçinin işləyir:

```js run no-beautify
alert('Salam')
alert('Dünya')
```

Burada, JavaScript-də sətir kəsilməsi "gizli" nöqtəli vergülü bildirir. Bu [avtomatik nöqtəli vergül əlavəsi](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion) adlanır.

**Əksər hallarda yeni sətir nöqtəli vergülü bildirir. Ancaq "əksər hallar" " həmişəni" bildirmir!**

Bəzi hallarda yeni sətir nöqtəli vergülü bildirmir. Məsələn:

```js run no-beautify
alert(3 +
1
+ 2);
```

Burada JavaScript nöqtəli vergülü daxil etmədiyi üçün kod `6` nəticəsini göstərir. İntuitiv şəkildə aydındır ki, əgər sətir müsbət `"+"` ilə bitərsə, deməli bu "natamam ifadədir". Beləliklə, nöqtəli vergülə ehtiyac duyulmur və bu halda nəzərdə tutulduğu kimi işləyir.

**Ancaq bəzi hallarda JavaScript nöqtəli vergülün harada lazım olmasını "uğursuz" şəkildə fərz edir.**

Belə hallarda baş verən xətaları tapmaq və düzəltmək çətindir.

````smart header="An example of an error"
Əgər siz belə xətanı göstərən spesifik misalı görmək istəyirsinizsə, bu koda nəzər salın:

```js run
[1, 2].forEach(alert)
```

Hələki mötərizəsi `[]` və `forEach` haqqında düşünməyə dəyməz. Biz onları sonra öyrənəcəyik. İndiki vəziyyət üçün sadəcə kodun nəticəsini yadda saxlayın: ilk öncə `1`-i və daha sonra `2`-ni göstərir.

İndi isə gəlin koddan öncə `alert`- i əlavə edək və nöqtəli vergül ilə *bitirməyək*:

```js run no-beautify
alert("TBurada xəta olacaqdır")

[1, 2].forEach(alert)
```

Əgər indi biz kodu işə salsaq, ilk `alert` göstərilir və sonra bizdə xəta baş verir!

Amma  əgər biz `alert`-dən sonra nöqtəli vergül əlavə etsək hər şey qaydasına düşəcək:
```js run
alert("Hər şey qaydasındadır");

[1, 2].forEach(alert)  
```

İndi bizim "Hər şey qaydasındadır" ismarıcımız var və ondan sonra`1` və `2`gəlir.


JavaScript `[...]` düz mötərizədən öncə nöqtəli vergülün gəldiyini fərz etmədiyi üçün qeyri-nöqtəli vergül versiyasında xəta baş verir.

Beləliklə, nöqtəli vergül avtomatik daxil edilmədiyi üçün birinci nümunədəki kodu tək ifadə kimi qəbul edir. Javscript mexanizmi bunu belə görür:

```js run no-beautify
alert("Burada xəta olacaqdır")[1, 2].forEach(alert)
```

Anacq bu bir yox, iki ayrı ifadə olmalıdır. Bu halda belə bir birləşdirmə səhvdir və buna görə də xəta baş verir. Bu xəta digər situasiyalarda da baş verə bilər. 
````

Hətta yeni sətir ilə ayırılsa belə, biz ifadələr arasında nöqtəli vergülləri daxil etməyi məsləhət görürük. Bu qayda geniş şəkildə icma tərəfindən tədbiq olunur. Gəlin bir daha qeyd edək ki, *çox zaman nöqtəli vergülü buraxmaq mümkündür*. Ancaq xüsusilə kodlaşdırmaya yeni başlayanlar üçün nöqtəli vergülü istifadə etmək məsləhətdir.

## Şəhrlər [#code-comments]

Zaman keçdikcə proqramlar daha çox mürəkkəbləşir. Buna görə də kodun nə etdiyi və səbəbini izah edən *şəhrləri* əlavə etmək vacibdir.

Şəhrlər skriptin istənilən yerində istifadə oluna bilər. Mexanizm şəhrlərə əhəmiyyət vermədiyi üçün şəhrlər skriptin icrasına təsir etmirlər.

**Bir sətirli şəhrlər iki sləş (çəpinə xətt) `//` işarəsi ilə başlayır.**

Sətirin qalan hissəsi şəhrdir. Şəhrlər ayrıca sətirdə qeyd oluna və ya ifadənin davamı ilə qeyd oluna bilər.The rest of the line is a comment. It may occupy a full line of its own or follow a statement.

Məsələn:
```js run
// Bu şəhr ayrı bir sətrdə qeyd olunub
alert('Hello');

alert('World'); // Bu şəhr ifadənin davamı ilə qyd olunub
```

**Çoxsətirli şəhrlər sləş və ulduz işarələri <code>/&#42;</code> ilə başlayır və ulduz və sləş simvolları ilə <code>&#42;/</code> bitirlər.**

Məsələn:

```js run
/* İki ismarıclı nümunə.
Bu çoxsətirli şəhrdir.
*/
alert('Salam');
alert('Dünya');
```

Şəhrlərdəki məzmun nəzərə alınmır, beləliklə əgər biz kodu <code>/&#42; ... &#42;/</code> daxilinə qoysaq kod icra olunmayacaq.

Bəzən kodun bir hissəsini belə üsullar ləğv etmək yaxşı üsuldur:

```js run
/* Kodu şəhr kimi qeyd etmək
alert('Salam');
*/
alert('Dünya');
```

```smart header="Use hotkeys!"
Əksər redaktə proqramlarında  təksətirli şəhrlər kimi qeyd etmək üçün `key:Ctrl+/` qaynarklavişləri və ya çoxsətirli şəhrlərdə `key:Ctrl+Shift+/` qaynar klavişləri basmaqla kod sətrini şəhrə keçirmək mümkündür. Mac istifadə etdikde isə  `key:Ctrl` yerinə `key:Cmd` qaynar klavişləri basın.
```

````warn header="Bir-birinin daxilində şəhrlər yaratmaq dəstəklənmir!"
`/*...*/`-nin daxilində digər bir `/*...*/` ola bilməz.

Belə kod xəta gğstərərək "öləcəkdir":

```js run no-beautify
/*
  /* bir-birnin daxilində şəhrlər ?!? */
*/
alert( 'World' );
```
````

Zəhmət olmasa öz kodunuzu şəhr etməyə çəkinməyin.

Şəhrlər kodda izləri çoxaltsa da bu problem deyil. İstehsal serverinə dərc etdərkən kodun yığcamlaşdırılması üçün müxtəlif alətlər mövcuddur. Onlar şəhrləri aradan qaldırır, beləliklə şəhrlər iş skriptində qarşınıza çıxmır. Buna görə də, şəhrlərin məhsula heç bir mənfi təsiri yoxdur. 

Sonra dərslikdə daha yaxşı şəhrlər yazmağı izah edən <info:code-quality>  bölməsi olacaqdır.
