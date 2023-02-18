# Brauzer mühiti, texniki xüsusiyyətlər

JavaScript dili əvvəlcə veb brauzerlər üçün yaradılmışdır. O vaxtdan bəri inkişaf etdi və bir çox istifadəsi və platforması olan bir dilə çevrildi.

Platforma brauzer, veb-server və ya başqa bir *host*, hətta qəhvə maşını ola bilər. Onların hər biri platformaya xas funksiyaları təmin edir. JavaScript spesifikasiyası bunu *host mühiti* adlandırır.

Host mühiti dil nüvəsinə əlavə olaraq öz obyektlərini və funksiyalarını təmin edir. Veb brauzerləri veb səhifələrini idarə etmək üçün bir vasitədir. Node.js server tərəfi xüsusiyyətlərini  və s. təmin edir.

JavaScript veb-brauzerdə işlədiyi zaman əldə etdiyimiz şeyə quşbaxışı nəzər salaq:

![](windowObjects.svg)

"window" adında bir "root" obyekt var. Onun iki rolu vardır:

1. Birincisi, bu fəsildə təsvir olunduğu kimi JavaScript kodu üçün qlobal obyektdir <info:global-object>.
2. İkincisi, o, "brauzer pəncərəsini" təmsil edir və onu idarə etmək üçün üsullar təqdim edir.

Məsələn, biz onu qlobal obyekt olaraq aşağıdakı kimi  istifadə edirik:

```js run
function sayHi() {
  alert("Salam");
}

// global functions are methods of the global object:
window.sayHi();
```

Və burada pəncərənin hündürlüyünü görmək üçün onu brauzer pəncərəsi kimi istifadə edirik:

```js run
alert(window.innerHeight); // inner window height
```

Pəncərəyə(window) xas olan daha çox üsul və xüsusiyyətlər var, biz onları daha sonra nəzərdən keçirəcəyik.

## DOM (Document Object Model)

Sənəd Obyekt Modeli və ya qısaca SOM, özünü bütün səhifə məzmununu dəyişdirə bilən obyektlər kimi təmsil edir.

`document` obyekti səhifənin əsas "giriş nöqtəsidir". Bundan istifadə edərək səhifədə hər hansı bir şeyi dəyişdirə və yaxudda yeni bir şey yarada bilərik.

Məsələn:
```js run
// arxa fon rəngini qırmızıya çevir
document.body.style.background = "red";

// 1 saniyədən sonra onu yenidən dəyişdir
setTimeout(() => document.body.style.background = "", 1000);
```

Burada biz `document.body.style`, istifadə etdik, lakin daha çox şey var. Xüsusiyyətlər və üsullar spesifikasiyada təsvir edilmişdir:

- **DOM yaşayış standartı** at <https://dom.spec.whatwg.org>

```smart header="DOM is not only for browsers"
DOM spesifikasiyası sənədin strukturunu izah edir və onu idarə etmək üçün obyektlər təqdim edir. DOM-dan istifadə  edən və brauzer olmayan alətlər də var.

Məsələn, HTML səhifələrini yükləyən və onları emal edən server tərəfi skriptləri də DOM-dan istifadə edə bilər. Onlar spesifikasiyanın yalnız bir hissəsini dəstəkləyə bilər.
```

```smart header="CSSOM for styling"
CSS qaydaları və üslub cədvəlləri HTML-dən fərqli bir şəkildə qurulmuşdur. Ayrı bir spesifikasiya var, [CSS Object Model (CSSOM)](https://www.w3.org/TR/cssom-1/), bu, onların obyekt kimi necə təmsil olunduğunu və necə oxunub yazılacağını izah edir.

Sənəd üçün üslub qaydalarına dəyişiklik etdikdə CSSOM DOM ilə birlikdə istifadə olunur. Təcrübədə CSSOM nadir hallarda tələb olunur, çünki adətən CSS qaydaları statik olur. Bizə nadir hallarda JavaScript-dən CSS qaydalarını əlavə etmək/çıxarmaq lazımdır, lakin bu da mümkündür.
```

## BOM (Browser Object Model)

Brauzer Obyekt Modeli (BOM) sənəddən başqa hər şeylə işləmək üçün brauzer (host mühiti) tərəfindən təmin edilən əlavə obyektləri təmsil edir.

Məsələn:

- [navigator](mdn:api/Window/navigator) obyekti brauzer və əməliyyat sistemi haqqında məlumat verir. Bir çox xüsusiyyəti var, lakin ən çox tanınan iki xüsusiyyəti bunlardır: `navigator.userAgent` -- cari brauzer haqqında və `navigator.platform` -- platforma haqqında (Windows/Linux/Mac və s. arasında fərq qoymağa kömək edə bilər).
- [location](mdn:api/Window/location) obyekti bizə cari URL-ni oxumağa imkan verə və brauzeri yenisinə yönləndirə bilər.

`location` obyektindən necə istifadə edə bilərik:

```js run
alert(location.href); // cari URL-ni göstərir
if (confirm("Go to Wikipedia?")) {
  location.href = "https://wikipedia.org"; // brauzeri başqa URL-ə yönləndir
}
```

`alert/confirm/prompt` funksiyaları da BOM-un bir hissəsidir: onlar birbaşa sənədlə əlaqəli deyil, lakin istifadəçi ilə ünsiyyət qurmağın təmiz brauzer üsullarını təmsil edirlər.

```smart header="Specifications"
BOM ümumi [HTML specification](https://html.spec.whatwg.org)-in bir hissəsidir.

Bəli, düz eşitdiniz. <https://html.spec.whatwg.org> ünvanındakı HTML spesifikasiyası təkcə "HTML dili" (teqlər, atributlar) haqqında deyil, həm də bir sıra obyektləri, metodları və brauzerə məxsus DOM uzantılarını əhatə edir. Bu, "geniş mənada HTML"dir. Həmçinin, bəzi hissələrin <https://spec.whatwg.org> ünvanında sadalanan əlavə xüsusiyyətləri də vardır.
```

## Xülasə olaraq

Standartlar haqqında danışarkən bizdə:

DOM spesifikasiyası
: Sənəd strukturunu, manipulyasiyaları və hadisələri təsvir edir, bura baxa bilərsiniz <https://dom.spec.whatwg.org>.

CSSOM spesifikasiyası
: Üslub cədvəllərini və üslub qaydalarını, onlarla manipulyasiyaları və onların sənədlərə bind olmasını təsvir edir, bura baxa bilərsiniz <https://www.w3.org/TR/cssom-1/>.

HTML spesifikasiyası
: HTML dilini (məsələn, teqlər) və həmçinin BOM (brauzer obyekt modeli) -- müxtəlif brauzer funksiyalarını təsvir edir: `setTimeout`, `alert`, `location` və s., baxın <https://html.spec.whatwg .org>. DOM spesifikasiyasını götürür və onu bir çox əlavə xüsusiyyətlər və üsullarla genişləndirir.


Bundan əlavə, bəzi dərslər <https://spec.whatwg.org/> saytında ayrıca təsvir edilmişdir.

Zəhmət olmasa bu linklərə diqqət yetirin, çünki öyrənmək üçün o qədər şey var ki, hər şeyi əhatə etmək və yadda saxlamaq mümkün deyil.

Özəllik və ya metod haqqında oxumaq istədiyiniz zaman, <https://developer.mozilla.org/en-US/search>-da Mozilla təlimatı da gözəl mənbədir, lakin müvafiq spesifikasiya daha yaxşı ola bilər: o, daha mürəkkəb və oxunması daha uzun müddətdir, lakin fundamental biliklərinizi sağlamlaşdıracaq və tamamlayacaq.

Nəyisə tapmaq üçün "WHATWG [term]" və ya "MDN [term]" internet axtarışından istifadə etmək çox vaxt rahatdır, məsələn, <https://google.com?q=whatwg+localstorage>, <https://google. com?q=mdn+localstorage>.

İndi DOM-u öyrənməyə başlayacağıq, çünki DOM UI-də çox əsas bir  rol oynayır.
