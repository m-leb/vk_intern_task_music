## Профильное задание на стажировку VK ##
### ML-инженер ###

Обучена модель CatBoostClassifier

**NDCG@20: 0.9293**

*Нобходимо обратить внимание, что метрика посчитана с учетом эвристик, на основании которых представленное в обучающем датасете бинарное значение было переведено в ранги. В тест было отобрано 20% датасета.*

**ROC-AUC: 0.735**

*Метрика подсчитана локально на 20% датасета. Использовалась модель без подобранных гиперпараметров, не успевал к дедлайну.*

**KAGGLE(privat). ROC-AUC: 0.647**

*Использовалась модель без подобранных гиперпараметров, не успевал к дедлайну.*

### Работа представлена в двух jupyet notebook. ###

1. **EDA.ipynd** - содержит описание работы по анализу данных;
2. **train.ipynd** - содержит обучение модели, подсчёт метрик и подбор гиперпараметров.

### Краткое описание процесса обучения модели. ###

Есть много разных способов решения задачи ранжирования. В данной ситуации, мне показалось логичным рассмотреть эту задачу как задачу бинарной классификации, а ранг выставлять на основе уверенности модели в принадлежности объекта целевому классу.

Собрал все данные в одну таблицу и обучил бинарный классификатор. Логика применения в том, чтобы признаки юзера соеденить с известными признаками объектов (в данном случае, песен) и с помощью модели посчитать вероятности.

Для того, чтобы посчитать целевую метрику использовал идею о том, что данные о том, откуда слушается данная песня могут относительно говорить о предпочтении пользователя. Так как таргет подсчитывается исходя из трейна напрямую, то возникает проблема утечки данных и к посчитанной метрике необходимо относиться с критикой. Метрика ROC-AUС будет более информативной.

При этом, в случае, если нет размеченных данных, такой подход, кажется, вполне приемлемым.
