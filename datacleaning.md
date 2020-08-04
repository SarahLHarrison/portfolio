### Data Cleaning

In this example, I cleaned reaction time (RT) data from an experiment to prepare it for further analysis. 


```python
import pandas as pd
import numpy as np
from scipy.stats import zscore

#read in data
df = pd.read_csv(in_file, sep='\t')

#drop rows with null values, repeated rows, and practice trials
df = df.dropna()
df = df.iloc[::3, :]
df = df[df.block != 'practice']

#convert RTs to ms
df['rt'] = df['rt'] * 1000

#remove outliers
df['zrt'] = zscore(df['rt'])
df = df[df['zrt'] <= 3]
```
