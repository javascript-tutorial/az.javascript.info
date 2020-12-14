# Tərtibatçı alətləri

Yazdığımız kodlar həmişə xatalara meyillidir. Yəni, yəqin ki, arada bir iki səhv edəcəksiniz də... desəm düzgün olmaz, çünki siz **mütləq** səhv edəcəksiniz. Siz insansınız.

Lakin brauzer mühitində istidəçilər həmin xətaları görmürlər. Əgər yazdığınız skriptdə nə isə qaydasında deyilsə, siz onu görə bilməyəcəksiniz və bu səbəbdən də problemi həll etmək sizin üçün çətin olacaq.

Məhz bu səbəbdən, etdiyimiz xətaları görmək və yazdığımız skriptlər haqqında əlavə məlumat əldə etmək üçün brauzerlər "tərtibatçı alətləri" (developer tools) təqdim edir.

Bu cür alətlərin ən yaxşısı və seviləni Chrome və Firefoxda olduğu üçün, əksər proqramçılar məhz bu brauzerləri istifadə edir. Digər brauzerlər də bu kimi tərtibatçı alətləri təqdim etsələr də, Chrome və Firefox ilə demək olar ki, eyni şey olduğu üçün bu iki brauzer əksər proqramçıların sevimlisidir və sadəcə brauzer-spesifik problemlər yarandığı hallarda digər brauzerlərə keçid edirlər.

<<<<<<< HEAD
Tərtibatçı alətləri güclüdür və çoxlu sayda xüsusiyyətləri var. Başlanğıc üçün, gəlin onları açmağı, xətalara baxmağı və JavaScript komandalarını icra etməyi öyrənək.
=======
Developer tools are potent, they have many features. To start, we'll learn how to open them, look at errors, and run JavaScript commands.
>>>>>>> 23e85b3c33762347e26276ed869e491e959dd557

## Google Chrome

[bug.html](bug.html) səhifəsini açın.

Bu səhifədə yazılmış JavaScript-də xəta var. Bu xəta normal istifadəçidən gizlədilmişdir, gəlin tərtibatçı alətlərini açaq və görək yazılmış kodda nə problem var.

Bunun üçün `key:F12` düyməsini basın. Əgər Mac istifadəçisinizsə o zaman `key:Cmd+Opt+J` kombinasiyasından istifadə edin.

Tərtibatçı alətləri açılacaq və orada çoxlu sayda tab görəcəksiniz. Defolt olaraq isə Console tabı açıq olacaq.

Təxmini belə bir şey:

![chrome](chrome.png)

Konsolun dəqiq görünüşü Chrome-un versiyasına görə dəyişə bilər lakin çox vaxt oxşardır.

- Yəqin ki, konsoldakı qırmızı rəngli xəta mesajını görürsünüz. Bu halda, xəta bizə "lalala" deyə bir şeyin təyin olunmadığını deyir.
- Sağ tərəfdə isə `bug.html:12` adlı keçid var. Bu keçid, bizə xətanın `bug.html` faylının `12`-ci sətrindən qaynaqlandığını göstərir.

Ondan aşağıda gördüyünüz `>` işarəsi isə komanda xəttidir (command line) . Siz burada JavaScript komandaları yaza və `key:Enter` basmaqla həmin komandaları icra edə bilərsiniz.

Artıq xətaları görə bildiyimizə görə hələ ki, bu bizim üçün kifayətdir. Sonrakı fəsillərdə debugging (bug-lardan təmizləmə) haqqında daha çox öyrənəcəyik.

```smart header="Bir neçə sətirlik komandalar"
Adətən komandanı daxil edib `key:Enter` basdıqdan sonra həmin komanda icra olunur.

Əgər bir neçə sətirlik kod yazırsınızsa, o zaman `key:Shift+Enter` basın. Bu vasitə ilə siz uzun JavaScript kodları yaza və icra edə bilərsiniz.
```

## Firefox, Edge və başqaları

Əksər brauzerlərdə alətləri açmaq üçün `key:F12` komandasından istifadə olunur.

Görünüş hamısında demək olar ki, eynidir. Birini istifadə etməyi tam öyrəndikdən sonra (misalçün Chrome ilə başlaya bilərsiniz) digərlərinə rahatlıqla keçid edə bilərsiniz.

## Safari

Safaridə (Mac brauzerdiri, Windows/Linux əməliyyat sistemlərində dəstəklənmir) isə vəziyyət bir qədər fərqlidir. Əvvəlcə "Develop menu"-nu aktiv etməyimiz lazımdır.

Bunun üçün öncəliklər (Preferences) pəncərəsini açın və "Advanced" panelinə daxil olun. Orada aşağıdakı kimi bir checkbox görəcəksiniz:

![safari](safari.png)

İndi isə `key:Cmd+Opt+C` kombinasiyası ilə konsolu aça və bağlaya bilərsiniz. Nəzərinizə çatdıraq ki, yuxarı menyuda da "Develop" adlı yeni bir seçim yaranmışdır.

## Xülasə

- Tərtibatçı alətləri bizə xətaları görmək, komandalar icra etmək, dəyişənləri təhlil etmək və s. bu kimi çoxlu sayda imkanlar yaradır.
- `key:F12` komandası ilə onları aça və istifadə edə bilərsiniz. Chrome for Mac üçün `key:Cmd+Opt+J`, Safari üçün isə `key:Cmd+Opt+C` kombinasiyalarında istifadə edin (unutmayın ki, Safaridə əvvəlcə bunu aktivləşdirmək lazmdır).

Mühit ilə bağlı hər şeyi yekunlaşdırdığımız üçün artıq JavaScript ilə yaxından tanış olmağa tam hazırıq.
