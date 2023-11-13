# Brauzer mühiti, texniki xüsusiyyətlər

<<<<<<< HEAD
JavaScript dili əvvəlcə veb brauzerlər üçün yaradılmışdır. O vaxtdan bəri inkişaf etdi və bir çox istifadəsi və platforması olan bir dilə çevrildi.

Platforma brauzer, veb-server və ya başqa bir *host*, hətta qəhvə maşını ola bilər. Onların hər biri platformaya xas funksiyaları təmin edir. JavaScript spesifikasiyası bunu *host mühiti* adlandırır.

Host mühiti dil nüvəsinə əlavə olaraq öz obyektlərini və funksiyalarını təmin edir. Veb brauzerləri veb səhifələrini idarə etmək üçün bir vasitədir. Node.js server tərəfi xüsusiyyətlərini  və s. təmin edir.

JavaScript veb-brauzerdə işlədiyi zaman əldə etdiyimiz şeyə quşbaxışı nəzər salaq:
=======
The JavaScript language was initially created for web browsers. Since then, it has evolved into a language with many uses and platforms.

A platform may be a browser, or a web-server or another *host*, or even a "smart" coffee machine if it can run JavaScript. Each of these provides platform-specific functionality. The JavaScript specification calls that a *host environment*.

A host environment provides its own objects and functions in addition to the language core. Web browsers give a means to control web pages. Node.js provides server-side features, and so on.

Here's a bird's-eye view of what we have when JavaScript runs in a web browser:
>>>>>>> 285083fc71ee3a7cf55fd8acac9c91ac6f62105c

![](windowObjects.svg)

"window" adında bir "root" obyekt var. Onun iki rolu vardır:

1. Birincisi, bu fəsildə təsvir olunduğu kimi JavaScript kodu üçün qlobal obyektdir <info:global-object>.
2. İkincisi, o, "brauzer pəncərəsini" təmsil edir və onu idarə etmək üçün üsullar təqdim edir.

<<<<<<< HEAD
Məsələn, biz onu qlobal obyekt olaraq aşağıdakı kimi  istifadə edirik:
=======
For instance, we can use it as a global object:
>>>>>>> 285083fc71ee3a7cf55fd8acac9c91ac6f62105c

```js run global
function sayHi() {
  alert("Salam");
}

// global functions are methods of the global object:
window.sayHi();
```

<<<<<<< HEAD
Və burada pəncərənin hündürlüyünü görmək üçün onu brauzer pəncərəsi kimi istifadə edirik:
=======
And we can use it as a browser window, to show the window height:
>>>>>>> 285083fc71ee3a7cf55fd8acac9c91ac6f62105c

```js run
alert(window.innerHeight); // inner window height
```

<<<<<<< HEAD
Pəncərəyə(window) xas olan daha çox üsul və xüsusiyyətlər var, biz onları daha sonra nəzərdən keçirəcəyik.

## DOM (Document Object Model)

Sənəd Obyekt Modeli və ya qısaca SOM, özünü bütün səhifə məzmununu dəyişdirə bilən obyektlər kimi təmsil edir.
=======
There are more window-specific methods and properties, which we'll cover later.

## DOM (Document Object Model)

The Document Object Model, or DOM for short, represents all page content as objects that can be modified.
>>>>>>> 285083fc71ee3a7cf55fd8acac9c91ac6f62105c

`document` obyekti səhifənin əsas "giriş nöqtəsidir". Bundan istifadə edərək səhifədə hər hansı bir şeyi dəyişdirə və yaxudda yeni bir şey yarada bilərik.

Məsələn:
```js run
// arxa fon rəngini qırmızıya çevir
document.body.style.background = "red";

// 1 saniyədən sonra onu yenidən dəyişdir
setTimeout(() => document.body.style.background = "", 1000);
```

<<<<<<< HEAD
Burada biz `document.body.style`, istifadə etdik, lakin daha çox şey var. Xüsusiyyətlər və üsullar spesifikasiyada təsvir edilmişdir:

- **DOM yaşayış standartı** at <https://dom.spec.whatwg.org>
=======
Here, we used `document.body.style`, but there's much, much more. Properties and methods are described in the specification: [DOM Living Standard](https://dom.spec.whatwg.org).
>>>>>>> 285083fc71ee3a7cf55fd8acac9c91ac6f62105c

```smart header="DOM is not only for browsers"
DOM spesifikasiyası sənədin strukturunu izah edir və onu idarə etmək üçün obyektlər təqdim edir. DOM-dan istifadə  edən və brauzer olmayan alətlər də var.

<<<<<<< HEAD
Məsələn, HTML səhifələrini yükləyən və onları emal edən server tərəfi skriptləri də DOM-dan istifadə edə bilər. Onlar spesifikasiyanın yalnız bir hissəsini dəstəkləyə bilər.
```

```smart header="CSSOM for styling"
CSS qaydaları və üslub cədvəlləri HTML-dən fərqli bir şəkildə qurulmuşdur. Ayrı bir spesifikasiya var, [CSS Object Model (CSSOM)](https://www.w3.org/TR/cssom-1/), bu, onların obyekt kimi necə təmsil olunduğunu və necə oxunub yazılacağını izah edir.

Sənəd üçün üslub qaydalarına dəyişiklik etdikdə CSSOM DOM ilə birlikdə istifadə olunur. Təcrübədə CSSOM nadir hallarda tələb olunur, çünki adətən CSS qaydaları statik olur. Bizə nadir hallarda JavaScript-dən CSS qaydalarını əlavə etmək/çıxarmaq lazımdır, lakin bu da mümkündür.
=======
For instance, server-side scripts that download HTML pages and process them can also use the DOM. They may support only a part of the specification though.
```

```smart header="CSSOM for styling"
There's also a separate specification, [CSS Object Model (CSSOM)](https://www.w3.org/TR/cssom-1/) for CSS rules and stylesheets, that explains how they are represented as objects, and how to read and write them.

The CSSOM is used together with the DOM when we modify style rules for the document. In practice though, the CSSOM is rarely required, because we rarely need to modify CSS rules from JavaScript (usually we just add/remove CSS classes, not modify their CSS rules), but that's also possible.
>>>>>>> 285083fc71ee3a7cf55fd8acac9c91ac6f62105c
```

## BOM (Browser Object Model)

Brauzer Obyekt Modeli (BOM) sənəddən başqa hər şeylə işləmək üçün brauzer (host mühiti) tərəfindən təmin edilən əlavə obyektləri təmsil edir.

Məsələn:

<<<<<<< HEAD
- [navigator](mdn:api/Window/navigator) obyekti brauzer və əməliyyat sistemi haqqında məlumat verir. Bir çox xüsusiyyəti var, lakin ən çox tanınan iki xüsusiyyəti bunlardır: `navigator.userAgent` -- cari brauzer haqqında və `navigator.platform` -- platforma haqqında (Windows/Linux/Mac və s. arasında fərq qoymağa kömək edə bilər).
- [location](mdn:api/Window/location) obyekti bizə cari URL-ni oxumağa imkan verə və brauzeri yenisinə yönləndirə bilər.
=======
- The [navigator](mdn:api/Window/navigator) object provides background information about the browser and the operating system. There are many properties, but the two most widely known are: `navigator.userAgent` -- about the current browser, and `navigator.platform` -- about the platform (can help to differentiate between Windows/Linux/Mac etc).
- The [location](mdn:api/Window/location) object allows us to read the current URL and can redirect the browser to a new one.
>>>>>>> 285083fc71ee3a7cf55fd8acac9c91ac6f62105c

`location` obyektindən necə istifadə edə bilərik:

```js run
alert(location.href); // cari URL-ni göstərir
if (confirm("Go to Wikipedia?")) {
  location.href = "https://wikipedia.org"; // brauzeri başqa URL-ə yönləndir
}
```

<<<<<<< HEAD
`alert/confirm/prompt` funksiyaları da BOM-un bir hissəsidir: onlar birbaşa sənədlə əlaqəli deyil, lakin istifadəçi ilə ünsiyyət qurmağın təmiz brauzer üsullarını təmsil edirlər.

```smart header="Specifications"
BOM ümumi [HTML specification](https://html.spec.whatwg.org)-in bir hissəsidir.

Bəli, düz eşitdiniz. <https://html.spec.whatwg.org> ünvanındakı HTML spesifikasiyası təkcə "HTML dili" (teqlər, atributlar) haqqında deyil, həm də bir sıra obyektləri, metodları və brauzerə məxsus DOM uzantılarını əhatə edir. Bu, "geniş mənada HTML"dir. Həmçinin, bəzi hissələrin <https://spec.whatwg.org> ünvanında sadalanan əlavə xüsusiyyətləri də vardır.
=======
The functions `alert/confirm/prompt` are also a part of the BOM: they are not directly related to the document, but represent pure browser methods for communicating with the user.

```smart header="Specifications"
The BOM is a part of the general [HTML specification](https://html.spec.whatwg.org).

Yes, you heard that right. The HTML spec at <https://html.spec.whatwg.org> is not only about the "HTML language" (tags, attributes), but also covers a bunch of objects, methods, and browser-specific DOM extensions. That's "HTML in broad terms". Also, some parts have additional specs listed at <https://spec.whatwg.org>.
>>>>>>> 285083fc71ee3a7cf55fd8acac9c91ac6f62105c
```

## Xülasə olaraq

Standartlar haqqında danışarkən bizdə:

<<<<<<< HEAD
DOM spesifikasiyası
: Sənəd strukturunu, manipulyasiyaları və hadisələri təsvir edir, bura baxa bilərsiniz <https://dom.spec.whatwg.org>.

CSSOM spesifikasiyası
: Üslub cədvəllərini və üslub qaydalarını, onlarla manipulyasiyaları və onların sənədlərə bind olmasını təsvir edir, bura baxa bilərsiniz <https://www.w3.org/TR/cssom-1/>.
=======
DOM specification
: Describes the document structure, manipulations, and events, see <https://dom.spec.whatwg.org>.

CSSOM specification
: Describes stylesheets and style rules, manipulations with them, and their binding to documents, see <https://www.w3.org/TR/cssom-1/>.
>>>>>>> 285083fc71ee3a7cf55fd8acac9c91ac6f62105c

HTML spesifikasiyası
: HTML dilini (məsələn, teqlər) və həmçinin BOM (brauzer obyekt modeli) -- müxtəlif brauzer funksiyalarını təsvir edir: `setTimeout`, `alert`, `location` və s., baxın <https://html.spec.whatwg .org>. DOM spesifikasiyasını götürür və onu bir çox əlavə xüsusiyyətlər və üsullarla genişləndirir.


<<<<<<< HEAD
Bundan əlavə, bəzi dərslər <https://spec.whatwg.org/> saytında ayrıca təsvir edilmişdir.

Zəhmət olmasa bu linklərə diqqət yetirin, çünki öyrənmək üçün o qədər şey var ki, hər şeyi əhatə etmək və yadda saxlamaq mümkün deyil.
=======
Please note these links, as there's so much to learn that it's impossible to cover everything and remember it all.

When you'd like to read about a property or a method, the Mozilla manual at <https://developer.mozilla.org/en-US/> is also a nice resource, but the corresponding spec may be better: it's more complex and longer to read, but will make your fundamental knowledge sound and complete.
>>>>>>> 285083fc71ee3a7cf55fd8acac9c91ac6f62105c

Özəllik və ya metod haqqında oxumaq istədiyiniz zaman, <https://developer.mozilla.org/en-US/search>-da Mozilla təlimatı da gözəl mənbədir, lakin müvafiq spesifikasiya daha yaxşı ola bilər: o, daha mürəkkəb və oxunması daha uzun müddətdir, lakin fundamental biliklərinizi sağlamlaşdıracaq və tamamlayacaq.

<<<<<<< HEAD
Nəyisə tapmaq üçün "WHATWG [term]" və ya "MDN [term]" internet axtarışından istifadə etmək çox vaxt rahatdır, məsələn, <https://google.com?q=whatwg+localstorage>, <https://google. com?q=mdn+localstorage>.

İndi DOM-u öyrənməyə başlayacağıq, çünki DOM UI-də çox əsas bir  rol oynayır.
=======
Now, we'll get down to learning the DOM, because the document plays the central role in the UI.
>>>>>>> 285083fc71ee3a7cf55fd8acac9c91ac6f62105c
