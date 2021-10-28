# Data Cleaning Documentation

My research question addresses how Covid might have impacted certain services across different ages of participants. I used the columns program_name, duration and age from the HFS Service data. The program_name column contains three different services, which are: mental health, substance use and gambling. I am also using the columns duration and age. 

Dataset Description:

To access the data:

```
newdata=read.csv("/Users/fsamadi@unomaha.edu/Desktop/ISQA 8600/HFS Service Data.csv")
```

Program_name: This column contains three different programs which are: mental health, substance abuse gambling. There is no missing values in this column. There is a total of 8745 values in the data. There are 87 values for gambling, 6860 values for mental health and 1798 values for substance use.


```
table(newdata$program_name)
```

     Gambling Mental Health Substance Use 
           87          6860          1798 


Duration: This column contains duration time during the service encounter. There are 28 missing values in this column. Therefore, this column contains 8719 values. 2813 values are recorded as 0:00, which means that there was no time spend during the programs. 

```
table(newdata$duration)
```

       0:00  0:01  0:02  0:03  0:04  0:05  0:06  0:07  0:08  0:09  0:10 
   28  2813    59    37    20    15    83     5     9     3     6    82 
 0:11  0:12  0:13  0:14  0:15  0:16  0:17  0:18  0:19  0:20  0:21  0:22 
    5     8     3     4   129     7     7    12     3    60     7    28 
 0:23  0:24  0:25  0:26  0:27  0:28  0:29  0:30  0:31  0:32  0:33  0:34 
   12     7    47     8     9     9     8   252    18    23    19    17 
 0:35  0:36  0:37  0:38  0:39  0:40  0:41  0:42  0:43  0:44  0:45  0:46 
   60    16    13    15    13    76    25    23    37    33  1182   120 
 0:47  0:48  0:49  0:50  0:51  0:52  0:53  0:54  0:55  0:56  0:57  0:58 
  130   119    84   853    98    62    17     6    31     2     7     6 
 0:59  1:00  1:01  1:02  1:03  1:05  1:07  1:09  1:10  1:11  1:12  1:13 
   16   938     1     2     2     1     1     5     3     1     1     1 
 1:15  1:17  1:18  1:19  1:20  1:23  1:24  1:25  1:27  1:30  1:32  1:33 
    8     1     2     2     3     2     2     2     2   426     1     1 
 1:36  1:37  1:40  1:45  1:46  1:48  1:49  1:50  1:55  1:56  1:58 11:40 
    1     4     1     5     1     2     1     1     1     1     2     1 
12:00  2:00  2:30  2:40 
    1   407     1     1 



Age: This column contains the clients age at the time of service. There is no missing value in this column. Therefore, this column contains 8745 values. 

```
 table(newdata$age)
 ```

  1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17  18 
  3  25  21  28  49 155 201 123 179 276 311 195 420 283 169 101 117 174 
 19  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34  35  36 
 63  57  96 184 113 126 185 375 164 199 197 359 231 220 132 133 273  44 
 37  38  39  40  41  42  43  44  45  46  47  48  49  50  51  52  53  54 
114 182 160 195  61 209 239 202 102  39  96 121  81  80  93  35  93  56 
 55  56  57  58  59  60  61  62  63  64  65  66  67  71  72 
 61  33  60 127  89  28  44   6   8  78  35   5  17   6   9 










Metadata: There are a few sources that we have used as metadata, which are the data dictionary, presenation slides as well as notes from lecture. The data to decisions presentation was useful to interpret into the project due to its helpful information about the background of Heartland Family Services. The HFS Program Summaries presentation slides have also been useful to understand more about the individual programs. The data dictionary was another great resource to better understand some aspects of the data. 

I have encountered missing values with the columns duration. 

I am planning on omitting the missing values in the columns that contain them. First, I will be checking the columns Program_name, duration and age for missing values. 

```
newdata %>% filter(program_name=="") %>% count()

```

```
newdata %>% filter(duration=="") %>% count()

```

```
newdata %>% filter(age=="") %>% count()
```



newdata %>% filter(duration=="") %>% count()
 n
1 28


newdata %>% filter(program_name=="") %>% count()
  n
1 0


newdata %>% filter(age=="") %>% count()
  n
1 0








The next step I took is to omit all the missing values in both columns with the function na.rm().



```
newdata <-  newdata %>% filter(duration!="") 

```


```
newdata <-  newdata %>% filter(age!="") 

```


```
newdata <-  newdata %>% filter(program_name!="") 

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



