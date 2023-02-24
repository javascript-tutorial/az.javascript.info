kitabxanalar:
  - d3
  - dom ağacı

---

# DOM ağacı

HTML sənədinin əsasını teqlər təşkil edir.

Sənəd Obyekt Modelinə (DOM) görə, hər bir HTML etiketi bir obyektdir. İçəridə yerləşdirilmiş teqlər əlavənin "uşaqlarıdır". Teqin içindəki mətn də bir obyektdir.

Bütün bu obyektlərə JavaScript istifadə etməklə daxil olmaq mümkündür və biz onlardan səhifəni dəyişdirmək üçün istifadə edə bilərik.

Məsələn, `document.body`   `<body>` teqini təmsil edən obyektdir.

Bu kodu işlətdikdə `<body>` 3 saniyə qırmızı olacaq:

```js run
document.body.style.background = 'red'; // arxafonu qırmızı et

setTimeout(() => document.body.style.background = '', 3000); // geri qayıt
```

Burada `document.body` fonunun rəngini dəyişmək üçün `style.background`dan istifadə etdik, lakin bir çox başqa xüsusiyyətlər də var, məs:

- `innerHTML` -- Node-nin HTML məzmunu.
- `offsetWidth` -- node-nin eni (piksellə)
- ...və s.

Tezliklə biz DOM ilə manipulyasiya etməyin daha çox yollarını öyrənəcəyik, lakin əvvəlcə onun strukturu haqqında bilməliyik.

## DOM nümunəsi

Aşağıdakı sadə sənədlə başlayaq:

```html run no-beautify
<!DOCTYPE HTML>
<html>
<head>
  <title>Maral haqqında</title>
</head>
<body>
  Maral haqqında həqiqət.
</body>
</html>
```

DOM HTML-i teqlərin ağac strukturu kimi təmsil edir. Aşağıdakı kimi  görünür:

<div class="domtree"></div>

<script>
let node1 = {"name":"HTML","nodeType":1,"children":[{"name":"HEAD","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"\n    "},{"name":"TITLE","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"Maral haqqında"}]},{"name":"#text","nodeType":3,"content":"\n  "}]},{"name":"#text","nodeType":3,"content":"\n  "},{"name":"BODY","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"\n  Maral haqqında həqiqət."}]}]}

drawHtmlTree(node1, 'div.domtree', 690, 320);
</script>

```online
Yuxarıdakı şəkildə siz element node-larına klikləsəniz onların  açılıb-dağılmasını görə bilərsiniz.
```

Hər bir ağac qovşağı bir obyektdir.

Teqlər *element qovşaqlarıdır* (və ya sadəcə elementlərdir) və onlar ağac strukturunu təşkil edir: `<html>`  root-dur  `<head>` və `<body>` onun uşaqlarıdır və s.

Elementlərin daxilindəki mətn `#text` kimi etiketlənmiş *mətn qovşaqlarını* əmələ gətirir. Mətn qovşağı yalnız bir stringdən ibarətdir.  Onun uşaqları olmaya bilər və o həmişə ağacın bir yarpağıdır.

Məsələn, `<title>` teqində `"Maral haqqında"` mətin var.

Zəhmət olmasa mətn qovşaqlarında xüsusi simvollara diqqət yetirin:

- a newline: `↵` (in JavaScript known as `\n`)
- a space: `␣`

Boşluqlar və yeni sətirlər hərflər və rəqəmlər kimi tamamilə geçərli simvollardır. Onlar mətn qovşaqlarını meydana gətirir və DOM-un bir hissəsi olurlar. Beləliklə, məsələn, yuxarıdakı misalda `<head>` teqində `<title>`-dən əvvəl bəzi boşluqları əhatə edir və həmin mətn bir `#text` qovşağına çevrilir (yeni sətir və yalnız bəzi boşluqları ehtiva edir).

Yalnız iki yuxarı-səviyyəli istisnalar var:
1. `<head>`-dən əvvəlki boşluqlar və yeni sətirlər tarixi səbəblərə görə nəzərə alınmır.
2. Əgər biz `</body>`-dən sonra nəsə qoysaq, o zaman o, avtomatik olaraq sonunda `body` daxilində köçürülür, çünki HTML spesifikasiyası bütün məzmunun `<body>` daxilində olmasını tələb edir. Beləliklə, `</body>`-dən sonra boşluq ola bilməz.

Digər hallarda hər şey sadədir -- sənəddə boşluqlar varsa (hər hansı simvol kimi), onlar DOM-da mətn qovşaqlarına çevrilirlər və əgər biz onları silsək, onların heç biri olmayacaq.

Aşağıda  boşluq olan mətn qovşaqları yoxdur:

```html no-beautify
<!DOCTYPE HTML>
<html><head><title>Maral haqqında</title></head><body>Maral haqqında həqiqət</body></html>
```

<div class="domtree"></div>

<script>
let node2 = {"name":"HTML","nodeType":1,"children":[{"name":"HEAD","nodeType":1,"children":[{"name":"TITLE","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"Maral haqqında"}]}]},{"name":"BODY","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"Maral haqqında həqiqət."}]}]}

drawHtmlTree(node2, 'div.domtree', 690, 210);
</script>

```smart header="Spaces at string start/end and space-only text nodes are usually hidden in tools"
DOM ilə işləyən brauzer alətləri (tezliklə əhatə olunacaq) adətən mətnin əvvəlində/sonunda boşluq və teqlər arasında boş mətn qovşaqlarını (sətir fasilələri) göstərmir.

Developer alətləri bu yolla ekran sahəsinə qənaət edir.

Əlavə DOM şəkillərində biz bəzən əhəmiyyətsiz olduqda onları buraxacağıq. Belə boşluqlar adətən documentin necə göstərilməsinə təsir etmir.
```

## Avotmatik düzəltmə

Brauzer səhv formalaşdırılmış HTML ilə qarşılaşarsa,  DOM-u hazırlayarkən həmin səhvi avtomatik olaraq düzəldir.

Məsələn, üst teq həmişə `<html>`-dir. Documentdə olmasa belə, DOM-da mövcud olacaq, çünki brauzer onu yaradacaq. Eyni şey `<body>` üçün də keçərlidir.

Nümunə olaraq, əgər HTML faylı tək `"Salam"` sözüdürsə, brauzer onu `<html>` və `<body>` -nin içinə daxil edəcək və tələb olunan `<head>` -də əlavə edəcək və DOM aşağıdakı kimi olacaq:


<div class="domtree"></div>

<script>
let node3 = {"name":"HTML","nodeType":1,"children":[{"name":"HEAD","nodeType":1,"children":[]},{"name":"BODY","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"Hello"}]}]}

drawHtmlTree(node3, 'div.domtree', 690, 150);
</script>

DOM yaradarkən, brauzerlər avtomatik olaraq documentdəki səhvləri emal edir, təgləri bağlayır və s.

Bağlanmamış təgləri olan sənəd:

```html no-beautify
<p>Hello
<li>Mom
<li>and
<li>Dad
```

...brauzer teqləri oxuduqca və çatışmayan hissələri bərpa etdikcə normal DOM-a çevriləcək:

<div class="domtree"></div>

<script>
let node4 = {"name":"HTML","nodeType":1,"children":[{"name":"HEAD","nodeType":1,"children":[]},{"name":"BODY","nodeType":1,"children":[{"name":"P","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"Hello"}]},{"name":"LI","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"Mom"}]},{"name":"LI","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"and"}]},{"name":"LI","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"Dad"}]}]}]}

drawHtmlTree(node4, 'div.domtree', 690, 360);
</script>

```` warn header="Cədvəllərdə həmişə `<tbody>` var"
Maraqlı bir "xüsusi hal" cədvəllərdir. DOM spesifikasiyasına görə onlar `<tbody>` olmalıdır, lakin HTML mətni (rəsmi olaraq) onu buraxa bilər. Sonra brauzer avtomatik olaraq DOM-da `<tbody>` yaradır.

HTML üçün:

```html no-beautify
<table id="table"><tr><td>1</td></tr></table>
```

DOM strukturu belə olacaq:
<div class="domtree"></div>

<script>
let node5 = {"name":"TABLE","nodeType":1,"children":[{"name":"TBODY","nodeType":1,"children":[{"name":"TR","nodeType":1,"children":[{"name":"TD","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"1"}]}]}]}]};

drawHtmlTree(node5,  'div.domtree', 600, 200);
</script>

Gördünüz? `<tbody>` anidən ortaya çıxdı. Sürprizlərin qarşısını almaq üçün cədvəllərlə işləyərkən bunu nəzərə almalısınız.
````

## Digər data tipləri

Elementlər və mətn qovşaqlarından başqa bəzi digər qovşaq növləri də var.

Məsələn, commentlər:

```html
<!DOCTYPE HTML>
<html>
<body>
  The truth about elk.
  <ol>
    <li>An elk is a smart</li>
*!*
    <!-- comment -->
*/!*
    <li>...and cunning animal!</li>
  </ol>
</body>
</html>
```

<div class="domtree"></div>

<script>
let node6 = {"name":"HTML","nodeType":1,"children":[{"name":"HEAD","nodeType":1,"children":[]},{"name":"BODY","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"\n  Maral haqqında həqiqət.\n    "},{"name":"OL","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"\n      "},{"name":"LI","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"Maral ağıllıdır"}]},{"name":"#text","nodeType":3,"content":"\n      "},{"name":"#comment","nodeType":8,"content":"comment"},{"name":"#text","nodeType":3,"content":"\n      "},{"name":"LI","nodeType":1,"children":[{"name":"#text","nodeType":3,"content":"...və hiyləgər heyvan!"}]},{"name":"#text","nodeType":3,"content":"\n    "}]},{"name":"#text","nodeType":3,"content":"\n  \n"}]}]};

drawHtmlTree(node6, 'div.domtree', 690, 500);
</script>

Biz burada iki mətn qovşağı arasında `#comment` kimi etiketlənmiş yeni ağac qovşağı növünü görə bilərik -- *comment node*.

Düşünə bilərik ki, niyə DOM-a şərh əlavə olunur? Vizual təmsilə heç bir şəkildə təsir göstərmir.  Qayda belədir -- HTML-də bir şey varsa, o mütləq  DOM ağacında olmalıdır.

**HTML-dəki hər şey, hətta şərhlər də DOM-un bir hissəsinə çevrilir.**

Hətta HTML-nin ən əvvəlindəki `<!DOCTYPE...>` direktivi də DOM qovşağıdır. O, DOM ağacında `<html>`-dən düz əvvəldir. Biz o düyünə toxunmuruq, hətta bu səbəbdən onu diaqramlara da çəkmirik, amma o, yenə də oradadır.

Bütün documenti təmsil edən “document” obyekti də rəsmi olaraq DOM qovşağıdır.

[12 qovşaq növü](https://dom.spec.whatwg.org/#node) var. Praktikada biz adətən onlardan 4-ü ilə işləyirik:

1. `document` -- DOM-a "giriş nöqtəsi".
2. element qovşaqları -- HTML etiketləri, ağac build blokları.
3. mətn qovşaqları -- mətni əhatələyir.
4. şərhlər -- bəzən biz ora məlumat yerləşdirə bilirik, ama onlar göstərilmir, amma JS onu DOM-dan oxuya bilir.

## Özünüz baxın

DOM strukturunu real vaxt rejimində görmək üçün [Live DOM Viewer](http://software.hixie.ch/utilities/js/live-dom-viewer/) cəhd edin. Sadəcə sənədi daxil edin və o, dərhal DOM kimi görünəcək.

DOM-u araşdırmağın başqa bir yolu brauzerin tools-larından istifadə etməkdir. Əslində, tərtib edərkən istifadə etdiyimiz şey budur.

Bunu etmək üçün, [elk.html](elk.html) veb səhifəsini açın, brauzerin tools-larını yandırın və Elementlər tabına keçin.

Bu belə görünməlidir:

![](elk.svg)

Siz DOM-u görə bilərsiniz, elementlərə klikləyin, onların təfərrüatlarına baxın və s.

Nəzərə alın ki, toolslarda DOM strukturu sadələşdirilmişdir. Mətn qovşaqları mətn kimi göstərilir. Və ümumiyyətlə "inspect" (yalnız boşluq) mətn qovşaqları yoxdur. Biz çox vaxt element qovşaqları ilə maraqlandığımız üçün bu belə yaxşıdır.

Yuxarı sol küncdəki <span class="devtools" style="background-position:-328px -124px"></span> düyməsinə klikləməklə, siçan (və ya digər göstərici cihazları) vasitəsilə veb-səhifədən qovşağı seçə bilərik. ) və onu "yoxlayın" (Elementlər tabında ona sürüşdürün). Nəhəng HTML səhifəmiz (və müvafiq nəhəng DOM) olduqda və orada müəyyən elementin yerini görmək istədikdə bu əla işləyir.

Bunu etmək üçün başqa bir yol isə veb-səhifəyə sağ klikləmək və kontekst menyusunda "Inspect" seçməkdir.

![](inspect.svg)

Alətlərin sağ hissəsində aşağıdakı alt nişanlar var:
- **Styles** -- biz CSS-nin daxili qaydalar (boz) daxil olmaqla, cari element qaydasına tətbiq edildiyini görə bilərik. Aşağıdakı qutunun ölçüləri/kənarları/doldurmaları da daxil olmaqla, demək olar ki, hər şey yerində redaktə edilə bilər.
- **Computed** -- elementə xassə üzrə tətbiq edilən CSS-i görmək üçün: hər bir xüsusiyyət üçün biz onu verən bir qayda görə bilərik (o cümlədən CSS mirası və sair).
- **Event Listeners** -- DOM elementlərinə əlavə edilmiş event listenersləri görmək üçün (biz onları təlimatın növbəti hissəsində danşacağıq).
- ...və s.

Onları öyrənməyin ən yaxşı yolu klikləməkdir. Əksər dəyərlər yerində redaktə edilə bilər.

## Konsolla qarşılıqlı əlaqə

DOM ilə işləyərkən biz də ona JavaScript tətbiq etmək istəyə bilərik. Bunun kimi: bir node alın və onu dəyişdirmək, nəticəni görmək üçün bir neçə kod işlədin. Elementlər tabı və konsol arasında səyahət etmək üçün bir neçə məsləhət

Başlanğıc üçün:

1. Elementlər tabında ilk `<li>` seçin.
2. `key: Esc` düyməsini basın -- o, Elementlər tabının altındakı konsolu açacaq.

İndi sonuncu seçilmiş element `$0` kimi mövcuddur, əvvəl seçilmiş `$1` və s.

Biz onlara əmrlər verə bilərik. Məsələn, `$0.style.background = 'red'' seçilmiş siyahı elementini qırmızı edir, məsələn:

![](domconsole0.svg)

Konsolda Elements-dən bir qovşaq əldə etmək belədir.

Bir də geriyə yol var. Əgər DOM qovşağına istinad edən dəyişən varsa, onu Elementlər panelində görmək üçün Konsolda `inspect(node)` əmrindən istifadə edə bilərik.

Və ya biz sadəcə konsolda DOM qovşağını çıxara və aşağıda "document.body" kimi "yerində" araşdıra bilərik:

![](domconsole1.svg)

Bu, əlbəttə ki, sazlama məqsədləri üçün. Növbəti fəsildən biz JavaScript istifadə edərək DOM-a daxil olacağıq və dəyişdirəcəyik.

Brauzer toolsları tərtibatda böyük köməkdir: biz DOM-u tədqiq edə, hər şeyi sınaya və nəyin səhv olduğunu görə bilərik.

## Nəhayət olaraq

HTML/XML documenti brauzer daxilində DOM ağacı kimi təqdim olunur.

- Teqlər element qovşaqlarına çevrilir və strukturu təşkil edir.
- Mətn mətn qovşaqlarına çevrilir.
- ...və s., HTML-də hər şeyin DOM-da öz yeri var, hətta şərhlərin də.

DOM-u yoxlamaq və onu əl ilə dəyişdirmək üçün toolslardan istifadə edə bilərik.

Burada əsasən, ən çox istifadə olunan və başlamaq üçün mühüm olan aksiyonları əhatə etdik. <https://developers.google.com/web/tools/chrome-devtools> ünvanında Chrome Developer Tools haqqında geniş sənədləşmə var. Alətləri öyrənməyin ən yaxşı yolu ora-bura klikləmək, menyuları oxumaqdır: seçimlərin çoxu göz qabağındadır. Daha sonra, ümumiyyətlə, onları tanıdığınız zaman sənədləri oxuyun və qalanını götürün.

DOM qovşaqlarının xassələri və üsulları var ki, onlar arasında səyahət etmək, onları dəyişdirmək, səhifədə hərəkət etmək və s. olur. Növbəti fəsillərdə onlara toxunacağıq.
