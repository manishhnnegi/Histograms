# Histograms
explanation of histograms!
# Histogram

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

## Unemployment Rates dataset for Canada

#### Ungrouped data

data = [2.3, 6.9, 6.3 ,11.3 ,9.6,
2.8, 7.1, 5.6 ,10.6, 9.1,
3.6 ,5.5 ,7.1, 8.8 ,7.6,
2.4, 5.5, 7.1, 8.8 ,7.6,
2.9 ,4.7, 7.1 ,7.8, 6.8,
3.1 ,3.9, 8.0, 7.5 ,7.2,
4.6 ,3.6, 8.4 ,8.1 ,7.7,
4.4 ,4.1 ,7.5, 10.3, 7.6,
3.4 ,4.8, 7.5 ,11.2 ,7.2,
4.6 ,4.7, 7.6 ,11.4, 6.8,
6.9 ,5.9 ,11.0, 10.4 ,6.3,
6.0 ,6.4, 12.0 ,9.5, 6.0]

print(f"Unemployment Rates for Canada for last {len(data)} years")

## Create a dataframe 

df = pd.DataFrame()
df['unemployment_rate'] = data
df.head()

## Frequency Distribution Table
    The cut method for pandas data splits the dataset into bins. There are a number of arguments for the method. The following code creates equal sized bins. The method value_counts returns a frequency table.



bins = [0. ,3. ,5. ,7.,9.,11.,13.]
frq_df = pd.cut(df['unemployment_rate'], bins)
print(frq_df.value_counts())

#new colum of bins
bins = [0. ,3. ,5. ,7.,9.,11.,13.]
df['feq'] =  pd.cut(df.unemployment_rate,bins,  labels=['1-3','3-5','5-7','7-9','9-11','11-13'])

df.head()

for i,j in df.groupby('feq')['unemployment_rate']:
    print(f"class intervel: {i}")
    print(f"values: {j.values}")
    print(f"Frequency: {len(j)}")
    print("************************")   

## Histogram

plt.xlabel('Unemployment Rates')
plt.ylabel('Frequency')
plt.title('Unemployment Rates for Canada')
plt.ylim(0,30)
sns.histplot(df.unemployment_rate, bins=[1,3,5,7,9,11,13])
plt.show()

### Effect of changing the parameter  bins

#### case1- increas the number of bins (class intervals)

plt.xlabel('Unemployment Rates')
plt.ylabel('Frequency')
plt.title('Unemployment Rates for Canada')
plt.ylim(0,30)
sns.histplot(df.unemployment_rate, bins=[1.,2.,3.,4.,5.,6. ,7.,8.,9.,10.,11.,12.,13.])
plt.show()

#### case2- decrease the number of bins (class intervals)

plt.xlabel('Unemployment Rates')
plt.ylabel('Frequency')
plt.title('Unemployment Rates for Canada')
sns.histplot(df.unemployment_rate, bins=[1.,5. ,9.,13.])
plt.show()

