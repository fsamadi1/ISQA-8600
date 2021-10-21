# Data Exploration
This is an open source license

{Data Entry Analysis} and {Data Exploration} 

[Visit DataEntryAnalysis!](www.github.com)

[Visit DataExploration!](www.github.com)

![Plot 1](Rplot01.png)

```
ggplot(data=newdata)+aes(x=duration, y=program_name)+geom_jitter()
```

![Plot 2](Rplot02.png)

```
 ggplot(data = newdata) + 
+     geom_point(mapping = aes(x = duration, y = age)) + 
+     facet_wrap(~ program_name, nrow = 2)
```

![Plot 3](Rplot03.png)

```
ggplot(data = newdata) + 
+     geom_bar(mapping = aes(x = duration))
```


```
ggplot(data = newdata) + 
+     geom_point(mapping = aes(x = duration, y = age, color = program_name))
```
