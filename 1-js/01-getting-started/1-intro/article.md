# JavaScript-ə giriş

Gəlin JavaScript-in niyə belə xüsusi olduğuna, onunla nələr edə biləcəyimizə və onun hansı texnologiyalarla qaynayıb qarışdığına bir nəzər yetirək.

## JavaScript nədir?

_JavaScript_ ilkin olaraq _"web səhifələri canlandırmaq"_ üçün yaradılmışdır.

Bu dilə yazılmış proqramlar _skriptlər_ adlandırılır. Bu skriptlər, birbaşa web səhifənin HTML-inin içərisində yazıla və səhifə yükləndikcə icra oluna bilər.

Skriptlər əvvəlcədən heç bir hazırlıq, kompilyasiya və s. mərhələlərə ehtiyac olmadan, adi mətn şəklində yazıla və təqdim edilə bilər.

Bu baxımdan, JavaScript, [Java](<https://en.wikipedia.org/wiki/Java_(programming_language)>) adlandırılan, lakin çox vaxt onunla qarışıq salınan dildən olduqca fərqlidir.

```smart header="Bəs onda niyə <u>Java</u>Script?"

JavaScript yaradılan vaxtlarda, ilkin olaraq "LiveScript" adlandırılmışdır. Lakin sonradan Java-nın məhşurluğu və digər səbəblərdən dolayı onu Java-nın "kiçik qardaşı" kimi qələmə vermək qərara alınmışdı.

Buna baxamayaraq sonradan JavaScript öz spesifikasiyaları olan ([ECMAScript](http://en.wikipedia.org/wiki/ECMAScript)), tamamilə müstəqil bir dilə çevrildi və artıq Java ilə uzaqdan yaxından heç bir əlaqəsi yoxdur.

```

Günümüzdə isə, JavaScript tək brauzer mühitində deyil, serverdə və [JavaScript mühərriki](https://en.wikipedia.org/wiki/JavaScript_engine) olan istənilən bir qurğuda işləyir.

Brauzerin daxilində "JavaScript virtual maşını" adlı bir mühərrik mövcuddur.

Müxtəlif mühərriklərin müxtəlif kodadları var. Misalçün:

- [V8](<https://en.wikipedia.org/wiki/V8_(JavaScript_engine)>) -- Chrome və Operada.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- in Firefoxda.
- [Chakra](<https://en.wikipedia.org/wiki/Chakra_(JScript_engine)>) -- Microsoft Edgedə
- [JavaScriptCore](https://en.wikipedia.org/wiki/WebKit#JavaScriptCore) -- Safaridə (WebKit) və s.

Yuxarıdakı terminləri yadda saxlamağınız tövsiyyə olunur çünki, bu cür terminlər developer məqalələrində çox istifadə olunur. Nümunə üçün onu deyə bilərik ki, kimsə sizə "filan xüsusiyyət V8-də dəstəklənir" deyəndə, o dəqiqə biləcəksiniz ki, Chrome və Opera (bir də gördünüz MS Edge) bu xüsusiyyəti dəstəkləyir.

```smart header="Bəs bu mühərriklər necə işləyir?"

Düzünü desək, bu mühərriklər olduqca mürəkkəbdir lakin əsaslar sadədir:

1. Əvvəlcə skript oxunulur, token-lərə ayrılır və parse edilir
2. Yaradılmış token-lərdən [AST](https://en.wikipedia.org/wiki/Abstract_syntax_tree) qurulur
3. Həmin tree-dən [bytecode](https://en.wikipedia.org/wiki/Bytecode) generasiya olunur
4. Bytecode isə maşın koduna çevrilərək icra olunur

Təbii ki, mühərrikin işi bununla bitmir. Hər bir mərhələdə müəyyən optimallaşdırmalar aparılır və skriptlər icra olunduqca optimallaşdırma üçün məlumatlar toplanılır. Bunun vasitəsilə daha süərtli maşın kodları generasiya olunur.
```

## JavaScript brauzer mühitində nələrə qadirdir?

Müasir JavaScript olduqca təhlükəsiz proqramlaşdırma dilidir. O, ilkin olaraq sadəcə brauzer mühitində işləmək üçün yaradıldığı üçün yaddaşa və ya CPU-ya birbaşa müdaxilə imkanı vermir.

Lakin JavaScript-in imkanları onun icra olunduğu mühitdən asılı olaraq dəyişir. Misalçün, [Node.js](https://wikipedia.org/wiki/Node.js) ilə JavaScript faylları oxuya/yaza, şəbəkə sorğuları və s. edə bilər.

Brauzer daxilində isə, JavaScript web səhifə ilə bağlı demək olar ki, hər şeyi edə bilir.

Bunlara misal olaraq:

- SƏhifəyə yeni HTML-in əlavə edilməsi və hazırkı kontentin dəyişdirilməsi.
- Mouse klik, key press və s. kimi istifadəçi tərəfindən tətiklənən eventlərə reaksiya vermək.
- Şəbəkə üzərindən sorğular göndərmək, fayllar endirmək, upload etmək ( [AJAX](<https://en.wikipedia.org/wiki/Ajax_(programming)>) və [COMET](<https://en.wikipedia.org/wiki/Comet_(programming)>) texnologiyaları vasitəsilə).
- Cookie-lərlə işəmək, ziyarətçilərə müxtəlif mesajlar göstərmək və ya suallar vermək.
- İstifadəçi tərəfdə (client-side) məlumatlar saxlamaq və s.

Və digər şeyləri göstərmək olar.

## Bəs JavaScript brauzer daxilində nələri EDƏ BİLMİR?

İstifadəçinin təhlükəsizliyini təmin etmək üçün, JavaScript-in brauzerdəki funksionallıqları limitlidir.

Bu cür limitlərə aşağıdakılar daxildir:

- Hər hansı bir web səhifədəki JavaScript sizin sərt diskinizdəki ixtiyari faylları yarada, silə, dəyişə və ya icra edə bilməz. Onun sizin əməliyyat sisteminin funksiyalarına bir başa çıxışı yoxdur.

<<<<<<< HEAD
  Müasir brauzerlər fayllarla işləməyə imkan yaradır lakin bu əməliyyat `<input>` etiketi vasitəsilə sayta fayl yükləməkdən başqa bir şeyə imkan yaratmır.
=======
- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS functions.
>>>>>>> fcfef6a07842ed56144e04a80c3a24de049a952a

  Bununla bərarbər, brauzer sizə kamera və mikrofon kimi cihazlarlə işləmək imkanı yaradır lakin bu əməliyyatları istifadəçinin bir başa icazəsi olmadan etmək qeyri-mümkündür. Yəni evdə hər hansı bir işlə məşğul olanda kimsə sizi hansısa web səhifədən izləyə bilməz, bunun üçün siz brauzerə icazə verməlisiniz.

- Fərqli pəncərələr və tablar normalda bir-biri haqqında heç nə bilmirlər. Əgər, siz JavaScript-i istifadə edərək, başqa bir pəncərə açsanız, bu halda açdığınız pəncərə və cari pəncərə fərqli mənbələrdəndirsə (fərqli domen adı, fərqli protokol və ya port) bir pəncərənin digər pəncərəyə heç bir çıxışı yoxdur.

  Bu eyni mənbə siyasəti adlandırılır (Same Origin Policy). Yalnız hər iki səhifə müəyyən protokol üzərindən razılaşdığı halda bir-birinin resurslarından istifadə edə bilərlər.

  Digər mahdudlaşdırmalar kimi, bu da istifadəçinin güvənliyi üçündür. Hər hansı `http://qeyrimüəyyənbirsayt.com` saytı digər pəncərədə açılmış `http://gmail.com` saytından məlumat götürə bilməməlidir. Əks halda halımız yaxşı olmaz.

![](limitations.svg)

Bu cür məhdudiyyətlər sadəcə brauzer daxilində mövcuddur, daha öncə də qeyd etdiyimiz kimi JavaScript-in imkanları mühitə görə dəyişir.

## JavaScript-i unikal edən nədir?

Aşağıdakılar, JavaScript-i unikal edən ən az üç şeydir:

```compare
+ HTML/CSS ilə tam inteqrasiya.
+ Sadə şeylər sadəliklə icra olunur.
+ Əksər brauzerlər tərəfindən dəstəklənir və defolt olaraq aktivdir.
```

Bu üç xüsusiyyəti özündə birləşdirən yegənə texnologiya JavaScript-dir.

Məhz bu səbəbdən, JavaScript unikaldır və ən çox yayılmış proqramlaşdırma dillərindəndir.

Yeri gəlmişək, onu da qeyd etmək lazımdır ki, JavaScript ilə mobil tətbiqlər və serverlər də yarada bilərsiniz.

## JavaScript "üzərində" dillər

JavaScript-in sintaksisi hamının ehtiyaclarını ödəmir. Müxtəlif insanlar, müxtəlif funksionallıqlar tələb edir.

Təbii ki, bu normaldır, çünki layihələr və tələblər hamı üçün fərqlidir.

Son zamanlarda, JavaScript-ə çevrilən (transpiled) bir çox dillər meydana gəlmişdir. Onlar, yalnız development mühitində fərqli funksionallıqlar irəli sürür lakin, daha sonra brauzerdə işləyə bilmək üçün JavaScript-ə çevrilməlidir.

Belə dillərə nümunə olaraq aşağıdakıları göstərmək olar:

- [CoffeeScript](http://coffeescript.org/) JavaScript üçün "Sintaktik şəkərdir"(syntactic sugar) və daha qısa və anlaşıqlı sintaksis ortaya qoyur. Adətən Ruby developerlər onu sevir.
- [TypeScript](http://www.typescriptlang.org/) JavaScript-ə strict type sistemi əlavə edir və development zamanı bəzi bugların qarşısını alır, çox vaxt performansda da qazandırır. TypeScript Microsoft tərəfindən yaradılmışdır və maintain edilir.
- [Flow](http://flow.org/) həmçinin strict type sistemi əlavə edir lakin başqa yol ilə. Facebook tərəfindən yaradılmışdır.

Təbii ki, belə dillər daha çoxdur. Lakin bu dilləri başa düşmək üçün əvvəlcə JavaScript-i tam anlamaq şərtdir.

## Xülasə

- JavaScript ilkin olaraq yalnız brauzerlər üçün yaradılmış, lakin sonradan başqa mühitlərdə də istifadə olunmağa başlamışdır.
- Günümüzdə JavaScript HTML və CSS ilə tam inteqrasiya oluna bilər, geniş yayılmış unikal bir proqramlaşdırma dilidir.
- JavaScript-ə çevrilən və yeni funksionallıqlar təqdim edən bir çox dillər mövcuddur. Bu dillərdən bəzilərinə nəzər salmaq tövsiyyə olunur. Misalçün, JavaScript-i tam başa düşdükdən sonra TypeScript-dən başlaya bilərsiniz.
