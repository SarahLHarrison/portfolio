### Seaborn Bar Plot

In this example, I caulated the error rate by condition of experiment. I then plotted the error rates of all four conditions on a well formatted barplot, using Seaborn.


```python
#total number of trials per group
total = data.groupby(['flankers', 'simon'])[['error']].count()

#number of error trials per group
errors = data.groupby(['flankers', 'simon'])[['error']].sum()

#calculate error rate
error_rate = ((errors / total) *100).round(2)
error_rate = error_rate.reset_index()

#plot bar plot of error rate per group
sns.set_palette(pal)
sns.set_style('whitegrid')

g = sns.barplot(x='flankers', y='error', hue='simon', data=error_rate )

g.set_title('Error Rate per Condition (Figure 3)', fontsize=18)
g.set_xlabel('Flankers', fontsize=15)
g.set_ylabel('% Error trials', fontsize=15)
g.set_xticklabels(['Congruent', 'Incongruent'], fontsize=12)
h, l = fig3.get_legend_handles_labels()
labels=['Congruent', 'Incongruent']
g.legend(h, labels, title='Simon')
```
