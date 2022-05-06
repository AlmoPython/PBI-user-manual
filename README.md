# PBI-user-manual
## Import file into PBI Desktop Version
   If just import simple excel or csv file, we can just select the Import function and select the version of the file we want to import. 
   But if we want to import from **SQL database**, then : 
   
![在这里插入图片描述](https://img-blog.csdnimg.cn/9667d078124245d6bb78e0fb736bdb48.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LiA5Liq6IKJ5YyF,size_15,color_FFFFFF,t_70,g_se,x_16#pic_center)

just select SQL Server, then you can put the credentials of your SQL into it, and the connection will be completed.
There are also other resources that PBI can connect to, you can simply just choose from here: 

![在这里插入图片描述](https://img-blog.csdnimg.cn/3fafb00c81f84949a00909dbfe0f2a5d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LiA5Liq6IKJ5YyF,size_16,color_FFFFFF,t_70,g_se,x_16#pic_center)

then you will see the resource list: 

![在这里插入图片描述](https://img-blog.csdnimg.cn/d36860df7c55463d848c2fb6bd8ed706.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LiA5Liq6IKJ5YyF,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

## Different Kind of Charts that We Usually Use

1. Table : 

	![在这里插入图片描述](https://img-blog.csdnimg.cn/60c2b508500f48eba1914516e2d9a5cf.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LiA5Liq6IKJ5YyF,size_18,color_FFFFFF,t_70,g_se,x_16)
  
	2. Metrix/Pivot Table
	
	![在这里插入图片描述](https://img-blog.csdnimg.cn/206838c6546b4444830ce2f6811e64ee.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LiA5Liq6IKJ5YyF,size_17,color_FFFFFF,t_70,g_se,x_16)
  
 3 Slicer :
 
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/0518eda73434484996b9923f84daac8c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LiA5Liq6IKJ5YyF,size_12,color_FFFFFF,t_70,g_se,x_16)

## Relationships between tables in PBI

![在这里插入图片描述](https://img-blog.csdnimg.cn/9cdc56f27ede4ed3a0e0594d9dfe3f7d.png)

Sometimes we need tables that are from different sources in one tab, but the filter cannot filter both table, then we can use this relationship tab, to connect all sources using the table that only has one column -- which is the same column that we want to filter. now you can put the 'brand name' column in to the filter section, then when you choose a brand, all tables will change. 
This is really important in building complex PBI tabs. 

[https://docs.microsoft.com/en-us/power-bi/transform-model/desktop-create-and-manage-relationships](https://docs.microsoft.com/en-us/power-bi/transform-model/desktop-create-and-manage-relationships)
Here is the detailed doc for the relationships. 

## DAX language in PBI

I only list the one that I have used and I think it is pretty important to know, will add more as I work on it more. 

1. Simple sum

     sum(table[column]), the important thing is that when you want to use a column for further calculation, like in dividing or a function, you need to us sum of that column, you cannot just use that column directly.  I will put an example here. 
     
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/8aec8c319429434c9c630df6c5849505.png)
    
2. IFERROR

    This is a function that will make your calculation more clean. if we don't add it when doing a calculation, especially a dividing, there will be "NaN", "infinite" show up in the table. We usually don't want this. So we can let PBI know that if these characters show up, change it to 0 or null. I usually change it to 0. I will put an example here
    
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/ac1065ce7f47410abbb364686e59c557.png)

3. Basic Calculation

    There are different calculations that we can do using DAX. The basic will just be : add, substract, times and divide. 
    Here I will put the function below. 
    
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/c60eb55b196a4cb0bed4abf4071283ba.png)
    
4. Quick Measure

	Sometimes the DAX function can be a little tricky to write, so PBI prepared some quick measure for us so that we don't need to write the code ourselves. And YOY percentage change is one of them that I used very often during the dashboard building. 
  
	![在这里插入图片描述](https://img-blog.csdnimg.cn/0b01488b69a948888f86369c16e60101.png)
  
	There are lots of quick measures that we can use, and one thing that we need to keep in mind if you use YOY quick measure, is that the Date field needs to be a ***specific date***, you cannot use Year column or Month column as the Date, and this is the most important factor in calculation date comparison measures. 
  
5. Filter

    Filter function is an important function that can help you with filtering the data within a table. 
    For example I have a table that has columns like sales, year, month, brand. I want to make two different table in a tab, one is to show the data that has sales > $1000 in year 2022, and another one is to show the data that has sales < $1000 in year 2022. 
    Then we can use Filter function , which will create a sub table, which will satisfy the requirement, and then you can use this sub table to create a table visual in the tab. 
here is the syntax:

![在这里插入图片描述](https://img-blog.csdnimg.cn/247c90801de646ee834ebe65e64e2de1.png)

and here is an example i made:

![在这里插入图片描述](https://img-blog.csdnimg.cn/597d846459604435a4b46be6bac6870f.png)



## Things that need to pay attention to
1. Total calculation
2. 
