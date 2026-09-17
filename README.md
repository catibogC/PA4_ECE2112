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

