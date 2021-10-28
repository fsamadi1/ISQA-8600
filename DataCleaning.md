# Data Cleaning Documentation

1. My research question addresses how Covid might have impacted certain services across different ages of participants. I used the columns program_name, duration and age from the HFS Service data. The program_name column contains three different services, which are: mental health, substance use and gambling. I am also using the columns duration and age. 

Dataset Description:

To access the data:

```
newdata=read.csv("/Users/fsamadi@unomaha.edu/Desktop/ISQA 8600/HFS Service Data.csv")
```

Program_name: This column contains three different programs which are: mental health, substance abuse gambling. There is one missing value in this column. There is a total of 8745 values in the data, and this column therefore contains 8744 values. There are 87 values for gambling, 6860 values for mental health and 1798 values for substance use. 

Duration: This column contains duration time during the service encounter. There are 29 missing values in this column. Therefore, this column contains 8718 values. 2813 values are recorded as 0:00, which means that there was no time spend during the programs. 

Age: This column contains the clients age at the time of service. There is one missing value in this column. Therefore, this column contains 8744 values. 

2.

3. Metadata: There are a few sources that we have used as metadata, which are the data dictionary, presenation slides as well as notes from lecture. The data to decisions presentation was useful to interpret into the project due to its helpful information about the background of Heartland Family Services. The HFS Program Summaries presentation slides have also been useful to understand more about the individual programs. The data dictionary was another great resource to better understand some aspects of the data. 

4. I have encountered missing values with the columns Program_name and duration. 

5. I am planning on omitting the missing values in the columns Program_name and duration. First, I will be checking the columns Program_name and duration for NAs. 

```
tibble_data %>% filter(program_name==NA) %>% count()
```
```
tibble_data %>% filter(duration==NA) %>% count()
```
The next step I took is to omit all the missing values in both columns with the function na.rm().


```
program_name %>% 
+     group_by(mentalhealth, substanceabuse, gambling) %>% 
+     summarise(mean = mean(program_name, na.rm = TRUE))
```

```
duration %>% 
+     group_by() %>% 
+     summarise(mean = mean(duration, na.rm = TRUE))

```



![Plot 1](Rplot01.png)

```
ggplot(data=newdata)+aes(x=duration, y=program_name)+geom_jitter()
```

- This plot shows a scatter plot of the duration of the different programs, such as Substance use, Mental health and Gambling. 




![Plot 3](Rplot03.png)

```
ggplot(data = newdata) + 
+     geom_bar(mapping = aes(x = duration))
```

- This is a bar chart that displays average duration of all services



