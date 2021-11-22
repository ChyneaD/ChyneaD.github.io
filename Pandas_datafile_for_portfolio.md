## Working with Pandas Dataframes

So, one of my preferred things I've done was a chunk of code that I created while trying to clean up some neuropsychological data, and work with it in a way that it was usable. For me, this meant getting rid of participants who left, grouping conditions, and creating dataframes from our new conditions based on sex. I think this is likely a common process which would need to be done for a lot of studies, especially behavioural studies where it's possible to find large sex differences. 


```python
import pandas as pd

#Read in a csv file 
df= pd.read_csv('EFData.csv', sep=';')

#Preserving only the participants who did not drop out of the study, whom were eligible to use for data analyses later
df= df[df.dropout==0]

#Figuring out the sex of participants from the description in the study, girls(48) and boys(46)- The sum of the sex column is 46, meaning we have the value of 1 added together from 46 rows, which means there value 1 is associated with the gender of boy.
df['sex'].sum()
#Age is in months since we're evaluating executive function of children in a development period where months can mean a lot of difference in performance


df1 = df[df.group ==1]
df2 = df[df.group ==2]
df3 = df[df.group ==3]
```

##### As you can see, an important part of going through the initial coding stages is using code to make data interpretable, like assigning binary coding to binary sex (0=girl, 1=boy)


```python
#In the last step, we got the groups separated by experiment condition/group number. 
#Now we're going to separate the groups by sex so we can run some tests and see if there is a difference in scores between the sexes, and between conditions
df1Boys = df1[df1.sex ==1]

means1Boys = df1Boys[['age', 'part_training', 'practice_minutes', 'education_parents', 'income_parents', 'iq', 'leisure_activities', 'agtb_mx_t0', 'agtb_mx_t1', 'agtb_cb_t0', 'agtb_cb_t1', 'inhibition_t0', 'inhibition_t1', 'auditory_attention_t0', 'auditory_attention_t1', 'design_fluency_t0', 'design_fluency_t1', 'animal_sorting_t0', 'animal_sorting_t1', 'clocks_t0', 'clocks_t1', 'bfie', 'bfia', 'bfic', 'bifn', 'bfio']].mean(axis=0)
```

    /tmp/ipykernel_1111/2900140135.py:5: FutureWarning: Dropping of nuisance columns in DataFrame reductions (with 'numeric_only=None') is deprecated; in a future version this will raise TypeError.  Select only valid columns before calling the reduction.
      means1Boys = df1Boys[['age', 'part_training', 'practice_minutes', 'education_parents', 'income_parents', 'iq', 'leisure_activities', 'agtb_mx_t0', 'agtb_mx_t1', 'agtb_cb_t0', 'agtb_cb_t1', 'inhibition_t0', 'inhibition_t1', 'auditory_attention_t0', 'auditory_attention_t1', 'design_fluency_t0', 'design_fluency_t1', 'animal_sorting_t0', 'animal_sorting_t1', 'clocks_t0', 'clocks_t1', 'bfie', 'bfia', 'bfic', 'bifn', 'bfio']].mean(axis=0)



```python
meanboysdf= pd.DataFrame(means1Boys).T
meanboysdf.index.names = ['meansforgroup']
```

##### Now, we would repeat the process we see in the beginning of my code until this last chunk above for the next two male groups were going to use for the dataframe.


```python
#We're going to save the new data as meanboysdfincom- you don't need this to be runnable in its entirety, this is just to showcase how you would use code in a similar way when processing your own data.
meanboysdfincom = meanboysdf.append(meanboys2df)
#Append the last of the new dataframes, under the new name MeanBoysDFCom Meaning MeanBoysDataframeComplete
meanboysdfcom= meanboysdfincom.append(meanboys3df)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    /tmp/ipykernel_1111/54715990.py in <module>
          1 #We're going to save the new
    ----> 2 MeanBoysDFIncom = MeanBoysDF.append(MeanBoys2DF)
          3 #Append the last of the new dataframes, under the new name MeanBoysDFCom Meaning MeanBoysDataframeComplete
          4 MeanBoysDFCom= MeanBoysDFIncom.append(MeanBoys3DF)


    NameError: name 'MeanBoys2DF' is not defined


###### Ignore the errors here, for brevity sake, the entire code isn't included which is leading to errors. The structure of the code is most important for adapting it for use.
