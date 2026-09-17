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

Using the .loc function, I created a Boolean index that selects rows where 'Hometown' is Visayas and 'Track' is Communication. Then, I indicated which columns should be called out for the new DataFrame. The new DataFrame was named VisComm. The final code is as follows.

    VisComm = df.loc[(df['Hometown']=='Visayas')&(df['Track']=='Communication'), 
                     ['Name', 'Gender', 'Math', 'Electronics', 'Average']]

With this, I was able to create the required DataFrame.

---

## B. VISAYAS FEMALE DATAFRAME

**Objective:** 

The objective of this problem is similar to the previous problem. Here, I should create a new DataFrame containing students whose Hometown is Visayas and whose Gender is Female. Additionally, columns 'Name', 'Track', 'GEAS', 'Electronics', and 'Average' are the only columns that should be retained.

However, unlike the previous problem, without overriding the newly created DataFrame, I should only display rows whose average is at least 60.

**Discussion**

For the first part of this problem, I essentially did the same thing I did for the previous problem, albeit with a few tweaks as instead of Track, we are referring to Gender, and some columns were replaced and some were added. The new DataFrame was named VisFemale. The code is as follows.

    VisFemale = df.loc[(df['Hometown']=='Visayas')&(df['Gender']=='Female'), 
                       ['Name', 'Track', 'GEAS', 'Electronics', 'Average']]

To call out rows from the VisFemale dataset whose averages are at least 60, I made use of the .loc function and created a Boolean index that calls out the rows that are greater than or equal to 60. The code is as follows.

    VisFemale.loc[VisFemale['Average'] >= 60]

With this, I was able to satisfy what was needed from the problem.

---

## C. CATEGORY-AVERAGE VISUALIZATION

**Objectives:**

The objective of this problem is to "examine how the recorded Average differs across the three categorical features Track, Gender, and Hometown".

This problem consists of 4 different parts.
- a. Using Pandas, I should compute for the mean of Average for every category. 
- b. I should display three summary tables that shows the mean of the Averages for each Track, Gender, and Hometown.
- c. I should then create a single figure showing bar graphs of the mean Average by Track, Gender, and Hometown.
- d. Lastly, under the figure, I should write three statements indicating the highest category for each feature.

**Discussion:**

**A.**

To get the mean of Average for every category, I made use of the .groupby function wherein I called out the categories of each of the aforementioned columns and I got the means of their averages. In preparation for Part B., the DataFrame names 'tracksummary', 'gendersummary', and 'hometownsummary' were used for each respective category. The codes I wrote for each column is as follows.

    tracksummary = df.groupby('Track')['Average'].mean().reset_index()
    gendersummary = df.groupby('Gender')['Average'].mean().reset_index()
    hometownsummary = df.groupby('Hometown')['Average'].mean().reset_index()

**B.**

To display the summary tables, I used the display(DataFrameName) function and passed the DataFrame names I created in Part A.

    display(tracksummary)
    display(gendersummary)
    display(hometownsummary)

**C.**

To create the figure, I first imported the matplotlib.pyplot library using the following code.

    import matplotlib.pyplot as plt

Upon setting up the figure, I made it show three graphs in a single row. I also changed the size of my figure so it would fit in the notebook. The following code was written to set up the figure.

    fig, axes = plt.subplots(1, 3, figsize = (15, 5))

To create the different bar graphs, I used the .bar function. Within the .bar function, I set the categories to represent the horizontal axis, with Average on the vertical axis. I also called out the DataFrames I made in Part A. The following code was written to set up the bar graphs.

    axes[0].bar(tracksummary['Track'], tracksummary['Average'])
    axes[1].bar(gendersummary['Gender'], gendersummary['Average'])
    axes[2].bar(hometownsummary['Hometown'], hometownsummary['Average'])

**D.**

To add statements under the figure, I made use of the .text function. Here, I mentioned the category with the highest mean for Average, and to place them below the figure, I set the x-values for each to 0 and assigned each statement its respective negative y-value. The following code was written to create the text.

    fig.text(0,-0.03, 'The Track with the highest mean Average is Communication.')
    fig.text(0,-0.07, 'The Gender with the highest mean Average is Male.')
    fig.text(0,-0.11, 'The Hometown with the highest mean Average is Luzon.')

To finally show the figure, I first made use of .tight_layout function as a way to make sure that the layout of the figure does not get clipped or overlapped. To show the figure, I simply made use of the .show function. The following code was written to show the figure I just created.

    plt.tight_layout()
    plt.show

With this, I was able to satisfy all the objectives given to me in this problem.








