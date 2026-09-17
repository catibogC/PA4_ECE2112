# PA4_ECE2112

Christian Victor S. Catibog

2ECE-D

---

Please take note that the following code was used in order to access the Pandas library.

    import pandas as pd

To import the .xlsx file into the notebook, make sure to put the .xlsx and .ipynb files in the same folder and type the following code.

    df = pd.read_excel('board2.xlsx')

Additionally, the given file does not contain an Average column. To make a new column 'Average', indicate that you will add all the values in columns 'Math', 'Electronics', 'GEAS', and 'Communication', and divide their sum by 4. The following code should be ressembled.

    df['Average'] = (df['Math']+df['Electronics']+df['GEAS']+df['Communication']) / 4

---

## A. VISAYAS COMMUNICATION DATAFRAME

**Objective:** The objective of this problem is to create a DataFrame containing students whose Hometown is Visayas and whose Track is Communication. Additionally, columns 'Name', 'Gender', 'Math', 'Electronics', and 'Average' are the only columns that should be retained.

**Discussion:**

Using the .loc function, I created a Boolean index wherein it only calls out rows whose 'Hometown' is Visayas and whose 'Track' is Communication. Then, I indicated which columns should be called out for the new DataFrame. The new DataFrame was named VisComm. The final code is as follows.

    VisComm = df.loc[(df['Hometown']=='Visayas')&(df['Track']=='Communication'), 
                     ['Name', 'Gender', 'Math', 'Electronics', 'Average']]

With this, I was able to create the required DataFrame.

---

## B. VISAYAS FEMALE DATAFRAME

**Objective:** 

The objective of this problem is similar to the previous problem. Here, I should create a new DataFrame containing students whose Hometown is Visayas and whose Gender is Female. Additionally, columns 'Name', 'Track', 'GEAS', 'Electronics', and 'Average' are the only columns that should be retained.

However, unlike the previous problem, without overriding the newly created DataFrame, I should only display rows whose average is at least 60.

**Discussion**


