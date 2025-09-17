# Experiment 4 – Data Wrangling and Visualization with Pandas

### Name: Dylan Rvy A. Marquez
### Section: 2ECE-B
### Date: 09/18/2025

## OVERVIEW

#### This experiment applies the Pandas library and Matplotlib to perform data wrangling and visualization on a dataset of board examinees. The objective is to filter the dataset based on specific conditions, create new DataFrames, compute averages, and finally visualize how features such as track, gender, and hometown contribute to average grades.

#### The experiment is divided into two parts:

#### Creating new filtered DataFrames (Instru and Mindy).

#### Visualizing the effects of different features (track, gender, hometown) on average grades.

## 1. PROBLEM 1
### Objective:

#### Create two new DataFrames (Instru and Mindy) based on given filtering conditions.

Import the Pandas library and read excel.

```python
boards = pd.read_excel('board2.xlsx')
boards
```
## TABLE : 

<img width="388" height="594" alt="Screenshot 2025-09-18 004806" src="https://github.com/user-attachments/assets/409a042a-d459-43b5-8499-44fc695e6a5e" />


   
## (a) Instru DataFrame

Condition: Track = Instrumentation, Hometown = Luzon, Electronics > 70.

#### Columns: ["Name", "GEAS", "Electronics"].

### Procedure:


```python
Instru = boards.loc[
    (boards['Track'] == 'Instrumentation') & 
    (boards['Hometown'] == 'Luzon') & 
    (boards['Electronics'] > 70),
    ['Name', 'GEAS', 'Electronics']
]
Instru
```

### OUTPUT : 

<img width="218" height="127" alt="Screenshot 2025-09-18 004837" src="https://github.com/user-attachments/assets/dc0ec6e1-2ec2-46b0-aef7-7137c0243ae5" />


This DataFrame filters out examinees who are enrolled in the Instrumentation track, come from Luzon, and have an Electronics score greater than 70. Only the columns for Name, GEAS, and Electronics are displayed to focus on their relevant academic performance.


## (b) Mindy DataFrame

Condition: Hometown = Mindanao, Gender = Female, Average ≥ 55.

#### Columns: ["Name", "Track", "Electronics", "Average"].

```python
boards['Average'] = boards[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

Mindy = boards.loc[
    (boards['Hometown'] == 'Mindanao') & 
    (boards['Gender'] == 'Female') & 
    (boards['Average'] >= 55),
    ['Name', 'Track', 'Electronics', 'Average']
]
Mindy
```

### OUTPUT : 

<img width="338" height="171" alt="Screenshot 2025-09-18 004858" src="https://github.com/user-attachments/assets/351449c6-2324-4448-8a44-347dbca291f0" />

This DataFrame highlights female examinees from Mindanao whose computed average score is at least 55. The table focuses on their Name, Track, Electronics grade, and calculated Average to provide a concise summary of qualified candidates based on the given conditions.


## 2. PROBLEM 2
### Objective:

#### Visualize how Track, Gender, and Hometown influence the average grade of examinees.

### Procedure:

(a) Track vs Average

```python
plt.figure(figsize=(10,6))
plt.bar(boards['Track'], boards['Average'], color="green")
```

### OUTPUT : 

<img width="849" height="520" alt="Screenshot 2025-09-18 004940" src="https://github.com/user-attachments/assets/02727668-12f1-4a65-b004-d75254831cc0" />


The command plt.figure(figsize=(10,6)) specifies the overall size of the graph to make it more readable. The line plt.bar(boards['Track'], boards['Average']) plots a bar graph with academic tracks on the x-axis and average scores on the y-axis. This provides a clear view of how performance varies between different academic tracks and allows direct comparison across categories.
(b) Gender vs Average

```python
plt.figure(figsize=(10,6))
plt.bar(boards['Gender'], boards['Average'], color="pink")
```

### OUTPUT : 

<img width="873" height="515" alt="image" src="https://github.com/user-attachments/assets/9c425396-0c16-439b-a8d9-bee14894b4c3" />


This bar chart displays the distribution of average scores based on gender. The code structure is the same as in the first example, where the figure size is set and a bar chart is generated, but here the x-axis represents gender categories instead of tracks.


(c) Hometown vs Average

```python
plt.figure(figsize=(10,6))
plt.bar(boards['Hometown'], boards['Average'], color="yellow")
```

### OUTPUT : 

<img width="834" height="500" alt="Screenshot 2025-09-18 005051" src="https://github.com/user-attachments/assets/439cecbb-91fe-4a8e-970b-bcfac76d19ec" />


The code begins with plt.figure(figsize=(10,6)) to set the size of the figure, for the plot to become clear. The plt.bar(boards['Hometown'], boards['Average']) command generates a bar chart, where the x-axis represents different hometowns and the y-axis represents the corresponding average scores. This visualization compares average scores across Luzon, Visayas, and Mindanao.

### CONCLUSION

This experiment demonstrated how Pandas and Matplotlib can be applied to effectively analyze and present data. Pandas was used to filter the dataset and compute averages, allowing specific groups such as examinees by track, gender, and hometown to be identified. Matplotlib provided a visual representation of the results through bar graphs, making it easier to compare categories and observe performance trends. The graphs complemented the numerical results by showing patterns that are less noticeable in raw data. The experiment showed the proper utilization of combining data manipulation with visualization in order to extract present findings in a clear and organized manner.













.
