---

title: "ANOVA FROM SCRATCH"
collection: Notebooks
permalink: /Notebooks/ANOVA
layout: post
Description: 'ANOVA from scratch'

---


```
from google.colab import drive
drive.mount('/content/drive')
```

    Mounted at /content/drive
    


```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
plt.style.use('seaborn')
plt.rcParams['figure.figsize'] = (12, 8)
import string

from scipy.stats import f
```


```
df = pd.read_csv('/content/drive/My Drive/temperaturevdensity.csv')
```


```
class OneWayANOVA:
  def __init__(self,dataframe,alpha):
    self.dataframe = dataframe
    self.alpha = alpha
 
  def SST(self):
    temp1 = np.array(self.dataframe[self.dataframe.columns[1]]*self.dataframe[self.dataframe.columns[1]]).sum()
    temp2 = np.array(self.dataframe[self.dataframe.columns[1]]).sum()**2
    temp3 = len(self.dataframe[self.dataframe.columns[1]])
    return temp1 - (temp2/temp3)

  def treatmentName(self):
    return self.dataframe[self.dataframe.columns[0]].unique()

  def operand(self,key):
    temp1=self.treatmentName()[key]
    return np.array(self.dataframe[self.dataframe[self.dataframe.columns[0]]==temp1][self.dataframe.columns[1]])
  
  def SSTreatment(self):
    l=[]
    for i in range(0,len(self.treatmentName())):
      temp1 = self.operand(i)
      temp1 = np.array(temp1)
      temp1 = temp1.sum()
      temp1 = temp1 ** 2
      l.append(temp1)
    
    l= np.array(l)

    temp2 = np.array(self.dataframe[self.dataframe.columns[1]]).sum()**2
    temp3 = len(self.dataframe[self.dataframe.columns[1]])


    return l.sum()/len(self.treatmentName()) - temp2/temp3

  def SSE(self):
    return self.SST()-self.SSTreatment()

  def degree_of_freedom(self):
    
    total = len(self.dataframe)-1
    treatment = len(self.treatmentName()) - 1
    error = total - treatment
    return {'treatment' : treatment, 'error':error, 'total':total}
  
  def MSE(self):
    return {'MSTreatment':self.SSTreatment()/self.degree_of_freedom()['treatment'],'MSE':self.SSE()/self.degree_of_freedom()['error']}
  
  def f_stats(self):
    return self.MSE()['MSTreatment']/self.MSE()['MSE']
  
  def f_stats_theoretical(self):
    d1 = self.degree_of_freedom()['treatment']
    d2 = self.degree_of_freedom()['error']
    return f.ppf(1-self.alpha,d1,d2)
  
  def ANOVA(self):
    
    temp1 = string.Template("""

               ANALYSIS OF VARIANCE - FIXED EFFECT AND ONE FACTOR

               CALCULATED F statistics   : $value1 

               THEORETICAL F statistics  : $value2

               $RESULT
               """)
    
    temp2 = {'value1':self.f_stats(),'value2':self.f_stats_theoretical()}

    if temp2['value1']> temp2['value2']:
      RESULT = 'SIGNIFICANT RESULT'
    else:
      RESULT = 'INSIGNIFICANT RESULT'
     
    temp2 = {'value1':self.f_stats(),'value2':self.f_stats_theoretical(),'RESULT':RESULT}
    print(temp1.substitute(temp2))






                
```


```
d = OneWayANOVA(df,0.10)
d.ANOVA()
```

    
    
                   ANALYSIS OF VARIANCE - FIXED EFFECT AND ONE FACTOR
    
                   CALCULATED F statistics   : -4.668707572181572 
    
                   THEORETICAL F statistics  : 2.5222235975347784
    
                   INSIGNIFICANT RESULT
                   
    
