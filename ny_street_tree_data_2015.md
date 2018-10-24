

```python
import pandas as pd
import datetime as dt
df = pd.read_csv('2015-street-tree-census-tree-data.csv')
```

```python
Data from https://www.kaggle.com/new-york-city/ny-2015-street-tree-census-tree-data
```

```python
#changes characters
df.created_at = df.created_at.str.replace('T', ':')
#changed to datetime
df['created_at'] = pd.to_datetime(df['created_at'])
```


```python
df.spc_common.value_counts().nlargest()
```




    London planetree    87014
    honeylocust         64264
    Callery pear        58931
    pin oak             53185
    Norway maple        34189
    Name: spc_common, dtype: int64




```python
df.status.value_counts()
```




    Alive    652173
    Stump     17654
    Dead      13961
    Name: status, dtype: int64




```python
alive = df.query('status == "Alive"')
alive.spc_common.value_counts().nlargest()
```




    London planetree    87014
    honeylocust         64263
    Callery pear        58931
    pin oak             53185
    Norway maple        34189
    Name: spc_common, dtype: int64




```python
df.sidewalk.value_counts()
```




    NoDamage    464978
    Damage      187194
    Name: sidewalk, dtype: int64




```python
damage = df.query('sidewalk == "Damage"')
damage.spc_common.value_counts().nlargest(7)
```




    London planetree     34433
    honeylocust          22856
    pin oak              18937
    Callery pear         12852
    Norway maple         11159
    littleleaf linden     9272
    Japanese zelkova      7362
    Name: spc_common, dtype: int64




```python
no_damage = df.query('sidewalk == "NoDamage"')
no_damage.spc_common.value_counts().nlargest(7)
```




    London planetree    52581
    Callery pear        46079
    honeylocust         41406
    pin oak             34248
    cherry              25048
    Norway maple        23030
    Japanese zelkova    21896
    Name: spc_common, dtype: int64


