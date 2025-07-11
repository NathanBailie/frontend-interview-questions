<a href="./README.md">← Назад</a>

<div align="center">
  <img src="../../assets/icons/icons-for-titles/react.png">
  <h2>React</h2>
</div>
<br />

<details>
<summary><span>1. Что такое реакт?</span></summary>
<br />

Это JavaScript-библиотека для построения пользовательских интерфейсов с помощью компонентов и виртуального DOM.

</details>

---

<details>
<summary><span>2. В чем преимущества React?</span></summary>
<br />

- **Компонентный подход** — интерфейс разбивается на переиспользуемые и изолированные блоки
- **Virtual DOM** — обновляются только изменённые части дерева, что ускоряет рендеринг
- **Односторонний поток данных** — упрощает отладку и делает поведение приложения предсказуемым
- **JSX** — декларативный синтаксис, объединяющий JavaScript и HTML
- **Хуки** — удобный способ управления состоянием и жизненным циклом без классов
- **Большая экосистема** — множество готовых решений и библиотек (React Router, Redux и т.д.)
- **Поддержка сообщества** — огромное количество обучающих ресурсов и активных разработчиков
- **Подходит для SPA и SSR** — можно использовать и с клиентской, и с серверной отрисовкой (например, через Next.js)
- **Универсальность** — применим не только для web (React Native для мобильной разработки)

</details>

---

<details>
<summary><span>3. Расскажите про <b>алгоритм согласования</b>?</span></summary>
<br />

**Согласование в React** — это процесс сравнения нового и предыдущего Virtual DOM, позволяющий определить минимальные изменения, которые нужно внести в реальный DOM.

**Ключевые моменты:**

- При каждом ререндере React создаёт новое Virtual DOM-дерево.
- Алгоритм сравнивает его с предыдущим деревом, вычисляя _diff_ — различия между ними.
- React использует эвристики:
  - компоненты с разными типами считаются различными и заменяются полностью;
  - элементы в списках требуют уникальных `key` для корректного сравнения;
  - если тип компонента совпадает — сравниваются только пропсы и потомки.

</details>

---

<details>
<summary><span>4. Какая сложность у алгоритма согласования?</span></summary>
<br />

_В среднем_ сложность близка к **O(n)**, но из-за оптимизаций и эвристик — **в реальности работает быстрее**, особенно при хорошо структурированных компонентах и корректных ключах в списках.

</details>

---

<details>
<summary><span>5. Этапы и <b>методы жизненного цикла</b> компонентов?</span></summary>
<br />

В React жизненный цикл компонента делится на **монтаж (mounting)**, **обновление (updating)** и **размонтаж (unmounting)** — каждый этап включает определённые методы или хуки, в зависимости от типа компонента.

**Для классовых компонентов:**

- `constructor` — инициализация состояния.
- `componentDidMount` — вызывается после первого рендера.
- `componentDidUpdate` — вызывается после обновлений пропсов или состояния.
- `componentWillUnmount` — очистка перед удалением компонента.

**Для функциональных компонентов (с хуками):**

- `useEffect(() => {...}, [])` — аналог `componentDidMount`.
- `useEffect(() => {...}, [deps])` — аналог `componentDidUpdate`.
- Возврат функции очистки `return () => {}` из `useEffect` — аналог `componentWillUnmount`.

</details>

---

<details>
<summary><span>6. В какой версии React появились хуки?</span></summary>
<br />

Хуки (hooks) были введены в **React 16.8**, выпущенном в **феврале 2019 года**.

</details>

---

<details>
<summary><span>7. Что такое <b>Virtual DOM</b>?</span></summary>
<br />

**Virtual DOM** — это лёгковесная абстракция над реальным DOM, представляющая собой JavaScript-дерево в памяти, которое React использует для вычисления изменений в интерфейсе перед их применением к реальному DOM.

Вместо непосредственного изменения DOM, React сначала строит виртуальное дерево, вносит в него изменения, затем сравнивает его с предыдущей версией (**diffing**) и применяет только нужные обновления к браузерному DOM.

Такой подход минимизирует количество операций с DOM, который считается «узким местом» по производительности, и делает обновления интерфейса более быстрыми и эффективными.

</details>

---

<details>
<summary><span>8. Какие хуки вы знаете?</span></summary>
<br />

Самые основные и часто используемые:

- `useState` — хранение и обновление локального состояния.
- `useEffect` — выполнение побочных эффектов (например, запросы или таймеры).
- `useContext` — доступ к значению контекста без `Consumer`.
- `useRef` — хранение мутабельных значений или ссылка на DOM-элемент.
- `useMemo` — кэширование вычислений для оптимизации.
- `useCallback` — кэширование функций для избежания лишних ререндеров.
- `useReducer` — управление сложным состоянием через редюсер.
- `useLayoutEffect` — как `useEffect`, но вызывается до отрисовки.

</details>

---

<details>
<summary><span>9. Для чего нужен <b>useState</b>?</span></summary>
<br />

**`useState`** — хук для хранения и управления локальным состоянием в функциональных компонентах.

Он позволяет сохранять значение между рендерами и обновлять его при необходимости — обновление вызывает повторный рендер компонента.

</details>

---

<details>
<summary><span>10. Для чего нужен <b>useRef</b>?</span></summary>
<br />

**`useRef`** — хук, который возвращает мутабельный объект с `.current`, позволяющий сохранять значения между рендерами **без** их повторного вызова.

Он часто используется для:

- доступа к DOM-элементам напрямую;
- хранения значений, которые не участвуют в рендеринге (например, таймеры, предыдущие значения и т.д.).

Обновление `.current` **не вызывает повторный рендер компонента**.

</details>

---

<details>
<summary><span>11. В чем особенность <b>useRef</b> в отличие от <b>useState</b>?</span></summary>
<br />

**`useRef`** реализует поверхностный рендеринг: изменения значения `.current` не триггерят повторный рендер компонента, в отличие от `useState`, который запускает полный цикл обновления при изменении значения

</details>

---

<details>
<summary><span>12. Для чего нужен хук <b>useContext</b>?</span></summary>
<br />

**`useContext`** позволяет создать единое хранилище данных (контекст), доступное всем компонентам внутри соответствующего `<Provider>`, что помогает избежать ручной передачи пропсов на каждом уровне (пропс-дриллинга).

</details>

---

<details>
<summary><span>13. В чем минусы useContext?</span></summary>
<br />

**Главный минус `useContext`** — любое изменение значения в провайдере вызывает перерисовку **всех** компонентов-потребителей, даже если они используют только часть контекста, что может привести к ненужным рендерам и потере производительности.

</details>

---

<details>
<summary><span>14. Что такое <b>пропсы</b>?</span></summary>
<br />

**Пропсы (props)** — это механизм передачи данных от родительского компонента к дочернему в React, позволяющий параметризовать компонент и сделать его переиспользуемым.

Они доступны только для чтения: дочерний компонент может их использовать, но не должен изменять.

</details>

---

<details>
<summary><span>15. Что такое <b>пропс-дриллинг</b>?</span></summary>
<br />

**Пропс-дриллинг** — это ситуация, когда данные передаются через цепочку вложенных компонентов с помощью пропсов, даже если они нужны только на нижнем уровне.

Это плохо тем, что **пропс-дриллинг усложняет структуру приложения**: каждый промежуточный компонент становится вынужденным "переадресатором" данных, что делает код более громоздким, менее читаемым и труднее масштабируемым.

</details>

---

<details>
<summary><span>16. Расскажите про <b>useEffect</b>?</span></summary>
<br />

**`useEffect`** — хук, заменяющий методы жизненного цикла классовых компонентов в функциональных компонентах.

Код внутри `useEffect` выполняется **после монтирования компонента**.  
Для отслеживания изменений отдельных значений можно передать массив зависимостей вторым аргументом.

Для выполнения "очистки" (например, отмена подписок, остановка таймеров) `useEffect` может возвращать **clean-up функцию**, которая будет вызвана **при размонтировании компонента** или перед следующим срабатыванием эффекта.

Поведение `useEffect` зависит от второго аргумента:

- Без массива зависимостей — выполняется **на каждом рендере и перерисовке**;
- С пустым массивом `[]` — выполняется **один раз** при первом рендере (монтаже);
- С заданными зависимостями `[dep1, dep2]` — выполняется при первом рендере и **при изменении этих зависимостей**.

</details>

---

<details>
<summary><span>17. В чем отличие <b>useEffect</b> от <b>useLayoutEffect</b>?</span></summary>
<br />

**`useLayoutEffect`** работает почти так же, как `useEffect`, но с одним ключевым отличием:  
он вызывается **синхронно после всех изменений DOM**, но **до** того, как браузер успеет «показать» обновлённый интерфейс пользователю.\_

В отличие от `useEffect`, который вызывается **асинхронно после отрисовки**, `useLayoutEffect` позволяет выполнить эффекты, которые **должны быть завершены до отображения пользователю** — например, измерение размеров, позиционирование, принудительный `scroll`, синхронные анимации.

> ⚠️ Если в `useLayoutEffect` долго выполняется код — это может вызвать "зависание" интерфейса, так как отрисовка будет отложена.

</details>

---

<details>
<summary><span>18. Что такое <b>JSX</b>?</span></summary>
<br />

Это способ писать HTML-подобную разметку прямо в JavaScript, чтобы описывать, как должен выглядеть интерфейс в React-компонентах.

</details>

---

<details>
<summary><span>19. Что такое <b>логические</b> и <b>презентационные</b> компоненты?</span></summary>
<br />

**Презентационные компоненты** — отвечают за внешний вид: отображают полученные данные через интерфейс

**Логические компоненты** — управляют бизнес-логикой, состоянием и обработкой данных, передавая всё нужное в дочерние презентационные

</details>

---

<details>
<summary><span>20. В чем разница между <b>контроллируемыми</b> и <b>неконтроллируемыми</b> компонентами?</span></summary>
<br />

**Контролируемые компоненты** — управляют своим состоянием через React: значение (например, `input`) хранится в `useState` и обновляется через события.

**Неконтролируемые компоненты** — хранят своё состояние внутри DOM и используют `ref` для доступа к значениям, а не `state`.

</details>

---

<details>
<summary><span>21. Что вызывает перерендер компонента?</span></summary>
<br />

Компонент в React может перерендериться в следующих случаях:

- Изменяется **состояние (`state`)** внутри компонента;
- Приходят новые **пропсы (`props`)** от родителя;
- Изменяется **контекст (`context`)**, к которому привязан компонент;
- Происходит **ререндер родительского компонента**, и текущий компонент не оптимизирован (например, не обёрнут в `React.memo`);
- Применяется **forceUpdate** (в классовых компонентах).

</details>

---

<details>
<summary><span>22. Что такое <b>мемоизация</b>?</span></summary>
<br />

**Мемоизация** — это техника оптимизации, при которой результат функции **сохраняется** (кэшируется), чтобы при повторном вызове с теми же аргументами не выполнять вычисления повторно.

В контексте React она помогает **избегать лишних ререндеров** и повторных вычислений, особенно при использовании `useMemo`, `useCallback` или `React.memo`.

</details>

---

<details>
<summary><span>23. Расскажите про хук <b>useMemo</b>?</span></summary>
<br />

**`useMemo`** — хук, который позволяет закешировать результат вычислений, чтобы избежать их повторного выполнения при ререндере.

Новые вычисления происходят только в случае изменения зависимостей, указанных во втором аргументе.
<br /><br />

**Стоит использовать:**

- **Тяжёлые вычисления** — чтобы не пересчитывать громоздкие операции (сортировка, фильтрация)
- **Стабильные входные данные** — чтобы не вызывать перерендеры из-за изменения ссылок
- **Кэшируемые объекты и массивы** — для стабильности пропсов и избежания лишних эффектов
- **Использование внутри `useEffect` или `useCallback`** — когда важна ссылка на стабильный результат
  <br /><br />

**Не стоит использовать:**

- **Лёгкие вычисления** — кэширование может быть дороже самих вычислений
- **Однократное использование результата** — нет смысла кэшировать то, что сразу отбрасывается
- **Нет проблем с производительностью** — преждевременная оптимизация усложняет поддержку
- **Простая логика** — проще пересчитать, чем усложнять код мемоизацией

</details>

---

<details>
<summary><span>24. Расскажите про хук <b>useCallback</b>?</span></summary>
<br />

**`useCallback`** — хук, мемоизирующий саму функцию, чтобы избежать её пересоздания при каждом ререндере компонента.

Новая функция создаётся только если изменились зависимости, переданные во втором аргументе.
<br /><br />

**Стоит использовать:**

- **Передача функций в дочерние компоненты** — чтобы избежать лишних ререндеров из-за смены ссылки
- **В связке с `React.memo`** — для повышения эффективности мемоизированных компонентов
- **При добавлении обработчиков событий** — особенно в списках и динамических элементах
- **Внутри `useEffect` или `useMemo`** — когда важно сохранять стабильную ссылку на функцию
  <br /><br />

**Не стоит использовать:**

- **Редкое использование колбэка** — нет смысла кэшировать то, что вызывается один раз
- **Минимальная нагрузка** — если функция лёгкая и не передаётся куда-либо, мемоизация может быть излишней
- **Нет зависимости от внешних значений** — проще объявить функцию напрямую в компоненте
- **Погоня за "оптимизацией ради оптимизации"** — код станет сложнее без ощутимой выгоды

</details>

---

<details>
<summary><span>25. Расскажите про <b>React.memo</b>?</span></summary>
<br />

**`React.memo`** — это HOC (Higher Order Component), который позволяет мемоизировать результат рендера функционального компонента. Если пропсы не изменились — компонент не будет перерендерен.

Полезен для оптимизации производительности в компонентах, которые получают одинаковые пропсы, но часто ререндерятся родительским компонентом.
<br /><br />

**Стоит использовать:**

- **Функциональные компоненты с тяжёлым рендером** — чтобы избежать лишних обновлений
- **Часто перерендериваемые родительские компоненты** — снижает нагрузку на дерево
- **Совместно с `useCallback` / `useMemo`** — для стабильности передаваемых пропсов и колбэков
- **Компоненты с неизменяемыми данными** — когда легко сравнивать пропсы по ссылке
  <br /><br />

**Не стоит использовать:**

- **Компоненты с часто изменяющимися пропсами** — мемоизация добавит затрат памяти и не даст выигрыша
- **Компоненты с простой логикой и лёгким рендером** — накладные расходы `React.memo` не оправданы
- **Если нужна глубокая проверка пропсов** — по умолчанию сравнение поверхностное (`shallow comparison`)
- **Оптимизация без явной причины** — может сделать поведение менее предсказуемым и затруднить отладку

</details>

---

<details>
<summary><span>26. Что принимает вторым аргументом React.memo?</span></summary>
<br />

Вторым аргументом `React.memo` принимает функцию-компаратор `areEqual(prevProps, nextProps)`, которая сравнивает предыдущие и новые пропсы компонента.

По умолчанию используется **поверхностное сравнение** (`shallow comparison`) с помощью `Object.is`. Если пропсы включают вложенные объекты, массивы или другие сложные структуры, можно передать **кастомную функцию сравнения**, которая выполнит глубокую проверку нужных полей.

Функция должна возвращать:

- `true` — если **пропсы считаются равными**, и **перерендер не требуется**;
- `false` — если **пропсы различаются**, и компонент должен быть перерендерен.

Это позволяет более точно контролировать, когда компонент должен обновляться, что особенно полезно для оптимизации производительности.

</details>

---

<details>
<summary><span>27. Что такое <b>чистый компонент</b>?</span></summary>
<br />

**Чистый компонент** — это компонент, который при одинаковых входных пропсах всегда возвращает один и тот же результат и не вызывает побочных эффектов.

</details>

---

<details>
<summary><span>28. Что такое <b>батчинг</b>?</span></summary>
<br />

**Батчинг (batching)** — это механизм React, при котором **несколько обновлений состояния объединяются в один ререндер**, чтобы сократить число лишних перерисовок и повысить производительность.

Раньше батчинг работал только внутри синтетических событий, а с React 18 — **включён по умолчанию даже в асинхронных операциях** (например, `setTimeout`, `fetch`, `Promise`).

</details>

---

<details>
<summary><span>29. Расскажите про <b>React Fiber</b>?</span></summary>
<br />

**React Fiber** — это новая архитектура внутреннего движка React (с версии 16), которая позволила более гибко и эффективно управлять рендерами компонентов.

Fiber делит работу React на небольшие части и обрабатывает их пошагово, что даёт возможность:

- приоритизировать обновления (в т.ч. на основе срочности);
- прерывать долгие рендеры и продолжать позже (для отзывчивости UI);
- использовать возможности асинхронного рендеринга (`Concurrent Mode`).

Благодаря Fiber React может лучше контролировать производительность, особенно при сложных интерфейсах и больших объемах данных.

</details>

---

<details>
<summary><span>30. Что такое <b>React Fragment</b>?</span></summary>
<br />

**React Fragment** — это специальный компонент, который позволяет группировать несколько элементов **без создания лишнего узла в DOM**.

</details>

---

<details>
<summary><span>31. В чем разница между <b>React.Fragment</b> и <b><></></b>?</span></summary>
<br />

- **`<>...</>`** — короткая запись, которую можно использовать, если не нужны атрибуты
- **`<React.Fragment>...</React.Fragment>`** — полная форма, необходима, если требуется `key` или другие атрибуты

</details>

---

<details>
<summary><span>32. Для чего нужны <b>ключи</b> в списках?</span></summary>
<br />

Ключи в списках нужны для того, чтобы React мог эффективно отслеживать, какие элементы изменились, были добавлены или удалены, и вносить изменения точечно — не перерисовывая всё дерево компонентов.

</details>

---

<details>
<summary><span>33. Что такое <b>условный рендеринг</b>?</span></summary>
<br />

**Условный рендеринг** — это способ отображать разные элементы в интерфейсе в зависимости от условий, например: авторизован пользователь или нет, загружены ли данные и т.п.

</details>

---

<details>
<summary><span>34. Как получить доступ к дом элементу в React?</span></summary>
<br />

В React доступ к DOM-элементу можно получить через **рефы** — с помощью `useRef` в функциональных компонентах или `createRef` в классовых.

</details>

---

<details>
<summary><span>35. Какие <b>новые хуки</b> появились в React?</span></summary>
<br />

1. **`useId`** — генерирует уникальный стабильный ID, полезен для элементов формы и SSR.
2. **`useTransition`** — позволяет пометить часть обновлений как "неприоритетные" для повышения отзывчивости UI.
3. **`useDeferredValue`** — откладывает обновление значения, чтобы избежать "фриза" интерфейса при быстрой смене данных.
4. **`useSyncExternalStore`** — безопасный способ подписки на внешние сторы, работает с Concurrent Mode.
5. **`useInsertionEffect`** — выполняется до отрисовки DOM, нужен для библиотек, вставляющих стили напрямую.

Также в экспериментальной версии React 19 появились новые хуки:

6. **`use`** — позволяет использовать Promise и другие ресурсы внутри компонентов.
7. **`useFormStatus`** — предоставляет информацию о состоянии отправки формы.
8. **`useOptimistic`** — позволяет оптимистично обновлять UI до завершения асинхронной операции.

</details>

---

<!--
Когда стоит использовать мемоизацию а когда нет?
Для чего используются портал?
 -->

<!-- <details>
<summary><span></span></summary>
<br />

</details>

--- -->
