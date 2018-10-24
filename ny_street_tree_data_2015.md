

```python
import pandas as pd
import datetime as dt
df = pd.read_csv('2015-street-tree-census-tree-data.csv')
```

Data from https://www.kaggle.com/new-york-city/ny-2015-street-tree-census-tree-data

## Clean

```python
#changes characters
df.created_at = df.created_at.str.replace('T', ':')
#changed to datetime
df['created_at'] = pd.to_datetime(df['created_at'])
```

## Analysis
#### Health and Species Analysis

```python
df.spc_common.value_counts().nlargest()
```

```python
good = df.query('health == "Good"')
good.spc_common.value_counts().nlargest(7)
```

```python
fair = df.query('health == "Fair"')
fair.spc_common.value_counts().nlargest(7)
```

```python
poor = df.query('health == "Poor"')
poor.spc_common.value_counts().nlargest(7)
```

#### Tree Status and Species Analysis

```python
df.status.value_counts()
```


```python
alive = df.query('status == "Alive"')
alive.spc_common.value_counts().nlargest()
```

```python
dead = df.query('status == "Dead"')
dead.spc_common.value_counts().nlargest()
```

```python
stump = df.query('status == "Stump"')
stump.spc_common.value_counts().nlargest()
```

#### Sidewalk Status and Species Analysis

```python
df.sidewalk.value_counts()
```

```python
damage = df.query('sidewalk == "Damage"')
damage.spc_common.value_counts().nlargest(7)
```

```python
no_damage = df.query('sidewalk == "NoDamage"')
no_damage.spc_common.value_counts().nlargest(7)
```

## References
- https://stackoverflow.com/questions/26763344/convert-pandas-column-to-datetime
