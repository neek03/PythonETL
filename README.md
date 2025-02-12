# PythonETL
ETL using Python - test



Prerequisites
Python. 
A Windows PowerShell. 
A working MongoDB database.

Here are some basic examples of using Python for ETL (Extract, Transform, Load) tasks. These scripts extract data from various sources, transform the data, and then load it into a target system like a database or file.

Example 1: Extracting Data from a CSV File, Transforming, and Loading into Another CSV File

1. Extract Data from CSV

import pandas as pd

# Extract data from a CSV file
data = pd.read_csv('input_data.csv')
print(data.head())  # Display first few rows of data


2. Transform Data

# Example transformation: Add a new column with modified data
data['Total'] = data['Quantity'] * data['UnitPrice']


USING MONGOdb
Step 1: Install & Import Required Packages
Importing the right libraries is the first step toward creating anything using Python. This step includes using two libraries to make an ETL pipeline: pandas and pymongo. To achieve this task, type the following code in the command line:


pip install pandas pymongo

The pandas library can be used to transform and manipulate data, and the pymongo library helps interact with MongoDB in a Python project. 

Step 2: Extracting Data from Source
The extraction process in Python varies based on the data source. A data source could include a database, flat file, CSV file, API, or an application. As mentioned above, this method involves extracting data from the CSV file in this ETL pipeline. Make a file named etl.py in your local machine and paste the code below to perform this task:


Import pandas as pd 
from pymongo import MongoClient

data = pd.read_csv(‘your_csv_file.csv’)

In the above code, the pandas library is imported, and the data from your_csv_file.csv is saved into the data variable.

Step 3: Transforming Data in Required Format
In this step, you will transform data in format and sequence according to your requirements. With Python’s modern syntax and pandas' data transformation functionalities like aggregation and manipulation, there is a lot of scope for enhancing datasets. Below are some examples of the basic transformations with CSV data using Python: 

Sort and Filter
One common use case when transforming is ordering data. To do this, you can use methods like sort_valuesand filter from the pandas library. Here’s how to use these methods:


#Sort by filter
sorted = data.sort_values(by=[‘name’])

#Filter columns
just_filters = data.filter([‘name’, ‘is_student’, ‘target’])

In the above code, a hypothetical example is given as a name in the sort_values method to sort the name field alphabetically from the data stored in the CSV file. However, in the filter method, you can provide specific columns in this example (name, is_student, target), and only those columns will appear in the results. 

Removing Duplicates
A common challenge in raw datasets is duplicate rows of data. The code below demonstrates finding and removing duplicates using the drop_duplicate method of the pandas library:


#Remove duplicates
remove_dups = data.drop_duplicates()

Above are the two common examples of basic transformations of Python ETL. You can choose to perform more transformation practices according to your requirements.

Step 4: Loading Data in MongoDB
This is the most technical step of the ETL process. However, if you have a basic working knowledge of Python, you’ll be fine. Here’s how to load the CSV data to MongoDB with Python:

First, you must connect MongoDB to Python:


mongoClient = MongoClient(‘MongoDB Atlas URL with port’) 
db = mongoClient['your_database'] 
collection = db['your_collection']

In the above code, replace your_database with the name of your MongoDB database and your_collection with the collection name. 

To copy the CSV data to MongoDB, you must use the to_dict method of pandas and create JSON data (list of dictionaries) for inserting multiple records in MongoDB. Here’s the code: 


jsondata = data.to_dict(orient='records')
collection.insert_many(jsondata)

Complete Code for Python ETL 
Here is the complete code for the Python ETL pipeline you created. You can use Python IDE’s like Jupyter Notebook to execute this command:


Import pandas as pd 
from pymongo import MongoClient

data = pd.read_csv(‘your_csv_file.csv’)

mongoClient = MongoClient(‘MongoDB Atlas URL with port’) 
db = mongoClient['your_database'] 
collection = db['your_collection']

jsondata = data.to_dict(orient='records')
collection.insert_many(jsondata)

Note: The above code does not involve transformation to the CSV file before loading, as it depends on your specific requirements.

That's it. If you carefully follow the steps mentioned above, you can create a basic Python ETL framework to migrate data from the CSV file to MongoDB. 


