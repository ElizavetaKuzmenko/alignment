# alignment
Repository for storing the project "Automatic alignment of dictionaries for closely related languages".
See more in the paper (Automatic_alignment.pdf).

# alignment.py
В скрипте alignment.py мы перебираем леммы казахского и татарского языков и ищем наиболее близкие друг к другу строки с помощью расстояния Левенштейна, которое вычисляется в скрипте levenshtein.py

# levenshtein.py
Здесь вычисляется расстояние Левенштейна. Различные его модификации переписывались друг поверх друга, а потому сохранилась только последняя. Но все остальные не представляют особого интереса и с легкостью восстанавливаются из текста работы.

# transition.py
Здесь вычисляются частотности переходов одного символа в другой на основе списка, полученного при предыдущей модификации Левенштейна и записанного в Levenshtein_pairs.txt.

# read_scores.py
Здесь мы проходимся по файлу с результатом работы alignment.py и приводим его в более читаемый вид. Результат работы этого скрипта -- Levenshtein_pairs.txt, который затем используется везде далее.

# extract_words.py
Здесь мы извлекаем из файла Levenshtein_pairs.txt предварительно вручную отобранные хорошие соответствия. Список их постоянно менялся, а потому содержание переменной need lines не несёт особого смысла сейчас.

# vector_models.py
Здесь мы берём хорошие пары когнатов из extract_words.py и на основе их строим линейную регрессию, чтобы предсказывать вектор "когната" в одном языке на основе вектора в другом языке.

# Иное
скрипт извлечения лемм и словоформ из корпусных файлов в формате .prs был в итоге написан на коленке -- в командной строке (частично основан на скрипте Д. Кирьянова) и безвозвратно утерян. Прошу прощения у будущих поколений, что он не попал в этот репозиторий.
Сами корпуса не предоставляются в общее пользование. То же с векторными моделями по двум причинам: - они будут доделаны, - они весят по 2 гигабайта каждая.
