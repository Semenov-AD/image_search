<div id="header" align="center">
  <img src="https://avatars.mds.yandex.net/i?id=76e8d89f97c87f2a899bc05c540db96c_l-8102231-images-thumbs&n=13" width="500"/>
</div>

# Image Search  

## Описание проекта
Целью проекта является разработка демонстрационной версии поиска изображений по запросу.

Для демонстрационной версии нужно обучить модель, которая получит векторное представление изображения, векторное представление текста, а на выходе выдаст число от 0 до 1 — покажет, насколько текст и картинка подходят друг другу.

### Описание данных

В нашем распоряжении два набора данных: тренировочный и тестовой.  
Тренировочные данные включают в себя:  
- набор изображений;  
- файл формата csv с информацией о идентификаторе изображения, идентификаторе описания и тексте описания;  
- файл с оценками соответствия изображения запросу, полученными с помощью краудсорсинга;  
- файл с оценками экспертов соответствия изображений запросам.  

Тестовые данные представляют собой файл csv с идентификатором запроса, текстом запроса и релевантным изображением.

### В проекте рассмотрены:  
- анализ оценок и их агрегация для получения целевой переменной;  
- векторизация изображений с помощью модели ResNet-18;  
- векторизация текстовых запросов с помощью трансформера Bert;  
- формирование обучающих данных;  
- обучение моделей предсказывать соответствие изображения запросу;  
- тестирование лучшей модели;
- применение модели CLIP.  

### Используемы библиотеки:  
pandas, scikit-learn, nltk, torch, torchvision, transformers, sentence_transformers.  

### Выводы по проекту:  
**Первое решение:**  
Векторизация изображений проводилась с помощью модели ResNet18, векторизация запросов - с помощью трансформера Bert, для оценки соответствия изображения запросу применялись полносвязанные нейросети различный архитектур. Результат тестирования неудовлетворительный. Качество подбора изображений в лучшем случае соответствует критерию "частично подходит".  
**Второе решение:**  
Рассмотрена предобученная модель CLIP версии ViT-B-32. Векторизация изображений и запросов а также оценка соответствия проводилась с помощью данной модели. Результат подбора изображений удовлетворительный, изображения практически точно соответствуют запросу.