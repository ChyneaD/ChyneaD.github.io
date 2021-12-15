## Visualization of Data

#### One of the best things I have learned for processing data beyond looking at tables is how to use packages from seaborn to represent data as histograms, box plots, and bar plots.

##### An interesting feature of this is setting the background to different colours.


```
import seaborn as sns
#This is the line which makes a difference when plotting, by changing the style to 'dark' the graph as a unit stands at more, which would be useful for print in textbooks against a white page or screen. The 'whitegrid' style would be most useful in a graphical sense where you need to visually determine which points something may be located in relation to the bin number, it makes it easier to follow visually, especially for those how may have poor visual interpretation skills. The 'ticks' setting is another useful setting which may be less visually disruptive in presentation, but still provide better guidance as to where the bin locations are in relation to the spread of the data.
sns.set_style('white')

#The default is a histogram.
sns.displot(data=df, x='rt_ms', hue='flankers')
plt.show()
```

###### If a histogram isn't the best type of representation for your data, there are also code options for box plots and bar plots:


```
# Box plots and bar plots are changed very easily using matplotlib as you simply need to replace the phase kind='box' with kind='bar'
sns.catplot(kind='box',
           data=df,
           x='flankers', y='rt_ms')
plt.show()



![image](https://user-images.githubusercontent.com/94612613/146229133-e3b98035-bd1d-48cb-937d-f2e2eb143394.png)


sns.catplot(kind='bar',
           data=df,
           x='flankers', y='log_rt')

plt.show()


![Bar plot](https://user-images.githubusercontent.com/94612613/146230038-e7f04f13-02bd-4151-9ba6-794ba6f1d961.png)

```
