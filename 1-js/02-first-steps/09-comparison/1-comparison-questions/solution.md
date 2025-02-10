

```js no-beautify
5 > 4 → true
"apple" > "pineapple" → false
"2" > "12" → true
undefined == null → true
undefined === null → false
null == "\n0\n" → false
null === +"\n0\n" → false
```

Bəzi səbəblər:

<<<<<<< HEAD:1-js/02-first-steps/08-comparison/1-comparison-questions/solution.md
1. Əlbəttəki, doğru.
2. Lüğət müqayisəsi. `"a"` `"p"`-dən əvvəl gəlir, buna görə də `"false"`.
3. Yenə lüğət müqayisəsinə görə ilk simvol olan `"2"`, `"1"`-dən böyükdür.
4. `null` və `undefined` bir-birinə bərabərdir. Digər heç bir dəyərlə bərabər olmaz.
5. Sıx bərabərlik (`===`) eyni zamanda hər iki tərəfin tipini də nəzərə alır. Fərqli tiplər olduqda nəticə həmişə `false` olaraq nəticələnir.
6. `(4)` kimi `null` yalnız `undefined` tipinə bərabərdir.
7. Fərqli tiplər arasında sıx bərabərlik (`===`) mümkün deyil.
=======
1. Obviously, true.
2. Dictionary comparison, hence false. `"a"` is smaller than `"p"`.
3. Again, dictionary comparison, first char `"2"` is greater than the first char `"1"`.
4. Values `null` and `undefined` equal each other only.
5. Strict equality is strict. Different types from both sides lead to false.
6. Similar to `(4)`, `null` only equals `undefined`.
7. Strict equality of different types.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e:1-js/02-first-steps/09-comparison/1-comparison-questions/solution.md
