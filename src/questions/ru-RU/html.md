<a href="./README.md">← Назад</a>

<div align="center">
  <img src="../../assets/icons/icons-for-titles/html.png">
  <h2>HTML</h2>
</div>
<br />

<details>
<summary><span>1. Что такое <b>HTML</b>?</span></summary>
<br />

HTML (HyperText Markup Language) - это стандартный язык разметки, используемый для создания и структурирования контента в интернете.

</details>

---

<details>
<summary><span>2. Что такое <b>DOCTYPE</b>?</span></summary>
<br />

DOCTYPE (Document Type Declaration) - это инструкция в начале HTML-документа, которая сообщает браузеру, какую версию HTML использовать для отображения страницы.

</details>

---

<details>
<summary><span>3. Какими способами можно подключить JavaScript файл к HTML документу?</span></summary>
<br />

Существует два основных способа включения JavaScript в HTML документ:

1. **Внешний JavaScript**

   ```html
   <!-- Синхронная загрузка (в конце body) -->
   <body>
   	<!-- контент -->
   	<script src="script.js"></script>
   </body>

   <!-- Асинхронная загрузка (в head) -->
   <head>
   	<script src="script.js" defer></script>
   	<!-- Выполняется после разбора HTML, не блокирует парсинг HTML -->
   	<script src="script.js" async></script>
   	<!-- Выполняется сразу после загрузки, не блокирует парсинг HTML, может нарушить порядок выполнения -->
   </head>
   ```

   Ключевые моменты:

   - Наиболее удобный подход для поддержки
   - Может кэшироваться браузерами
   - Можно управлять поведением загрузки с помощью атрибутов `defer` и `async`
   - Один файл можно использовать на нескольких страницах

2. **Встроенный JavaScript**

   ```html
   <script>
   	function sayHello() {
   		alert('Привет!');
   	}
   </script>
   ```

   или непосредственно в HTML элементах:

   ```html
   <button onclick="sayHello()">Нажми меня</button>
   ```

   - Код встроен непосредственно в HTML
   - Не может кэшироваться
   - Смешивает поведение с контентом
   - Полезно для небольших, специфичных для страницы скриптов
   </details>

---

<details>
<summary><span>4. Что такое семантическая разметка?</span></summary>
<br />

Семантическая разметка - это подход к HTML разметке, где теги используются для передачи смысла контента, а не только для определения его внешнего вида.

</details>

---

<details>
<summary><span>5. Какие примеры семантических HTML тегов вы знаете?</span></summary>
<br />

Вот распространенные семантические HTML теги:

- `<header>` - Определяет секцию заголовка
- `<nav>` - Содержит навигационные ссылки
- `<main>` - Указывает основное содержимое
- `<article>` - Представляет самостоятельную композицию
- `<section>` - Определяет тематическую группировку контента
- `<aside>` - Содержит контент, косвенно связанный с окружающим содержимым
- `<footer>` - Определяет секцию подвала
</details>

---

<details>
<summary><span>6. Какие преимущества дает семантическая разметка?</span></summary>
<br />

- **Улучшает SEO**: Поисковые системы лучше понимают структуру страницы, что может улучшить позиции сайта в результатах поиска

- **Повышает доступность**: Программы чтения с экрана и другие вспомогательные технологии могут лучше интерпретировать контент, делая сайт более удобным для людей с ограниченными возможностями

- **Упрощает обслуживание кода**: Семантические теги делают код более читаемым, уменьшая сложность редактирования и масштабирования

- **Улучшает пользовательский опыт**: Логически структурированный контент помогает пользователям быстрее находить информацию

- **Увеличивает совместимость**: Семантический HTML лучше адаптируется к различным устройствам и будущим веб-стандартам

</details>

---

<details>
<summary><span>7. Какие глобальные HTML атрибуты вы знаете?</span></summary>
<br />

- `class` - Указывает один или несколько классов для стилизации и выбора через JavaScript
- `id` - Определяет уникальный идентификатор элемента
- `style` - Содержит встроенные CSS стили
- `title` - Предоставляет дополнительную информацию при наведении
- `data-*` - Пользовательские атрибуты данных для хранения дополнительной информации
- `hidden` - Скрывает элемент
- `lang` - Указывает язык содержимого элемента
- `dir` - Задает направление текста (ltr или rtl)
- `tabindex` - Управляет порядком табуляции элемента
- `contenteditable` - Делает содержимое элемента редактируемым

</details>

---

<details>
<summary><span>8. Какие мета-теги вы знаете?</span></summary>
<br />

- `<meta charset="UTF-8">` - Указывает кодировку документа. UTF-8 наиболее распространена

- `<meta name="viewport" content="width=device-width, initial-scale=1.0">` - Управляет масштабированием и адаптацией страницы на мобильных устройствах

- `<meta name="description" content="Описание страницы">` - Краткое описание содержимого страницы для поисковых систем и социальных сетей

- `<meta name="keywords" content="ключевые, слова">` - Список ключевых слов

- `<meta name="author" content="Имя автора">` - Указывает автора страницы или сайта

- `<meta name="robots" content="index, follow">` - Задает инструкции для роботов поисковых систем (например, индексировать или нет)

- `<meta property="og:title" content="Заголовок для соцсетей">` - Заголовок страницы для отображения в Facebook, LinkedIn и т.д.

- `<meta property="og:description" content="Описание для соцсетей">` - Краткое описание при шеринге ссылок

- `<meta property="og:image" content="URL изображения">` - Ссылка на изображение, отображаемое при шеринге

</details>

---

<details>
<summary><span>9. Для чего используются data-атрибуты?</span></summary>
<br />

Они используются для хранения дополнительных данных прямо в разметке. В наши дни они чаще всего используются для хранения тестовых идентификаторов, облегчая поиск нужного элемента.

</details>

---

<details>
<summary><span>10. Для чего используется тег <b>label</b>?</span></summary>
<br />

**Привязка метки к элементу формы** - это делает интерфейс более удобным, так как пользователи могут кликнуть по тексту, чтобы активировать соответствующий `<input>`, `<textarea>` или `<select>`.

**Улучшение доступности** - программы чтения с экрана распознают `<label>` и помогают людям с ограниченными возможностями понять, какие данные нужно ввести.

</details>

---

<details>
<summary><span>11. Как можно вставить изображение в HTML?</span></summary>
<br />

Тег `<img>`

```html
<img src="image.jpg" alt="Описание" width="300" height="200" />
```

CSS `background-image`

```css
background-image: url('image.jpg');
```

CSS `content` в `::before` и `::after`

```css
background-image: url('image.jpg');
```

Тег `<picture>`

```html
<picture>
	<source srcset="image-large.jpg" media="(min-width: 800px)" />
	<source srcset="image-small.jpg" media="(max-width: 799px)" />
	<img src="fallback.jpg" alt="Описание" />
</picture>
```

Base64-кодирование

```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..." alt="Описание" />
```

</details>

---

<details>
<summary><span>12. Зачем нужен атрибут <b>alt</b> в теге <b>img</b>?</span></summary>
<br />

- Для поддержки экранных дикторов
- Для улучшения ранжирования изображения в поисковых системах
- Для описания содержимого изображения и отображения альтернативного текста при сбое загрузки

</details>

---

<details>
<summary><span>13. Как используется атрибут <b>srcset</b>?</span></summary>
<br />

Атрибут `srcset` позволяет загружать разные версии изображения в зависимости от разрешения экрана или плотности пикселей.

- В этом примере браузер выберет `image-2x.jpg` для экранов с плотностью 2x и `image-3x.jpg` для 3x.

```html
<img
	src="default.jpg"
	srcset="image-2x.jpg 2x, image-3x.jpg 3x"
	alt="Описание"
/>
```

- Здесь атрибут `srcset` в `source` подсказывает браузеру, какое изображение загрузить в зависимости от ширины экрана.

```html
<picture>
	<source srcset="image-large.jpg" media="(min-width: 800px)" />
	<source srcset="image-medium.jpg" media="(min-width: 500px)" />
	<img src="image-small.jpg" alt="Адаптивное изображение" />
</picture>
```

</details>

---

<details>
<summary><span>14. Какие виды списков существуют в HTML?</span></summary>
<br />

В HTML существуют три основных вида списков:

1. **Упорядоченный список (`<ol>`)** – используется для отображения элементов в определённом порядке. Обычно нумеруется цифрами или буквами.

   ```html
   <ol>
   	<li>Первый пункт</li>
   	<li>Второй пункт</li>
   	<li>Третий пункт</li>
   </ol>
   ```

2. **Неупорядоченный список (`<ul>`)** – элементы располагаются без строгого порядка, обычно с маркерами (кружочки, квадраты и т. д.).

   ```html
   <ul>
   	<li>Элемент 1</li>
   	<li>Элемент 2</li>
   	<li>Элемент 3</li>
   </ul>
   ```

3. **Список определений (`<dl>`)** – используется для отображения терминов и их описаний.
   ```html
   <dl>
   	<dt>HTML</dt>
   	<dd>Язык разметки для создания веб-страниц</dd>
   	<dt>CSS</dt>
   	<dd>Язык стилизации для оформления веб-страниц</dd>
   </dl>
   ```

Дополнительно можно стилизовать списки с помощью CSS, изменяя маркеры, добавляя нестандартную нумерацию или применяя кастомные стили.

</details>

---

<details>
<summary><span>15. Как изменить маркер списка?</span></summary>
<br />

В HTML можно изменить маркер списка с помощью CSS. Вот основные способы:

### 1. **`list-style-type`**

```css
ul {
	list-style-type: square; /* Квадрат вместо круга */
}
```

Доступные значения: `disc` (по умолчанию), `circle`, `square`, `none` (убирает маркеры).

```css
ol {
	list-style-type: upper-roman; /* Римские цифры (I, II, III) */
}
```

Доступные значения: `decimal`, `lower-alpha`, `upper-alpha`, `lower-roman`, `upper-roman`.

### 2. **Кастомное изображение**

```css
ul {
	list-style-image: url('marker.png'); /* Задаём свой маркер */
}
```

Но лучше использовать `background-image`.

### 3. **Кастомный маркер через `::before`**

```css
ul li {
	list-style: none; /* Убираем стандартные маркеры */
}

ul li::before {
	content: '🔥'; /* Добавляем эмодзи вместо маркера */
	margin-right: 10px;
}
```

</details>

---

<details>
<summary><span>16. Что такое <b>iframe</b>? </span></summary>
<br />

Это HTML-элемент, который позволяет встраивать одну веб-страницу внутри другой. Он используется для отображения внешнего контента, например, карт, видео, других веб-страниц или даже интерактивных приложений.

</details>

---

<!--
<details>
<summary><span></span></summary>
<br />

</details>

--- -->
