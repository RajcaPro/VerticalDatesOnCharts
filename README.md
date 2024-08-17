# Vertical Dates On Charts
In this post, we'll learn how to handle the situation when our dates on the X-axis don't fit horizontally and stand on a diagonal!  
Example:

![image](https://github.com/user-attachments/assets/8b90800d-ae4a-4861-817e-25687c1d5a0b)

Get to it:) 🚀

For the purpose of this assignment, let's look at a few key points.
1) The chart is : Cumulative column chart
2) On the X axis, we want to display the data by year and month -> YearMonth
3) On the Y axis we show Total Sales
4) In the legend we insert the product brand categories.
In the example there are two brands : own brand and external brand.

Result of action :

![image](https://github.com/user-attachments/assets/697909e1-d6fc-47e7-b81b-0840455ca485)

At first glance, you may notice that the way the dates are presented diagonally takes the report user more time to read the data correctly.
This is tiresome when working with the chart for a longer period of time.
Let's fix it!

---------------------------------------------------------------------------------------------------------

The first step we need to take is to go into Power Query and then into our Calendar table.

![image](https://github.com/user-attachments/assets/e6975ecc-8454-405f-b854-55157d0f2d4d)

As you can see the way our columns are written is horizontal.
Let's also point out the fact that each record is on a single line.

And what if I told you that it is possible to perform the operation “shift + Enter”, which transports us to the second line of the line in the same record ?
Such situations occur every day in conversations conducted through instant messaging .

Example :

![image](https://github.com/user-attachments/assets/9be42b7c-b990-4a5f-bded-1b182d7eb5f4)

The question is how to do it in Power Query ?

First, we need to add a new column in the Calendar table : by selecting “Custom Column” in the “Add Column” section.

Result : 

![image](https://github.com/user-attachments/assets/3d7db324-04b2-46a5-afa7-9ede5032d91e)

Creating a Custom Column allows us to write M-Code to perform this operation !

The following M code allows us to perform this operation!

Result:

![image](https://github.com/user-attachments/assets/5d7d1c46-56c5-420b-9074-50a38ba2ccf8)

Now let's explain how this code works!✨


This code in the M language in Power Query converts values from the [Year] and [Date] columns to text and then concatenates them into a single string. Here's a step-by-step explanation of how it works:

1. Text.From([Year])
[Year]: This is a column or field in the table that contains the year value, most likely in a numeric format.
Text.From([Year]): This function converts the numeric value from the [Year] column to text. For example, if the value in the [Year] column is 2024, the result of this operation will be "2024" (as text).
------
2. "#(lf)"
"#(lf)": This is a special code in the M language that represents a new line character (line feed).
Using this code inserts a new line between two parts of the text, which causes the next element after "#(lf)" to appear on a new line.
------
3. Date.ToText([Date], "MMM")
[Date]: This is a column or field in the table that contains a date value in a date format.
Date.ToText([Date], "MMM"): This function converts the date value to text but only in the three-month format, meaning it returns the abbreviated name of the month from that date. For example, if the date in [Date] is 15th August 2024, the result of this operation will be "Aug".
------
4. Text.From([Year]) & "#(lf)" & Date.ToText([Date], "MMM")
&: This operator concatenates two or more text strings into one string.
The result of this operation will be a combination of the text version of the year (from [Year]), the new line character, and the text version of the month (from [Date]). 


Result: 

![image](https://github.com/user-attachments/assets/cd2de5f7-87f0-4757-9d64-7d478a5286ea)

Let's save our operation and select the newly created column for our chart !

RESULT: 

![image](https://github.com/user-attachments/assets/c77e14cc-bde2-4d0f-9141-b1c0ba5df21f)


Everything works! ✨ This is the end of this guide !

I hope you will use it in your work 🚀

Best Regards,
Mateusz Rajca
