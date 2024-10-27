Шаблон взят из: npm create vue@legacy

- Почему composition api? По api в ТЗ не было ограничения.

- Может ли в одном json-е приходить несколько форм? Если да, то логика нуждается в изменении. Если нет - а на это намекает один title и submitUrl - то зачем в массиве controls сама форма? Возможен вариант полей без формы?

- Почему у одних текстовых полей есть label, а у других нет? Поле "caption" для плейсхолдера инпутов?

- Как можно понять, что эта кнопка должна очистить форму? По названию "Отмена" или по полю position? Ну бред же. Изменил type для кнопки "Отмена" на "reset" - так хотя бы логично

```
{
    "id": "5927943494",
    "control": "BUTTON",
    "caption": "Отмена",
    "parentID": "5927943491",
    "tabIndex": 5,
    "position": 5,
    "type": "button",
}
```

- Возможно нет смысла присылать отдельным объектом контрол 'LABEL' для инпутов - достаточно добавить в структуру к ним поле "label": "Вид кредита". Преимущество будет как минимум в том, что в огромных формах меньше перебирать элементов. Плюс если вынести label в шаблон компонента инпута, проще будет менять оформление при необходимости. В принципе из-за ненужности лейбла он и не вынесен в отдельный компонент, в отличии кнопки и инпута.

- **_Реализовать логику отображения/скрытия полей на основе значений других полей._** - банально и скучно, тем более в реальных задачах скорее всего контролы, которые должны скрываться, будут ссылаться на обязательно заполненные поля, имея поле вроде "requiredFields": [123124, 4564321]. Либо опираться на их значения - для этого опять же нужна полная версия JSON-a

- **_Добавить поддержку дополнительных типов контролов (например, радиокнопки, чекбоксы, выпадающие списки)._** - :D

P.S. "required": "true" - отправка строки вместо boolean, так сложилось исторически?