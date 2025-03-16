# Project: Customer Feedback Management System


"This notebook demonstrates the process of collecting, storing, and analyzing customer feedback data using Python, pandas, and CSV operations."


## Step 1: Set Up the Environment.
    First, we need to import the necessary libraries.


```python
import pandas as pd
import csv
```

## Step 2: Collect Customer Feedback Data
     we'll collect feedback from 5 customers. For each customer, we'll gather their name, rating, and feedback.

     - Use `input()` to get user input for each piece of data.
     - Convert the rating to an integer using `int()`.
     - Repeat this process for all 5 customers.
     


```python
#data for first customer
customer_name1=input("first customer's name")
customer_rating1=int(input('first customer rating(1-5)'))
customer_feedback1=input('first customer feedback')
#data for second customer
customer_name2=input("second customer's name")
customer_rating2=int(input('second customer rating(1-5)'))
customer_feedback2=input('second customer feedback')
#data for third customer
customer_name3=input("third customer's name")
customer_rating3=int(input('third customer rating(1-5)'))
customer_feedback3=input('third customer feedback')
#data for fourth customer
customer_name4=input("fourth customer's name")
customer_rating4=int(input('fourth customer rating(1-5)'))
customer_feedback4=input('fourth customer feedback')
#data for fifth customer
customer_name5=input("fifth customer's name")
customer_rating5=int(input('fifthcustomer rating(1-5)'))
customer_feedback5=input('fifthcustomer feedback')
```

## Step 3: Store Data in a CSV File.

    Now that we are going to collect the data, and store it in a CSV file for easy access and analysis.

    - Use csv module
    - Open a new file named 'customer_feedback.csv' in write mode.
    - Use `csv.writer()` to create a writer object.
    - Write the header row first, then data for each customer.
    - The `with` statement ensures the file is properly closed after writing.
   
    
    


```python
#open a new file named "customer_feedback.csv" in write mode
with open('customer_feedback.csv', 'w', newline='') as file:
    # instantiate writer object
    writer=csv.writer(file)
    #write header row first
    writer.writerow(['Name', 'Rating', 'feedback'])
    #data for eah customer
    writer.writerow([customer_name1, customer_rating1, customer_feedback1])
    writer.writerow([customer_name2, customer_rating2, customer_feedback2])
    writer.writerow([customer_name3, customer_rating3, customer_feedback3])
    writer.writerow([customer_name4, customer_rating4, customer_feedback4])
    writer.writerow([customer_name5, customer_rating5, customer_feedback5])
```

 ## Step 4: Read and Display Data using pandas
    
    Let's read the CSV file we just created and display its contents using pandas.
  
    - Use `pd.read_csv()` to read the CSV file into a pandas DataFrame.
    - Display the DataFrame to see all the collected customer feedback data in a tabular format.


```python
#import csv file we created above
df=pd.read_csv('customer_feedback.csv')
#use info() to display details of the dataframe
print(df.info)
# display first five row by using head()
df.head()

```

## Step 5: Data Analysis
    Now that we have our data in a DataFrame, we can perform various analyses.
   
    - Use the `mean()` function on the 'Rating' column to calculate the average rating.
    - Or the 'sum() and len()' and use division operator
    - Format the result to display with two decimal places.
    


```python
# average=sum of numbers/count items
total_number_of_rating=df['Rating'].sum()
print(f'sum of rating is {total_number_of_rating}')

#the number of items 
num_items=len(df['Rating'])
print(f'the number of items are {num_items}')

# average of rating
average=total_number_of_rating/num_items
print(f'Average of rating is {average}')
```


```python
#this is the second way
df['Rating'].mean()
```

 ### Categorize Feedback
 
     Use conditional statements to determine the feedback category based on rating and keywords.



```python
#customer 1
if customer_rating1 >=4 and 'excellent' in customer_feedback1.lower():
    feedback_category= 'Very positive'
elif customer_rating1>=4:
    feedback_category='positive'
elif customer_rating1==3:
    feedback_category= 'Neutral'
elif customer_rating1<3:
    feedback_category='negative'
print(f'category feeedback for customer1: {feedback_category}')
#customer 2
if customer_rating2 >=4 and 'excellent' in customer_feedback2.lower():
    feedback_category= 'Very positive'
elif customer_rating2>=4:
    feedback_category='positive'
elif customer_rating2==3:
    feedback_category= 'Neutral'
elif customer_rating2<3:
    feedback_category='negative'
print(f'category feeedback for customer2: {feedback_category}')
#customer3
if customer_rating3 >=4 and 'excellent' in customer_feedback3.lower():
    feedback_category= 'Very positive'
elif customer_rating3>=4:
    feedback_category='positive'
elif customer_rating3==3:
    feedback_category= 'Neutral'
elif customer_rating3<3:
    feedback_category='negative'
print(f'category_feeedback for customer3: {feedback_category}')
#customer 4
if customer_rating4 >=4 and 'excellent' in customer_feedback4.lower():
    feedback_category= 'Very positive'
elif customer_rating4>=4:
    feedback_category='positive'
elif customer_rating4==3:
    feedback_category= 'Neutral'
elif customer_rating4<3:
    feedback_category='negative'
print(f'category_feeedback for customer4: {feedback_category}')
#customer 5
if customer_rating5 >=4 and 'excellent' in customer_feedback5.lower():
    
    feedback_category= 'Very positive'
elif customer_rating5>=4:
    feedback_category='positive'
elif customer_rating5==3:
    feedback_category= 'Neutral'
elif customer_rating5<3:
    feedback_category='negative'
print(f'category_feeedback for customer5: {feedback_category}')
```

### Step 5: Analyzing Feedback Comments
        Use lower(), split() and count() 


```python
#use lower() to convert all customer in put feedback to lower case the split words in sentence 
#delineator will be space between words in sentence

# first customer
feedback_word1= customer_feedback1.lower().split()

#second customer
feedback_word2= customer_feedback2.lower().split()

#third customer
feedback_word3= customer_feedback3.lower().split()

#fourth customer
feedback_word4= customer_feedback4.lower().split()

#fifth customer
feedback_word5= customer_feedback5.lower().split()


print(f'feedback_word1= {feedback_word1}')
print(f'feedback_word2= {feedback_word2}')
print(f'feedback_word3= {feedback_word3}')
print(f'feedback_word4= {feedback_word4}')
print(f'feedback_word5= {feedback_word5}')
```


```python
#counting occurrence of word 'sevice'
word_to_count='service'
word_count1=feedback_word1.count(word_to_count)
word_count2=feedback_word2.count(word_to_count)
word_count3=feedback_word3.count(word_to_count)
word_count4=feedback_word4.count(word_to_count)
word_count5=feedback_word5.count(word_to_count)
#print eah count
print(f"count of '{word_to_count}' in first feedback:", word_count1)
print(f"count of '{word_to_count}' in first feedback:", word_count2)
print(f"count of '{word_to_count}' in first feedback:", word_count3)
print(f"count of '{word_to_count}' in first feedback:", word_count4)
print(f"count of '{word_to_count}' in first feedback:", word_count5)
```
