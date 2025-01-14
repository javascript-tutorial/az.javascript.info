

```js no-beautify
5 > 4 → true
"apple" > "pineapple" → false
"2" > "12" → true
undefined == null → true
undefined === null → false
null == "\n0\n" → false
null === +"\n0\n" → false
```

Səbəblərdən bəziləri:

1. Əlbəttəki, doğru.
2. Lüğət müqayisəsi. `"a"` `"p"`-dən əvvəl gəlir, buna görə də `"false"`.
3. Yenə lüğət müqayisəsinə görə ilk simvol olan `"2"`, `"1"`-dən böyükdür.
4. `null` və `undefined` bir-birinə bərabərdir. Digər heç bir dəyərlə bərabər olmaz.
5. Sıx bərabərlik (`===`) eyni zamanda hər iki tərəfin tipini də nəzərə alır. Fərqli tiplər olduqda nəticə həmişə `false` olaraq nəticələnir.
6. `(4)` kimi `null` yalnız `undefined` tipinə bərabərdir.
7. Fərqli tiplər arasında sıx bərabərlik (`===`) mümkün deyil.
