# ML
## Описание проекта
В данном проекты продесмонтриваны навыки по обучению моделей для опеделения потенциальных клиентво, которые откажутся от услуг Фитнес центра.
Для данного проекта было необходимо разеделить пользователей на кластеры, предсказать, кто из клиентов больше подвержен оттоку. В рамках данного проекта были выполенены следующие задачи:
* Проведен исследовательский анализ данных (EDA)
* Разеделение имеющейся выборки на обучающуюся и тестовую
* Обучение 2х моделей:
  * Линейной регрессии
  * Случаного дерева
* Кластеризация пользователей
* Даны рекомендации

## Цели проекта
Разработать рекомендации по повышению качества работы с клиентами:
1) выделить целевые группы клиентов;
2) предложить меры по снижению оттока;
3) определить другие особенности взаимодействия с клиентами.

## Выводы
Общие выводы:
* `gender` - Доля мужчин и женщин приблизительно одинакова. Как и в числе оставшихся так и в числе ушедших клиентов
* `near_location` - большинство клиентов предпочитают заниматсья около работы/дома. При этом отток клиентов у пользователей, кто занимается не около дома/работы выше.
* `partner` - участники партерских программ более склонны к продолжению занятий по сравнению с другими пользовтелями
* `promo_friends` - среди пользователей, првиеденных друзьями, доля оттока заметно ниже, чем у остальных пользоватлей
* `phone` - по данным этого графика сложно судить, так как сейчас практически везде просят оставить телефон. И данные этого рафика не информативны для исследования
* `group_visit` - среди тех, кто посещает групповые занятия доля оттока меньше
* `contract_period` - чем дольше срок абонимента - тем меньшая доля оттока
* `age` - до 26 лет отток преобладает над оставшимеся пользователями. В 26 наблюдается большая и в последствии растущая заинтерисованность в занятии спортом
* `avg_additional_charges_total` - здесь можно сказать, что доли ушел/остался мало зависят от трат на доп.услуги.
* `month_to_end_contract` - если до окончания контаркта остается один месяц - доля ушедших пользователей очень вилика
* `lifetime` - первые 2 месяца самые показательные, оснавня часть клиентов отваливается в этот промежуток
* `avg_class_frequency_total` - У тех кто ходит до 2 раз в неделю доли оттока примерно одинаковые, но ситуация резко меняется если клиент ходит 3 раза, а если 4-5 раз(это наверно профессиональные спортсмены), то вообще оттока не видно, но таких клиентов значительно меньше.
* `avg_class_frequency_current_month` - чем чаще клиент ходил в клуб за последний месяц, тем и отток меньше

Матрица корреляции по отношению к целевой функции показала следующий результат:
* `gender` и `phone` - не влияют на отток клиентов (коэффиуиенты корреляции близки к 0)
* `near_location`, `partner`, `promo_friends`, `group_visit`, `avg_additional_charges_total`, `avg_class_frequency_total` - имеют корреляцию ниже среднего (коэффициент корреляции менее 0.3)
* `contract_period`, `age`, `month_to_end_contract`, `lifetime`, `avg_class_frequency_current_month` - наибольшая корреляция из представленных (выше 0.3)

Целевая функция - отток клиентов. Сравнение 2х моделей - логичсекой регрессии и случайным лесом.
* ***Доля правильных ответов.*** У обоих методов занчение одинаково
* ***Точность.*** Метод логистической регрессии показал себя лучше
* ***Полнота.*** Метод логистической регрессии показал себя лучше

По всем параметрам чуть впереди модель **Линейной регрессии**

По матрице расстояний получено число кластеров равное **5**.

По заданному в результате числу кластеров проведено обучение модели кластеризации на основании алгоритма K-Means и спрогнозированы кластеры клиентов.
Получено описание кластеров:
***Кластер 0***
* Пользователи живущие около фитнес центра
* Приглашены по партнерской программе
* Преимущественно период контракта 12 месяцев
* В среднем посещают зал 1-2 раза в неделю
* Средний возраст 30 лет
* Слабо подвержены оттоку

***Кластер 1***
* Большинство клиентов живет около фитнес центра
* Средне пользуются партнерской программой
* Купили абонимент в основном на 6 месяцев
* Средний возраст 29 лет
* Подвержены оттоку

***Кластер 2***
* Все живут далеко фитнес центра
* Преимущественно период контракта 1 месяц
* Не используют почти промокоды друзей и партнерскую программу
* Средний возраст 28 лет
* Подвержены оттоку

***Кластер 3***
* Все живут около фитнес центра
* В большенстве не используют партнерскую программу
* Возраст 28 лет
* Абонимент на 1 месяц в основном
* Наиболее подержены оттоку

***Кластер 4***
* Большенство живет около фитнес центра
* Покупают абонимент на 1-6 месяцев
* Возраст 30 лет
* Посещают зал 2-3раза в неделю
* не подвержены оттоку

**Масмиальная доля оттока пользователей у Кластера номер 3**

## Рекомендации
* Предлагать клиентам контракты на более продолжительный срок (путем применения специальных предложений)
* Предлагать для клентов моложе 30 лет больше промоакций и партнерских программ
* Прделагать занятия\атмосферу в фитнес центре, которая будет привлекательна для занятий (2-3 раза в неделю)
* Целевая аудитория:
    * Посетители 30 лет
    * работающие\живущие около фитнес центров
