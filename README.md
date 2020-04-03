# Catscatter
*Scatter visualization for categorical features with matplotlib.*


## Context 🤔
I work as a Data Analyst using a bit of Data Science and a lot of Data Visualization. Last December a coworker gave me for Christmas the book ["Knowledge is Beautiful"](https://informationisbeautiful.net/2014/knowledge-is-beautiful/) which I loved. **Data Visualizations there are amazing** and really complex and I like to read it when I want the get inspired.

At the same time I work for a VC fund, where frameworks and **relations are really important**. Showing relations between categorical variables is not always an easy thing due to their "string" nature.

## Solution 💡
These two situations give me to create and use a *catscatter* function that is based in scatter plots relationships but uses categorical variables in a pretty and simple way. Actually, the visualization it's closer to an "adjacent matrix" than to a "scatter plot" because we are **not interested in where the markers are to find correlations but on which categories are connected to each other**, or which ones are more connected to something than other. It can be seen as a kind of "graph" relationships. To follow that relationship it was important to not only plot the markers in the intersections but to draw vertical and horizontal backwards lines.

## Development :gear:
The function is built for python over matplotlib and pandas. The object is not closed so it can be initiated or changed by the user before and after.

## How to use it 👩‍💻

### Properties
- Input:

  + **df:** *required.* pandas DataFrame with at least two columns with categorical variables you want to relate, and the value of both (if it's just an adjacent matrix write 1)
  + **colx:** *required.* The name of the column to display horizontaly
  + **coly:** *required.* The name of the column to display vertically
  + **cols:** *required.* The name of the column with the value between the two variables
  + **color:** *optional.* Colors to display in the visualization, the length can be two or three. The two first are the colors for the lines in the matrix, the last one the font color and markers color.
            *default ['grey','black']*
  + **ratio:** *optional.* A ratio for controlling the relative size of the markers.
            *default 10*
  + **font:** *optional.* The font for the ticks on the matrix.
            *default 'Helvetica'*
  + **save:** *optional.* True for saving as an image in the same path as the code.
            *default False*
  + **save_name:** *optional.* The name used for saving the image (then the code ads .png)
            *default: "Default"*
- Output:

  + No output.

### Use example
- **Basic use**
```
import pandas as pd
import matplotlib as plt

# example data frame
data=pd.DataFrame({'friend':['Peter','Marc','Ignacio','Marta','Marta','Ignacio','Maria','Pedro','Bea','Pedro'],
                  'favorite_food':['Salmon','Chocolate','Hamburguer','Pizza','Apples','Pizza','Pizza','Hamburguer','Salmon','Banana'],
                  'favorite_grade':[1,5,5,3,2,3,4,4,3,1]})

#plot it
scatter_matrix(data,'friend','favorite_food','favorite_grade')
plt.show()
```

![](basic_use.png)

- **Personalized use**
```
import pandas as pd
import matplotlib as plt

# example data frame
data=pd.DataFrame({'friend':['Peter','Marc','Ignacio','Marta','Marta','Ignacio','Maria','Pedro','Bea','Pedro'],
                  'favorite_food':['Salmon','Chocolate','Hamburguer','Pizza','Apples','Pizza','Pizza','Hamburguer','Salmon','Banana'],
                  'favorite_grade':[1,5,5,3,2,3,4,4,3,1]})

colors=['green','grey','orange']

#create the plot
plt.figure(figsize=(8,8))
catscatter(data,'friend','favorite_food','favorite_grade',color=colors,ratio=100)
plt.xticks(fontsize=14)
plt.yticks(fontsize=14)
plt.show()
```
![](personalized_use.png)
