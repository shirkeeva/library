<b>1. Модель данных</b>
<br>Модель данных, лежащая в основе заданного приложения, описана с помощью ER диаграммы со следующими таблицами: Автор, Книга, Издательство, Выданная книга, Студент
![datamodel](https://user-images.githubusercontent.com/58703112/139531377-e47919ca-cd31-4a3e-92d3-9aa361dd9deb.jpg)
<br>Между таблицами Автор и Книга а также Издательство и Книга построены связи "многие ко многим" с помощью дополнительных таблиц.
<br><br>
<b>2. Популярный автор</b>
<br>select a.authorname, count(ib.issuedate) from author a 
<br>join booksauthor ba on a.authorid = ba.authorid
<br>join issuedbook ib on ba.bookid = ib.bookid
<br>group by a.authorname
<br>order by count(ib.issuedate) desc limit 1
<br><br>
<b>3. Злостный читатель</b>
<br>Злостный читатель - это человек, который не возвращает книги дольше 60 дней.
<br>1. Создаем пустой список для заполнения его "злостными читателями"
<br>2. В цикле проходимся по каждой выданной книге;
<br>3. Если дата возврата отсутствует, то для проверки определяем её как сегодняшний день;
<br>4. Если между датой выдачи и датой возврата >= 60 дней И студент не находится в списке злостных читателей, то определяем студента, взявшего эту книгу, как "злостного читателя".
<br><br>Написанная функция для поиска "злостного читателя" находится в файле application.js
