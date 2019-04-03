 1. **Все теги должны работать даже без CSS и JS**;

    > Все тексты, видимые сначала при открытии страницы так же должны быть доступны, формы должны сабмититься, ссылки должны переходить (а ссылки по которым вообще не должно быть перехода и для которых принято ставить `href="#"` вообще не использовать, это будет далее).

 1. **Структура тегов в первую очередь должна идти от содержания, а не от дизайна**;
 
    > ![пример](http://image.prntscr.com/image/a89c1aed00f14864851989caceacd59d.png) - например, такой элемент можно оформить как четыре подряд идущих элемента - иконка сообщений, бадж с цифрой 10, иконка аватара и имя пользователя. Но тут надо явно объединить с помощью `<div>` два блока, чтобы семантически они были отдельными - блок с информацией по сообщению и блок про пользователя. Для css потом, возможно, придется писать лишние стили, но верстка будет более осмысленной и не привязанной лишний раз к дизайну
  
 1. **Начинаем новый .html файл с `<!DOCTYPE html>`, как следует по HTML5 стандарту, если этот файл не предназначен для расширения другими файлами через какой-нибудь шаблонизатор**;

 1. **Перед `<!DOCTYPE html>` не должно быть никаких символов, включая пробелов и переносов строк**;

 1. **Внутри `<head>` первым тегом должно идти `<meta charset="utf-8">`**;

 1. **У каждой страницы должны быть теги `title` и мета теги `keywords`, `description` (на содержимое спросить конент у менеджера)**;

 1. **В `head` добавлять `<meta name="viewport" content="initial-scale=1.0, width=device-width">` - на мобильных браузерах можно избежать горизонтального скролла и масштабировать конент на всю ширину экрана**;

 1. **Не использовать самозакрывающиеся теги, если они не поддерживают другого режима**;
    Нельзя: <br>
    ```html
      <div />
      <span />
    ```
    Можно:
    ```html
      <link />
      <img />
      <input />
    ```
  
 1. **Все атрибуты должны быть внутри двойных кавычек**;
 
    Нельзя:
    ```html
      <img width=200 />
      <div class=block>
      <a href='/some/url'>
    ```
    Можно:
    ```html
      <img width="200" />
      <div class="block">
      <a href="/some/url">
    ```

    >Плюс, если в проекте нет других соглашений, атрибуты должны именоваться lower-case-hyphenated (имена только маленькими буквами и через дефис) и если значение строковое и показывает какое-то имя, то тоже должно быть lower-case-hyphenated. Кастомные атрибуты стараться начинать с data- (это стандартная практика, рекомендованная для HTML5).

    >Пример: `<a href="/" data-index="33" data-page-name="main-page">Home</a>`
  
 1. **Не использовать id, кроме случаев, когда они семантически востребованы**;
    > Когда гарантируется их уникальность например на уровне базы данных и когда вам нужно
    > - требуется рабочая навигация в рамках одной страницы (например, как на Википедии или на этом сайте сборника [best-practices](https://isobar-idev.github.io/code-standards/#javascript_javascript);
    > - требуется связать `<label>` и `<input />`, которые находятся в совершенно разных ветках дерева DOM (вообще, лучше всегда просто `<input />` внутрь `<label>` ставить и тогда никакие айдишники не нужны);

 1. **Все теги идут только с классами - никаких пустых `<div>`, `<section>` и тд. Но можно для инлайновых элементов, если есть четкое понимание зачем. Это очень сильно мешает новым людям входить в проект и вам через некоторое время разобраться в собственной верстке**;

 1. **Избегать по-максимуму инлайновые стили и обработчики событий в `html` (то есть никаких `<div onclick="func()">`)**;

 1. **Все изображения должны содержать alt**;

 1. **Не использовать ссылки с пустым или невалидным `href` (никаких `<a href="#">`) - тогда лучше использовать ссылку-заглушку на несуществующий урл, который явно говорит, что ссылка не проставлена**;
    > Если вы верстаете проект, в котором есть страницы, которых нет в дизайне (допустим они потом при интеграции с сервером динамически создаваться будут), то лучше ставьте адрес, который явно говорит, что это ссылка-заглушка. Причем все ссылки-заглушки должны в рамках проекта иметь один адрес, например `<a href="/mock-address/change-me"></a>` - тогда после сдачи

    > Для SPA иногда приходится динамически js-ом генерить такие ссылки (как минимум в angular, там для этого даже отдельный атрибут ng-href), которые бы поддерживали динамическую генерацию на основе чистого клиентского раутинга 

    > Не надо никаких `<a href="#">` или `<a href="javascript:someFunc(1)">`. Плюс не надо сюда сохранять урлы до методов API на сервере, надеясь, что JS-ом вы сможете потом обработать клик, отправить ajax запрос на сервер по этому урлу и сами обработать ответ. Этого не произойдет, если юзер откроет ссылку в новой вкладке через контекстное меню или клик колесом мыши, например. Все урлы, указанные в `href` должны открывать читаемый для человека контент, который целиком зависит только от сервера.
    [Оригинал последнего абзаца](https://isobar-idev.github.io/code-standards/#html_anchors_amp_links)

 1. **Ссылки на чужие сайты должны содержать атрибут `target="_blank"`, чтобы открываться в новом окне**;

 1. **Все ссылки с `target="_blank"` должны так же содержать атрибут `rel="noopener noreferrer"`, это связано с уязвимостью:**
    > Это связано с [уязвимостью](https://mathiasbynens.github.io/rel-noopener/) в соотвествии с которой сайт, который вы открыли, получит доступ к сайту, с которого перешли через `window.opener`, причем это работает даже кроссдоменно
  
 1. **Все инпуты, селекты и другие интерактивные элементы должны быть обрамлены в форме `<form>`**;

 1. **Все интерактивные элементы, для которых дизайнером задуман нетривиальный порядок полей, использовать всегда `tabindex`, плюс всегда кнопка сабмита в tabindex должна быть последней (соответственно если есть визуально поля под кнопкой, у них должен быть tabindex и он должен быть меньше, чем у кнопки)**;

 1. **Спрашивать у дизайнеров, какие элементы делать autofocus на какой странице**;

 1. **Никогда не допускать вложенные формы `<form>`**;

 1. **Если у поля есть четкое назначение, то использовать соответствующий тип (email, number, color и тд)**;

 1. **Каждый тег в котором может лежать текст должен быть проверен на большое количество символов**;
    > * все заголовки и все теги с текстовыми описаниями;
    > * все инпуты проверять, чтобы при заполнении текст не прижимался вплотную к правой границе;
    ![image](https://user-images.githubusercontent.com/12808495/55307777-c0e18e80-5482-11e9-927f-9c195d81555e.png)
  
 1. **Классические инлайн теги должны быть только inline или inline-block и в них не должно быть ничего кроме простого текста и других таких же инлайновых тегов**;
    > Исключения: `<a>` - иногда ссылку надо сделать блочным элементом, но лучше использовать inline-block
  
 1. **Для телефонов, емайл-адресов и скайп никнеймов нужно использовать `<a>` c соответствующим адресом**;
    ```html
      <a href="tel: +74951234567">+7 (495) 123-45-67</a>
      <a href="mailto: example@mail.ru">example@mail.ru</a>
      <a href="skype: someskype?call">someskype</a>
    ```
 1. **Отображать примеры кода через тег `<code>`**;
    > Иногда на некоторых проектах нужно прямо на сайте показывать пользователям примеры кода (например, [здесь в туториале Реакта](https://reactjs.org/) целая куча примеров кода) - эти примеры должны быть написано моноширинными шрифтами и отличаться от обычного текста - по умолчанию достаточно обрамить код в тeг `<code>`.

  
  
  
  
  
  