# Data Cleaning Documentation

1. My research question addresses how Covid might have impacted certain services across different ages of participants. I used the columns program_name, duration and age from the HFS Service data. The program_name column contains three different services, which are: mental health, substance use and gambling. I am also using the columns duration and age. 

Dataset Description:

To access the data:

```
newdata=read.csv("/Users/fsamadi@unomaha.edu/Desktop/ISQA 8600/HFS Service Data.csv")
```

Program_name: This column contains three different programs which are: mental health, substance abuse gambling. There is one missing value in this column. There is a total of 8745 values in the data, and this column therefore contains 8744 values. 

Duration: This column contains duration time during the service encounter. There are 29 missing values in this column. Therefore, this column contains 8718 values. 

Age: This column contains the clients age at the time of service. There is one missing value in this column. Therefore, this column contains 8744 values. 

2.

3. Metadata: There are a few sources that we have used as metadata, which are the data dictionary, presenation slides as well as notes from lecture. The data to decisions presentation was useful to interpret into the project due to its helpful information about the background of Heartland Family Services. The HFS Program Summaries presentation slides have also been useful to understand more about the individual programs. The data dictionary was another great resource to better understand some aspects of the data. 

4. I have encountered missing values with the columns Program_name and duration. 




























![Plot 1](Rplot01.png)

```
ggplot(data=newdata)+aes(x=duration, y=program_name)+geom_jitter()
```

- This plot shows a scatter plot of the duration of the different programs, such as Substance use, Mental health and Gambling. 


![Plot 2](Rplot02.png)

```
 ggplot(data = newdata) + 
+     geom_point(mapping = aes(x = duration, y = age)) + 
+     facet_wrap(~ program_name, nrow = 2)
```

- This is a facet plot which shows duration of the three different programs in relation to age


![Plot 3](Rplot03.png)

```
ggplot(data = newdata) + 
+     geom_bar(mapping = aes(x = duration))
```

- This is a bar chart that displays average duration of all services


![Plot 4](Rplot04.png)

```
ggplot(data = newdata) + 
+     geom_point(mapping = aes(x = duration, y = age, color = program_name))
```

- Plot 4 contains three variables, which are duration, age and program name. Each program name is represented in a different color 
