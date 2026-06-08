# Live Preview: требования к изображениям

## Главный принцип

Live Preview собирается из слоёв:

1. подставка выбранного типа и цвета;
2. дополнительные опции;
3. фигурки;
4. в будущем, если понадобится, отдельные передние/задние части сложных опций.

Чтобы слои не превращались в кашу, все PNG должны быть подготовлены в одной
системе координат.

## Холст

- Формат: `4:3`.
- Рекомендуемый размер исходников: `1600x1200 px`.
- Экспорт: прозрачный `PNG`.
- Каждый слой должен оставаться на общем холсте `1600x1200`, а не быть
  обрезанным по видимому объекту.
- Объекты должны стоять на тех же местах, где они должны отображаться в сборке.

Если дизайнеру удобнее работать в `1000x750 px`, это тоже допустимо, но тогда
все слои должны быть именно в этом размере. Смешивать размеры нельзя.

## Подставки

У подставки один цвет равен одной картинке. Значит нужны отдельные PNG для
каждой пары:

```text
stand_code + material_variant_code
```

Пример именования:

```text
stand_1__plywood_default.png
stand_1__acrylic_clear_3mm.png
stand_1__acrylic_red_3mm.png
stand_1__acrylic_blue_3mm.png
stand_2__plywood_default.png
stand_2__acrylic_clear_3mm.png
stand_2__acrylic_red_3mm.png
stand_2__acrylic_blue_3mm.png
```

То же самое нужно для `stand_3` и `stand_4`, если эти цвета доступны для них.

## Фигурки

Нужны отдельные прозрачные PNG для всех фигурок из логики:

```text
samovar
balalaika
matryoshka_khokhloma_big
matryoshka_khokhloma_medium
matryoshka_khokhloma_small
matryoshka_gorodets_big
matryoshka_gorodets_medium
matryoshka_gorodets_small
matryoshka_gzhel_big
matryoshka_gzhel_medium
matryoshka_gzhel_small
```

Важно:

- фигурки должны быть выровнены по нижней точке, чтобы они стояли на подставке;
- большой размер матрёшек считается базовым масштабом;
- средний и малый размеры должны быть визуально пропорциональны реальной высоте.

## Опции

Нужны PNG для:

```text
small_block
medium_block
weekly_notebook
pens
bookmarks
stickers
basket
```

Для корзинки лучше подготовить два слоя, если она должна перекрывать фигурки:

```text
basket_back.png
basket_front.png
```

Сейчас frontend умеет работать с одним слоем `basket.png`; разделение на
front/back можно будет включить следующим шагом без изменения бизнес-логики.

## Чего нельзя делать

- Нельзя отдавать картинки с разным холстом и разным масштабом.
- Нельзя обрезать PNG по объекту, если слой должен участвовать в общей сборке.
- Нельзя называть файлы по русским названиям товаров. Нужны стабильные `code`.
- Нельзя смешивать вид сверху, фронтальный вид и перспективу в одном наборе.

## Что прислать разработке

Минимальный набор для калибровки:

```text
stand_2__plywood_default.png
stand_2__acrylic_clear_3mm.png
stand_2__acrylic_red_3mm.png
stand_2__acrylic_blue_3mm.png
basket.png
small_block.png
matryoshka_khokhloma_big.png
matryoshka_gorodets_big.png
matryoshka_gzhel_big.png
```

После него можно быстро настроить координаты и уже размножить систему на все
остальные подставки, фигурки и опции.
