## Тема 1. Получение данных
Одними из источников финансовых данных являются биржи, агрегаторы экономической информации и т.п.
### 1.1 Получение данных с Московской биржи
На Московской бирже есть отличное API для получения данных торгов, которое хорошо описано [в этом документе](https://fs.moex.com/files/6523).
Для примера получим исторические данные по индексу RTSI. Это можно сделать с помощью библиотеки pandas
```python
import pandas as pd

def get_batch_index(tiker: str, from_date: str='', start: int=0) -> tuple:
  url = 'https://iss.moex.com/iss/history/engines/stock/markets/index/'
  url += 'boards/rtsi/securities/' + tiker + '.json?start='+ str(start)
  if len(from_date) > 4: url += '&from=' + from_date
  res = pd.read_json(url)
  history = res['history']
  cols = history['columns']
  data = history['data']
  return data, cols, res['history.cursor']['data'][0]
```
