### Summary Stats

This is an exmaple of calcuating summary stats on a variable in a data frame and then adding them to a new data frame for easy display. This new DataFrame also puts the data in a better format for later plotting. 

This example was worked on in collboration with Isaac Zacher, a classmate.




```python
#Calculate summary stats for each condition
rt_mean = data.groupby(['flankers', 'simon'])[['rt']].mean().round(2)
rt_std = data.groupby(['flankers', 'simon'])[['rt']].std().round(2)
rt_min = data.groupby(['flankers', 'simon'])[['rt']].min().round(2)
rt_max = data.groupby(['flankers', 'simon'])[['rt']].max().round(2)
rt_median = data.groupby(['flankers', 'simon'])[['rt']].median().round(2)

#Arrange results in a table 
results = pd.DataFrame()
results['RT(std)'] = rt_std['rt']
results['RT(mean)'] = rt_mean['rt']
results['RT(min)'] = rt_min['rt']
results['RT(max)'] = rt_max['rt']
results['RT(median)'] = rt_median['rt']

results
```

![](Table.jpeg)
