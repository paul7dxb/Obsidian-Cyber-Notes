`import numpy as np`

Declare array
`A = np.array([1,2,3])`

### Matrix work
Matirces counted rows x columns
2 x 3 matrix:
```
[1,2,3],
[4,5,6]
```
```
#Dot product (a is np array)
np.dot(a,b)
a.dot(b)

#magnitude of matrix
np.linalg.norm(a)

#Accessing array element
A = np.array([1,2],[3,4])
A[0,1] # returns 2
#select column
A[:,0] #returns first column

#Transpose
A.T

#Dot product
A.dot(B)
#element wise multiplication
A * B

#Inverse
np.linalg.inv(A)

```

### Chack values equal
Without running into computer rounding errors
```
np.allclose(<expression1>, <expresssion2>)
```

### Solve similitaneous equations
```
x = np.linalg.solve(A,b)

#Don't use inverse operation
x = np.linalg.inv(A).dot(b)
```

## Matplotlib
```
import matplotlib.pyplot as plt
```
Plot linegraph and show
```
plt.plot(x,y)
plt.xlabel('myxLabel')
plt.title('myTitle')
plt.show()
```

Sctterplot with colours
```
X = np.random.randn(2100,2)
X[:50] += 3 #Shift first 50 to be centred around (3,3)
Y = np.zeros(200) # Label array
Y[:50] =1
plt.scatter(X[:0], X[:1], c=Y) #(x,y,colour)
```

Histogram
```
plt.hist(X, bins=50) # Set number of bins
```

Plot images
```
from PIL import image
im = Image.open('filename.png')
arr = np.array(im)
plt.imshow(arr)

gray = arr.mean(axis=2) #Average RGB
```

## Pandas
```
import pandas as pd
```
Import export CSV
```
df = pd.read_csv('fileinput.csv') #df is type DataFrame

df.to_csv('fileoutput.csv')
df.to_csv('fileoutput.csv', index=False) #Remove index column (sometimes blank)
df.to_csv('fileoutput.csv', header=False) #Remove column names

```

```
df.head(noOfRows) #preview table number of rows

df.info()

df.columns()
```

Select rows and columns
Pandas 1-d (column or row) stored as series
Pandas 2-d (2 or more columns) stored as DataFrame
Access by element [] returns a column not a row
Access row by iloc
```
df.iloc[0] #Returns first row of data by integer index
df.loc[0] # returns row by index label (if index_col set)
```

Get rows by condition
```
df[df['column'] > 64]
```

Data frame to numpy array
```
A = df[['column1','column2']].values
```

Data frame adjust data without for loop
```
def myFunc(row):
	return int(row['columnName'].someMethod())
	
df.apply(myFunc, axis=1)
```

Add new column
```
df['newColName'] = df.apply(someFunc, axis=1)
```

Pandas plotting
```
df['columnName'].hist()
df['columnName'].plot()

from pandas.plotting import scatter_matrix
scatter_matrix(df[['columnName1', 'high', 'low', 'columnName2']], alpha = 0.2, figsize=(6,6))
```