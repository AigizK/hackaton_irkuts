# Хакатон Иркутск

- разбиваем на кадры каждое видео: ffmpeg -i test.avi -vf fps=5 /home/hacaton_irkutsk/test/out%d.png
- с помощью TrOCR распознаем время на кадрах. Чтоб каждый фрейм не распознавать, применяется оптимизация - 1_crop time-test.ipynb
- дальше находим координаты людей с помощью Yolo5 в момент когда они зашли или вышли из двери. Так находим координаты дверей - Catboost door model.ipynb
- теперь можем детектить действия. типа если человек появился около двери и исчез, значит зашел. а если его не было и вдруг появился рядом с дверью, значит он вышел
- дополнительно создаем датасет людей и обучаем модель классфицировать 10 классов(с 0 по 11, исключая 7,9 классы)
- и этой моделькой предсказываем кто конкретно выходил или заходил - Submit.ipynb
