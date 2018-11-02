

```python
import pandas as pd
import datetime as dt
df = pd.read_csv('2015-street-tree-census-tree-data.csv')
```

## Clean

```# creates new column of genus names - aggregates species
df['genus_name'] = df['spc_latin'].str.extract('([A-Za-z]\w{0,})')
```

## Analysis

### Health and Species Analysis


```python
#finds number of trees in each health grade
df.health.value_counts()
```




    Good    528850
    Fair     96504
    Poor     26818
    Name: health, dtype: int64




```python
#finds percentage of good in database
good.count()/df.count()
```




    tree_id             0.773412
    block_id            0.773412
    created_at          0.773412
    tree_dbh            0.773412
    stump_diam          0.773412
    curb_loc            0.773412
    status              0.773412
    health              0.810906
    spc_latin           0.810903
    spc_common          0.810903
    steward             0.810904
    guards              0.810906
    sidewalk            0.810904
    user_type           0.773412
    problems            0.810904
    root_stone          0.773412
    root_grate          0.773412
    root_other          0.773412
    trunk_wire          0.773412
    trnk_light          0.773412
    trnk_other          0.773412
    brch_light          0.773412
    brch_shoe           0.773412
    brch_other          0.773412
    address             0.773412
    postcode            0.773412
    zip_city            0.773412
    community board     0.773412
    borocode            0.773412
    borough             0.773412
    cncldist            0.773412
    st_assem            0.773412
    st_senate           0.773412
    nta                 0.773412
    nta_name            0.773412
    boro_ct             0.773412
    state               0.773412
    latitude            0.773412
    longitude           0.773412
    x_sp                0.773412
    y_sp                0.773412
    council district    0.773734
    census tract        0.773734
    bin                 0.773865
    bbl                 0.773865
    dtype: float64




```python
#finds percentage of poor in database
poor.count()/df.count()
```




    tree_id             0.039220
    block_id            0.039220
    created_at          0.039220
    tree_dbh            0.039220
    stump_diam          0.039220
    curb_loc            0.039220
    status              0.039220
    health              0.041121
    spc_latin           0.041120
    spc_common          0.041120
    steward             0.041121
    guards              0.041120
    sidewalk            0.041121
    user_type           0.039220
    problems            0.041121
    root_stone          0.039220
    root_grate          0.039220
    root_other          0.039220
    trunk_wire          0.039220
    trnk_light          0.039220
    trnk_other          0.039220
    brch_light          0.039220
    brch_shoe           0.039220
    brch_other          0.039220
    address             0.039220
    postcode            0.039220
    zip_city            0.039220
    community board     0.039220
    borocode            0.039220
    borough             0.039220
    cncldist            0.039220
    st_assem            0.039220
    st_senate           0.039220
    nta                 0.039220
    nta_name            0.039220
    boro_ct             0.039220
    state               0.039220
    latitude            0.039220
    longitude           0.039220
    x_sp                0.039220
    y_sp                0.039220
    council district    0.039083
    census tract        0.039083
    bin                 0.039080
    bbl                 0.039080
    dtype: float64



Most trees in database (77%) are in good health


```python
#creates mask for trees that have good health
good = df.query('health == "Good"')
#finds seven most common tree species with good health 
good.spc_common.value_counts().nlargest(7)
```




    London planetree     73311
    honeylocust          54501
    Callery pear         48073
    pin oak              45556
    Japanese zelkova     25285
    cherry               24526
    littleleaf linden    23582
    Name: spc_common, dtype: int64




```python
#creates mask for trees that have fair health
fair = df.query('health == "Fair"')
#finds seven most common tree species with fair health
fair.spc_common.value_counts().nlargest(7)
```




    London planetree     11505
    Norway maple          9162
    Callery pear          8769
    honeylocust           8572
    pin oak               6394
    littleleaf linden     4440
    cherry                3448
    Name: spc_common, dtype: int64




```python
#creates mask for trees that have poor health
poor = df.query('health == "Poor"')
#finds seven most common tree species with poor health
poor.spc_common.value_counts().nlargest(7)
```




    Norway maple         3779
    London planetree     2198
    Callery pear         2089
    littleleaf linden    1720
    cherry               1305
    pin oak              1235
    honeylocust          1190
    Name: spc_common, dtype: int64



#### Percentage of London planetree Health


```python
#finds percentage of good health plantrees/good health trees total
good.query('spc_common == "London planetree"').count()/good.count()
```




    tree_id             0.138623
    block_id            0.138623
    created_at          0.138623
    tree_dbh            0.138623
    stump_diam          0.138623
    curb_loc            0.138623
    status              0.138623
    health              0.138623
    spc_latin           0.138624
    spc_common          0.138624
    steward             0.138623
    guards              0.138623
    sidewalk            0.138624
    user_type           0.138623
    problems            0.138630
    root_stone          0.138623
    root_grate          0.138623
    root_other          0.138623
    trunk_wire          0.138623
    trnk_light          0.138623
    trnk_other          0.138623
    brch_light          0.138623
    brch_shoe           0.138623
    brch_other          0.138623
    address             0.138623
    postcode            0.138623
    zip_city            0.138623
    community board     0.138623
    borocode            0.138623
    borough             0.138623
    cncldist            0.138623
    st_assem            0.138623
    st_senate           0.138623
    nta                 0.138623
    nta_name            0.138623
    boro_ct             0.138623
    state               0.138623
    latitude            0.138623
    longitude           0.138623
    x_sp                0.138623
    y_sp                0.138623
    council district    0.138541
    census tract        0.138541
    bin                 0.138628
    bbl                 0.138628
    dtype: float64




```python
#finds percentage of fair health plantrees/fair health trees total
fair.query('spc_common == "London planetree"').count()/fair.count()
```




    tree_id             0.119218
    block_id            0.119218
    created_at          0.119218
    tree_dbh            0.119218
    stump_diam          0.119218
    curb_loc            0.119218
    status              0.119218
    health              0.119218
    spc_latin           0.119218
    spc_common          0.119218
    steward             0.119218
    guards              0.119218
    sidewalk            0.119218
    user_type           0.119218
    problems            0.119227
    root_stone          0.119218
    root_grate          0.119218
    root_other          0.119218
    trunk_wire          0.119218
    trnk_light          0.119218
    trnk_other          0.119218
    brch_light          0.119218
    brch_shoe           0.119218
    brch_other          0.119218
    address             0.119218
    postcode            0.119218
    zip_city            0.119218
    community board     0.119218
    borocode            0.119218
    borough             0.119218
    cncldist            0.119218
    st_assem            0.119218
    st_senate           0.119218
    nta                 0.119218
    nta_name            0.119218
    boro_ct             0.119218
    state               0.119218
    latitude            0.119218
    longitude           0.119218
    x_sp                0.119218
    y_sp                0.119218
    council district    0.119430
    census tract        0.119430
    bin                 0.119590
    bbl                 0.119590
    dtype: float64




```python
#finds percentage of poor health plantrees/poor health trees total
poor.query('spc_common == "London planetree"').count()/poor.count()
```




    tree_id             0.081960
    block_id            0.081960
    created_at          0.081960
    tree_dbh            0.081960
    stump_diam          0.081960
    curb_loc            0.081960
    status              0.081960
    health              0.081960
    spc_latin           0.081963
    spc_common          0.081963
    steward             0.081960
    guards              0.081963
    sidewalk            0.081960
    user_type           0.081960
    problems            0.081966
    root_stone          0.081960
    root_grate          0.081960
    root_other          0.081960
    trunk_wire          0.081960
    trnk_light          0.081960
    trnk_other          0.081960
    brch_light          0.081960
    brch_shoe           0.081960
    brch_other          0.081960
    address             0.081960
    postcode            0.081960
    zip_city            0.081960
    community board     0.081960
    borocode            0.081960
    borough             0.081960
    cncldist            0.081960
    st_assem            0.081960
    st_senate           0.081960
    nta                 0.081960
    nta_name            0.081960
    boro_ct             0.081960
    state               0.081960
    latitude            0.081960
    longitude           0.081960
    x_sp                0.081960
    y_sp                0.081960
    council district    0.082471
    census tract        0.082471
    bin                 0.082432
    bbl                 0.082432
    dtype: float64



#### Percentage of Norway Maple Health


```python
#finds percentage of good health Norway Maples/good health trees total
good.query('spc_common == "Norway maple"').count()/good.count()
```




    tree_id             0.040178
    block_id            0.040178
    created_at          0.040178
    tree_dbh            0.040178
    stump_diam          0.040178
    curb_loc            0.040178
    status              0.040178
    health              0.040178
    spc_latin           0.040178
    spc_common          0.040178
    steward             0.040178
    guards              0.040178
    sidewalk            0.040178
    user_type           0.040178
    problems            0.040181
    root_stone          0.040178
    root_grate          0.040178
    root_other          0.040178
    trunk_wire          0.040178
    trnk_light          0.040178
    trnk_other          0.040178
    brch_light          0.040178
    brch_shoe           0.040178
    brch_other          0.040178
    address             0.040178
    postcode            0.040178
    zip_city            0.040178
    community board     0.040178
    borocode            0.040178
    borough             0.040178
    cncldist            0.040178
    st_assem            0.040178
    st_senate           0.040178
    nta                 0.040178
    nta_name            0.040178
    boro_ct             0.040178
    state               0.040178
    latitude            0.040178
    longitude           0.040178
    x_sp                0.040178
    y_sp                0.040178
    council district    0.040342
    census tract        0.040342
    bin                 0.040423
    bbl                 0.040423
    dtype: float64




```python
#finds percentage of fair health Norway Maples/fair health trees total
fair.query('spc_common == "Norway maple"').count()/fair.count()
```




    tree_id             0.094939
    block_id            0.094939
    created_at          0.094939
    tree_dbh            0.094939
    stump_diam          0.094939
    curb_loc            0.094939
    status              0.094939
    health              0.094939
    spc_latin           0.094939
    spc_common          0.094939
    steward             0.094939
    guards              0.094939
    sidewalk            0.094939
    user_type           0.094939
    problems            0.094946
    root_stone          0.094939
    root_grate          0.094939
    root_other          0.094939
    trunk_wire          0.094939
    trnk_light          0.094939
    trnk_other          0.094939
    brch_light          0.094939
    brch_shoe           0.094939
    brch_other          0.094939
    address             0.094939
    postcode            0.094939
    zip_city            0.094939
    community board     0.094939
    borocode            0.094939
    borough             0.094939
    cncldist            0.094939
    st_assem            0.094939
    st_senate           0.094939
    nta                 0.094939
    nta_name            0.094939
    boro_ct             0.094939
    state               0.094939
    latitude            0.094939
    longitude           0.094939
    x_sp                0.094939
    y_sp                0.094939
    council district    0.095171
    census tract        0.095171
    bin                 0.095421
    bbl                 0.095421
    dtype: float64




```python
#finds percentage of poor health Norway Maples/poor health trees total
poor.query('spc_common == "Norway maple"').count()/poor.count()
```




    tree_id             0.140913
    block_id            0.140913
    created_at          0.140913
    tree_dbh            0.140913
    stump_diam          0.140913
    curb_loc            0.140913
    status              0.140913
    health              0.140913
    spc_latin           0.140918
    spc_common          0.140918
    steward             0.140913
    guards              0.140918
    sidewalk            0.140913
    user_type           0.140913
    problems            0.140923
    root_stone          0.140913
    root_grate          0.140913
    root_other          0.140913
    trunk_wire          0.140913
    trnk_light          0.140913
    trnk_other          0.140913
    brch_light          0.140913
    brch_shoe           0.140913
    brch_other          0.140913
    address             0.140913
    postcode            0.140913
    zip_city            0.140913
    community board     0.140913
    borocode            0.140913
    borough             0.140913
    cncldist            0.140913
    st_assem            0.140913
    st_senate           0.140913
    nta                 0.140913
    nta_name            0.140913
    boro_ct             0.140913
    state               0.140913
    latitude            0.140913
    longitude           0.140913
    x_sp                0.140913
    y_sp                0.140913
    council district    0.141594
    census tract        0.141594
    bin                 0.141789
    bbl                 0.141789
    dtype: float64



Norway maples that are poor health are 14% of poor health trees. Norway maples that are good health is only 4% of good health trees. This does seem somewhat significant, but one aspect that needs to be fleshed out is that there are not that many trees in poor health (only 4% of this dataset), which could lessen the significance of this metric.

### Tree Status and Species Analysis


```python
#finds number of trees for each status
df.status.value_counts()
```




    Alive    652173
    Stump     17654
    Dead      13961
    Name: status, dtype: int64




```python
#finds percentage of alive trees in database
alive.count()/df.count()
```




    tree_id             0.953765
    block_id            0.953765
    created_at          0.953765
    tree_dbh            0.953765
    stump_diam          0.953765
    curb_loc            0.953765
    status              0.953765
    health              1.000000
    spc_latin           0.999998
    spc_common          0.999998
    steward             1.000000
    guards              1.000000
    sidewalk            1.000000
    user_type           0.953765
    problems            1.000000
    root_stone          0.953765
    root_grate          0.953765
    root_other          0.953765
    trunk_wire          0.953765
    trnk_light          0.953765
    trnk_other          0.953765
    brch_light          0.953765
    brch_shoe           0.953765
    brch_other          0.953765
    address             0.953765
    postcode            0.953765
    zip_city            0.953765
    community board     0.953765
    borocode            0.953765
    borough             0.953765
    cncldist            0.953765
    st_assem            0.953765
    st_senate           0.953765
    nta                 0.953765
    nta_name            0.953765
    boro_ct             0.953765
    state               0.953765
    latitude            0.953765
    longitude           0.953765
    x_sp                0.953765
    y_sp                0.953765
    council district    0.953782
    census tract        0.953782
    bin                 0.953786
    bbl                 0.953786
    dtype: float64



Most trees in the database (95%) are alive.


```python
#creates mask for trees that are alive
alive = df.query('status == "Alive"')
#finds seven most alive common tree species
alive.spc_common.value_counts().nlargest()
```




    London planetree    87014
    honeylocust         64263
    Callery pear        58931
    pin oak             53185
    Norway maple        34189
    Name: spc_common, dtype: int64




```python
#creates mask for trees that are dead
dead = df.query('status == "Dead"')
#finds seven most dead common tree species
dead.spc_common.value_counts().nlargest()
```




    honeylocust    1
    Name: spc_common, dtype: int64




```python
#creates mask for stumps
stump = df.query('status == "Stump"')
#finds seven most common tree species that are stumps
stump.spc_common.value_counts().nlargest()
```




    Series([], Name: spc_common, dtype: int64)



There are no species delineations for stumps, and only one for dead trees. Because of this, it isn't possible to look at the distribution of species types across status.

### Sidewalk Status and Species Analysis


```python
#finds number of trees by sidewalk status
df.sidewalk.value_counts()
```




    NoDamage    464978
    Damage      187194
    Name: sidewalk, dtype: int64




```python
#creates mask for trees that damaged sidewalk
damage = df.query('sidewalk == "Damage"')
#finds seven most common tree species that damaged sidewalk
damage.spc_common.value_counts().nlargest(7)
```


```python
#creates mask for trees that didn't damage sidewalk
no_damage = df.query('sidewalk == "NoDamage"')
#finds seven most common tree species that didn't damaged sidewalk
no_damage.spc_common.value_counts().nlargest(7)
```

### Tree Size Analysis


```python
#finds 10 largest average tree dbh - diameter at breast height - by tree species
df.groupby('spc_common')['tree_dbh'].mean().nlargest(10)
```




    spc_common
    London planetree      21.560657
    silver maple          21.013603
    eastern cottonwood    17.061594
    pin oak               16.867707
    weeping willow        15.797872
    pignut hickory        15.393939
    sycamore maple        14.767118
    Norway maple          14.330516
    catalpa               14.284936
    mulberry              14.219533
    Name: tree_dbh, dtype: float64




```python
df.spc_common.value_counts()
```




    London planetree          87014
    honeylocust               64264
    Callery pear              58931
    pin oak                   53185
    Norway maple              34189
    littleleaf linden         29742
    cherry                    29279
    Japanese zelkova          29258
    ginkgo                    21024
    Sophora                   19338
    red maple                 17246
    green ash                 16251
    American linden           13530
    silver maple              12277
    sweetgum                  10657
    northern red oak           8400
    silver linden              7995
    American elm               7975
    maple                      7080
    purple-leaf plum           6879
    swamp white oak            6598
    crimson king maple         5923
    Chinese elm                5345
    'Schubert' chokecherry     4888
    Japanese tree lilac        4568
    eastern redbud             3801
    golden raintree            3719
    crab apple                 3527
    Kentucky coffeetree        3364
    willow oak                 3184
                              ...  
    mimosa                      163
    tartar maple                153
    holly                       138
    southern magnolia           132
    blue spruce                 126
    European beech              125
    red horse chestnut          116
    black maple                 114
    trident maple               110
    false cypress               108
    red pine                    106
    pignut hickory               99
    bigtooth aspen               94
    eastern hemlock              88
    Atlas cedar                  87
    Douglas-fir                  85
    quaking aspen                83
    southern red oak             83
    Ohio buckeye                 75
    Himalayan cedar              72
    boxelder                     64
    Shantung maple               59
    smoketree                    58
    European alder               47
    American larch               46
    black pine                   37
    pitch pine                   33
    Osage-orange                 29
    Scots pine                   25
    Virginia pine                10
    Name: spc_common, Length: 132, dtype: int64



## References
- https://stackoverflow.com/questions/26763344/convert-pandas-column-to-datetime
- https://chrisalbon.com/python/data_wrangling/pandas_regex_to_create_columns/
