## Тема 2. Графический анализ
Это один из самых наглядных способов анализа, поэтому его используют и для предварительного анализа и в качестве подтверждения.
```python
import matplotlib.pyplot as plt
import pandas as pd
df = pd.read_csv('rtsi.csv', index_col=0, parse_dates=[0])
data = df['2024-05-01':].drop(columns='VALUE')
data.plot(figsize=(18, 12))
```
![График с четырьмя линииями](./fig2_1.png)
