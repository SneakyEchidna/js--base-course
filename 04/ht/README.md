# Теория

Прочитать материалы по следующим темам ( как минимум знать что это такое, а хотя бы пару слов зачем и как использовать ). По каждому пункту должна быть минимум 1 карточка в Anki

 - SOLID
 - KISS
 - DRY
 - YAGNI
 - MVC
 - Паттерны проектирования ( Что это? Какие есть группы? )
 - Антипаттерны проектирования
 - Модульные системы (CommonJS/ ES6 modules/ AMD)
 - requirejs

## Календарь задач

Реализовать одностраничное приложение "Календарь задач".

![enter image description here](https://github.com/vvscode/js--base-course/blob/e39522cad41dfc6022bee5526fcb26f754c91260/04/ht/calendar-spa.png)

### Функционал календаря

Опциональные параметры передаются в конструтор календаря

 - Отображение календаря
 - Опциональное отображение текущего месяца/года
 - Опциональная возможность измнения месяца кнопками "вправо/влево"
 - При двойном клике на ячейку календаря с датой - запросить у пользователя данные о задаче, после чего вывести запись о задаче в соответстачевующей ячейке. Возможность добавления записей опциональная
 - На каждой записи должен отображаться значек удаления записи ( удаление записей опциональное ). При клике по нему нужно запросить у пользователя подтверждение. После подтверждения удалить запись из календаря.
 - Календарь должен иметь возможность работать в нескольких экземплярах на странице. Независимо друг от друга.
 - При обновлении страницы информация о созданных заданиях должна сохраняться

## Страницы SPA ( SinglePageApplication)

### Демонстрация работы календаря

Представляет полнофункциональный календарь. Со всеми возможностями

### Создание своего календаря

Отображение трех блоков

#### 	1 - Форма настройки календаря
Форма для настройки всех опциональных возможностей календаря, ввода фиксированной даты ( или отсутствие фиксации даты ), настройка класса для виджета и тп

#### 2 - Блок с кодом
Блок с кодом, который позволит запустить на странице календарь с выбранными настройками ( см выше ).  Например
```
    <script scr="..."></script>
		<script>
		(function() {
			  var id = 'calendar' +  Math.random() ;
			  document.write('<div id="' + id + '"></div>');
			  new Calendar({
			    el: '#' + id,
			    showMonth: true,
			    allowAdd: false,
			    allowRemove: true,
			    date: null // date = [2017, 11]
			  })
		})();
  </script>
  ``` 

#### 3 - Предпросмотр календаря
Отображение календаря с текущими настройками.

Любые изменения в форме 1 сразу отображаются на данных в блоках 2 и 3.

Навигация между страницами происходит через меню, вверху страницы. Данные в текущей итерации хранятся в `localStorage` (важно учесть, что при нескольких календарях на странице данные для них хранятся раздельно ). 

Код разнести по нескольким файлам ( в соответсвии с назначением ) и интерфейсные методы/функции описать `jsdoc` комментариями.