### Loop Example

Here is an example of a loop that I wrote to read in participant data files and then calculate means for two levels of a variable for each partcipant.


```python
for id in IDs :
    
    part = pd.read_csv(id+'.csv')
    part.rt = part.rt * 1000

    con = part['flankers']=='congruent'
    part_con = part[con]
    part_con_mean = part_con.loc[:, 'rt'].mean()

    incon = part['flankers']=='incongruent'
    part_incon = part[incon]
    part_incon_mean = part_incon.loc[:, 'rt'].mean()

    print("The partcipant ID is " + id + "." + " Mean RT for the congruent condition is " + str(part_con_mean) + " ms. Mean RT for the incongruent condition is " + str(part_incon_mean) + " ms.")
```
