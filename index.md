# Морфемная разметка русского языка
## Формат разметки
Морфы слова разделяются между собой с помощью символа `/`. После каждого морфа указывается тип его морфемы после символа`:`. Используются основные типы морфем:

* `PREF` -- приставка;
* `ROOT` -- корень;
* `SUFF` -- суффикс;
* `END` -- окончание;
* `POSTFIX` -- постфикс (возвратные `ся` и `сь` для глаголов).

Дополнительно используются вспомогательные типы:

* `LINK` -- соединительная гласная в многокоренных словах;
* `HYPH` -- дефис в словах с дефисом.

Примеры размеченных слов:
```
рубчик  руб:ROOT/ч:SUFF/ик:SUFF
обижаться       обиж:ROOT/а:SUFF/ть:END/ся:POSTFIX
биобиблиографический    био:ROOT/библи:ROOT/о:LINK/граф:ROOT/ическ:SUFF/ий:END
сборно-щитовой  с:PREF/бор:ROOT/н:SUFF/о:LINK/-:HYPH/щит:ROOT/ов:SUFF/ой:END
```

## Датасеты с морфемной разметкой для русского языка

### [RuMorphs-Lemmas](https://github.com/cmc-msu-ai/NLPDatasets/releases/download/v0.2/RuMorphs-Lemmas.txt)
Датасет содержит 96036 лемм русского языка с морфемной разметкой в формате TSV: в первом столбце содержится лемма, во втором её разбор. Датасет построен на основе словообразовательного словаря А. Н. Тихонова. Фрагмент датасета:

```
спутываться     с:PREF/пут:ROOT/ыва:SUFF/ть:END/ся:POSTFIX
фуфаечка        фуфаеч:ROOT/к:SUFF/а:END
променять       про:PREF/мен:ROOT/я:SUFF/ть:END
лужа    луж:ROOT/а:END
заиндеветь      за:PREF/ин:ROOT/дев:SUFF/е:SUFF/ть:END
отсаживаться    от:PREF/саж:ROOT/ива:SUFF/ть:END/ся:POSTFIX
тамильский      тамиль:ROOT/ск:SUFF/ий:END
снетковый       снетк:ROOT/ов:SUFF/ый:END
```

Вариант датасета без классификации морфем доступен доступен по [ссылке](https://github.com/cmc-msu-ai/NLPDatasets/blob/main/morphemic/dicts/tikhonovsource.txt).

### [RuMorphs-Words](https://github.com/cmc-msu-ai/NLPDatasets/releases/download/v0.2/RuMorphs-Words.txt)
Датасет содержит 1756376 уникальных словоформ русского языка с морфемной разметкой в формате TSV: в первом столбце содержится словоформа, во втором её разбор, в третьем флексия словоизменительного класса, в четвертом пара (часть речи словоформы, словоизменительный класс). Датасет построен на основе датасета RuMorph-Lemmas с использованием [словоизменитльных классов русского языка](https://github.com/alesapin/XMorphy/blob/master/scripts/rules/classes_non_nested_infl_gerund_short_adj.json), открытого морфологического словаря [Opencorpora](http://opencorpora.org/) и [процедуры на основе правил](https://github.com/alesapin/XMorphy/blob/master/scripts/rules/rules_splitter_generator.py). Фрагмент датасета:
```
расшить рас:PREF/ши:ROOT/ть:END с-ши-ть (sp: VERB, class_num: 201)
расшил  рас:PREF/ш:ROOT/и:SUFF/л:SUFF   с-ш-и-л (sp: VERB, class_num: 201)
расшила рас:PREF/ш:ROOT/и:SUFF/л:SUFF/а:END     с-ш-и-л-а       (sp: VERB, class_num: 201)
расшило рас:PREF/ш:ROOT/и:SUFF/л:SUFF/о:END     с-ш-и-л-о       (sp: VERB, class_num: 201)
расшили рас:PREF/ши:ROOT/л:SUFF/и:END   с-ши-л-и        (sp: VERB, class_num: 201)
разошью разо:PREF/шь:ROOT/ю:END зо-шь-ю (sp: VERB, class_num: 201)
разошьешь       разо:PREF/шь:ROOT/ешь:END       зо-шь-ешь       (sp: VERB, class_num: 201)
разошьет        разо:PREF/шь:ROOT/ет:END        зо-шь-ет        (sp: VERB, class_num: 201)
разошьем        разо:PREF/шь:ROOT/ем:END        зо-шь-ем        (sp: VERB, class_num: 201)
разошьете       разо:PREF/шь:ROOT/ете:END       зо-шь-ете       (sp: VERB, class_num: 201)
разошьют        разо:PREF/шь:ROOT/ют:END        зо-шь-ют        (sp: VERB, class_num: 201)
расшей  рас:PREF/ше:ROOT/й:END  с-ше-й  (sp: VERB, class_num: 201)
расшейте        рас:PREF/ше:ROOT/йте:END        с-ше-йте        (sp: VERB, class_num: 201)
расшив  рас:PREF/ши:ROOT/в:SUFF с-ши-в  (sp: GRND, class_num: 201)
расшивши        рас:PREF/ши:ROOT/вши:SUFF       с-ши-вши        (sp: GRND, class_num: 201)
```

### [RuMorphs-SynTagRus](https://github.com/cmc-msu-ai/NLPDatasets/releases/download/v0.2/RuMorphs-SynTagRus.txt)
Датасет построен на основе корпуса с морфологической разметкой [SynTagRus](https://universaldependencies.org/treebanks/ru_syntagrus/index.html) и содержит 1105517 словоформ русского языка с морфологической и морфемной разметкой. Файл содержит исходные предложения SynTagRus в формате TSV к которым в 3-ем и 5-ом столбцах добавлена морфемная разметка словоформы и леммы соответственно. Разметка датасета производилась в автоматическом режиме с помощью модели морфемного разбора обученной на датасете RuMorphs-Words. Фрагмент датасета:
```
1       Скорее  скор:ROOT/ее:END        скорее  скор:ROOT/ее:END        ADV     Degree=Pos
2       всего   всего:ROOT      все     все:ROOT        PRON    Animacy=Inan|Case=Gen|Gender=Neut|Number=Sing
3       ,       ,:UNKN  ,       ,:UNKN  PUNCT   _
4       это     это:ROOT        это     это:ROOT        PRON    Animacy=Inan|Case=Nom|Gender=Neut|Number=Sing
5       фальшивка       фальш:ROOT/ив:SUFF/к:SUFF/а:END фальшивка       фальш:ROOT/ив:SUFF/к:SUFF/а:END NOUN    Animacy=Inan|Case=Nom|Gender=Fem|Number=Sing
6       или     или:ROOT        или     или:ROOT        CCONJ   _
7       не      не:ROOT не      не:ROOT PART    Polarity=Neg
8       его     ег:ROOT/о:END   его     ег:ROOT/о:END   DET     _
9       фотография      фото:ROOT/граф:ROOT/и:SUFF/я:END        фотография      фото:ROOT/граф:ROOT/и:SUFF/я:END        NOUN    Animacy=Inan|Case=Nom|Gender=Fem|Number=Sing
10      .       .:UNKN  .       .:UNKN  PUNCT   _
```
