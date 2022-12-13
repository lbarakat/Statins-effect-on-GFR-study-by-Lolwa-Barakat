import pandas as pd
df = pd.read_csv("https://www.lerner.ccf.org/qhs/datasets/GFR.csv")
df.head()
import pandas as pd
df = pd.read_csv("https://www.lerner.ccf.org/qhs/datasets/GFR.csv")
df[['eCcr Pre','eCcr Post']]
df.describe()

import pandas as pd
df = pd.read_csv("https://www.lerner.ccf.org/qhs/datasets/GFR.csv")
df[['eCcr Pre','eCcr Post']]

import pandas as pd
df = pd.read_csv("https://www.lerner.ccf.org/qhs/datasets/GFR.csv")
df.head(20)
df.shape
df.columns
df.info()
df.nunique()
df.isnull().sum()
df=df.fillna(df.median())
df.isnull().sum()
duplicated=df.duplicated().sum()
if duplicated:
  print('Duplicated Rows in Dataset are:{}'.format(duplicated))
else:
    print('Dataset contains no Duplicate Values')
df.describe()
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import missingno as msno # To visualize missing value
import plotly.graph_objects as go # To Generate Graphs
import plotly.express as px # To Generate box plot for statistical representation
%matplotlib inline
fig=px.box(df, x="Diabetes",y="Statins")
fig.show()
import pandas as pd
df = pd.read_csv("https://www.lerner.ccf.org/qhs/datasets/GFR.csv")
df.head(40)
fig=px.box(df, x="eCcr Pre",y="Statins")
fig.show()
sns.boxplot(x='eCcr Pre', y='Statins',data=df)
ns.boxplot(x='eCcr Post', y='Statins',data=df)
fig.show()
sns.boxplot(x='eCcr Post', y='Statins',data=df)
fig.show()
fig=px.box(df, x="eCcr Post",y="Statins")
fig.show()
# print(df.Statins.value_counts())
df['Statins'].hist().plot(kind='bar')
plt.title('Statins Distribution')
sns.set(style="white") 
plt.rcParams['figure.figsize'] = (15, 10) 
sns.heatmap(df.corr(), annot = True, linewidths=.5, cmap="Blues")
plt.title('Corelation Between Variables', fontsize = 30)
plt.show()
import pandas as pd
df = pd.read_csv("https://www.lerner.ccf.org/qhs/datasets/GFR.csv")
df.describe()
df['Statins']=df.Statins.replace({1:"Patients on Statins",0:"Patients not on statins"})
df['Diabetes']=df.Diabetes.replace({1:"Diabetes Patients",0:"Non Diabetes Patients"})
df['CHF']=df.CHF.replace({1:"Patienst with history of Congestive Heart Disease", 0:"Patients with no history of Congestive Heart Disease"})
df['Epired']=df.Epired.replace({1:"Patient Died", 0:"Patient didn't die"})
df['Female']=df.Female.replace({1:"Female Patients",0:"Male Patients"})
df['Acetylcystine']=df.Acetylcystine.replace({1:"Patients given Acetylcystine",0:"Patients not given Acetylcystine"})
df['Emergency']=df.Emergency.replace({1:"Patients needed Emergency Surgery",0:"Patients didn't need Emergency Surgery"})

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import missingno as msno # To visualize missing value
import plotly.graph_objects as go # To Generate Graphs
import plotly.express as px # To Generate box plot for statistical representation
%matplotlib inline
df.plot(kind='box',subplots=True, layout=(3,10),
sharex=False,sharey=False, figsize=(20, 10), 
color='deeppink');
fig= px.box(df,x="Statins",y="Epired")
fig.show()
print(df.Statins.value_counts())
print(df.Statins.value_counts())
#df['Statins'].value_counts().plot(kind='bar').set_title('Distribution of Statins use')#simple plot
fig,ax=plt.subplots(figsize=(5,4))
name=["Patients not on Statins","Patients on Statins"]
ax=df.Statins.value_counts().plot(kind='bar')
ax.set_title("Distribution of Statins use",fontsize=13,weight='bold')
ax.set_xticklabels (name,rotation= 0)
# To calculate the percentage
totals=[]
for i in ax.patches:
  totals.append(i.get_height())
total=sum(totals)
for i in ax.patches:
  ax.text(i.get_x()+.09, i.get_height()-50,\
           str(round((i.get_height()/total)*100, 2))+'%',fontsize=14,
           color='white',weight='bold')
  plt.tight_layout()
#print(df.age.value_counts())
df['Age'].hist().plot(kind='bar')
plt.title('Age Distribution')
# to know the youngest or teh oldest in age in df.describe() or you can have a quick print out
print(min(df.Age))
print(max(df.Age))
print(df.Age.mean())
print(df.Statins.value_counts())
# df['Statins'].value_counts().plot(kind='bar').set_title('Sex distribtion according to Statins use')#Simple plot
fig,ax=plt.subplots(figsize=(8,5))
name=df['Female']
ax=sns.countplot(x='Female',hue='Statins',data=df,palette='Set2')
ax.set_title("Sex Distribution according to Statin use",fontsize=13,weight='bold')
ax.set_xticklabels (name,rotation= 0)
totals=[]
for i in ax.patches:
  totals.append(i.get_height())
total=sum(totals)
for i in ax.patches:
  ax.text(i.get_x()+.05, i.get_height()-15,
          str(round((i.get_height()/total)*100, 2))+'%', fontsize=14,
          color='white', weight='bold')
plt.tight_layout()
print(df.Diabetes.value_counts())
#df['Diabetes'].value_counts().plot(kind='bar').set_title('Distribution of Diabetes')#simple plot
fig,ax=plt.subplots(figsize=(5,4))
name=["Non Diabetes Patients","Diabetes Pateints"]
ax=df.Diabetes.value_counts().plot(kind='bar')
ax.set_title("Distribution of Diabetes",fontsize=13,weight='bold')
ax.set_xticklabels (name,rotation= 0)
# To calculate the percentage
totals=[]
for i in ax.patches:
  totals.append(i.get_height())
total=sum(totals)
for i in ax.patches:
  ax.text(i.get_x()+.09, i.get_height()-50,\
           str(round((i.get_height()/total)*100, 2))+'%',fontsize=14,
           color='white',weight='bold')
  plt.tight_layout()
print(df.Statins.value_counts())
# df['Statins'].value_counts().plot(kind='bar').set_title('Diabetes distribtion according to Statins use')#Simple plot
fig,ax=plt.subplots(figsize=(8,5))
name=["Non Diabetes Patients","Diabetes Pateints"]
ax=sns.countplot(x='Diabetes',hue='Statins',data=df,palette='Set2')
ax.set_title("Diabetes Distribution according to Statin use",fontsize=13,weight='bold')
ax.set_xticklabels (name,rotation= 0)
totals=[]
for i in ax.patches:
  totals.append(i.get_height())
total=sum(totals)
for i in ax.patches:
  ax.text(i.get_x()+.05, i.get_height()-15,
          str(round((i.get_height()/total)*100, 2))+'%', fontsize=14,
          color='white', weight='bold')
plt.tight_layout()
print(df.Statins.value_counts())
# df['Statins'].value_counts().plot(kind='bar').set_title('Expired Patients distribtion according to Statins use')#Simple plot
fig,ax=plt.subplots(figsize=(8,5))
name=["Patients didnt die","Pateints died"]
ax=sns.countplot(x='Epired',hue='Statins',data=df,palette='Set2')
ax.set_title("Expired Patients Distribution according to Statin use",fontsize=13,weight='bold')
ax.set_xticklabels (name,rotation= 0)
totals=[]
for i in ax.patches:
  totals.append(i.get_height())
total=sum(totals)
for i in ax.patches:
  ax.text(i.get_x()+.05, i.get_height()-15,
          str(round((i.get_height()/total)*100, 2))+'%', fontsize=14,
          color='white', weight='bold')
plt.tight_layout()
print(df.Statins.value_counts())
# df['Statins'].value_counts().plot(kind='bar').set_title('Patients who needed emergency or not distribtion according to Statins use')#Simple plot
fig,ax=plt.subplots(figsize=(8,5))
name=["Patients didn't need Emergency Surgery","Pateints needed Emergency"]
ax=sns.countplot(x='Emergency',hue='Statins',data=df,palette='Set2')
ax.set_title("Patients who needed Emergency or not Distribution according to Statin use",fontsize=13,weight='bold')
ax.set_xticklabels (name,rotation= 0)
totals=[]
for i in ax.patches:
  totals.append(i.get_height())
total=sum(totals)
for i in ax.patches:
  ax.text(i.get_x()+.05, i.get_height()-8,
          str(round((i.get_height()/total)*100, 2))+'%', fontsize=11,
          color='white', weight='bold')
plt.tight_layout()
print(df.Statins.value_counts())
# df['Statins'].value_counts().plot(kind='bar').set_title('Patients with history of CHF or not distribtion according to Statins use')#Simple plot
fig,ax=plt.subplots(figsize=(8,5))
name=["Patients with no history of CHF","Pateints with history of CHF"]
ax=sns.countplot(x='CHF',hue='Statins',data=df,palette='Set2')
ax.set_title("Patients with history of CHF or not Distribution according to Statin use",fontsize=13,weight='bold')
ax.set_xticklabels (name,rotation= 0)
totals=[]
for i in ax.patches:
  totals.append(i.get_height())
total=sum(totals)
for i in ax.patches:
  ax.text(i.get_x()+.05, i.get_height()-10,
          str(round((i.get_height()/total)*100, 2))+'%', fontsize=14,
          color='white', weight='bold')
plt.tight_layout()

"Patients not given Acetylcystine"
print(df.Statins.value_counts())
# df['Statins'].value_counts().plot(kind='bar').set_title('Patients given Acetylcystine or not distribtion according to Statins use')#Simple plot
fig,ax=plt.subplots(figsize=(8,5))
name=["Patients not given Acetylcystine","Pateints given Acetycystine"]
ax=sns.countplot(x='Acetylcystine',hue='Statins',data=df,palette='Set2')
ax.set_title("Patients given Aceylcystine or not Distribution according to Statin use",fontsize=13,weight='bold')
ax.set_xticklabels (name,rotation= 0)
totals=[]
for i in ax.patches:
  totals.append(i.get_height())
total=sum(totals)
for i in ax.patches:
  ax.text(i.get_x()+.05, i.get_height()-15,
          str(round((i.get_height()/total)*100, 2))+'%', fontsize=14,
          color='white', weight='bold')
plt.tight_layout()
df[['eCcr Pre','eCcr Post']].describe()
from scipy import stats
stats.shapiro(df['eCcr Pre'])
ShapiroResult(statistic=0.9394695162773132, pvalue=3.387016144981714e-13)
stats.shapiro(df['eCcr Post'])
ShapiroResult(statistic=0.9462264776229858, pvalue=2.6056643821770198e-12)
stats.ttest_rel(df['eCcr Pre'], df['eCcr Post'])
Ttest_relResult(statistic=-0.7024386997891194, pvalue=0.48274122188709745)
df.sample()
df.loc()
import pandas as pd
df = pd.read_csv("https://www.lerner.ccf.org/qhs/datasets/GFR.csv")

#filter using Statins==1
#df.loc[row,columns]
df.loc[df.Statins==1]
df.describe()
df.isnull().sum()
df=df.fillna(df.median())
df.isnull().sum()
from scipy import stats
stats.shapiro(df['eCcr Pre'])
stats.shapiro(df['eCcr Post'])
stats.ttest_rel(df['eCcr Pre'], df['eCcr Post'])
Assumptions: H0: H null= there will be change in GFR in patients using statins after surgery as nephropathy contrast induced occurs thus GFR changed. H1: H Alternative: there will be no change in GFR in patients using statins, after surgery as statins are proven to be renal protective agents.
Interpretation of P value of 0.48 which is not statistically significant because it's > 0.05 in which my hypothesis of No change in GFR for patients on statins is rejected and the null hypothesis is not rejected, as Statins have protective renal effect which is proven by many studies, therefore GFR is expected to not be changed (reduced) after endovascular aortic surgery (in which Acute Kidney Injury as nephropathy can occur secondary to contrast that is given before the surgery as a result GFR may decrease after surgery).In our study null hypothesis can't be rejected as P value is > 0.05 which is 0.48 as GFR changed after procedure despite patients were on statins which have renal protective effects against nephropathy secondary to contrast after endovascular aortic procedure in which patients were given Acetylcysteine to reduce the severity of contrast induced nephropathy in which out of 192 patients who were statin users, 31.97% of those statins users, were given Acetylcysteine to reduce severity of contrast associated nephropathy and only 7.38% of statin users who didn't need to be given Acetylcysteine as they didn't develop contrast induced nephropathy which was measured by change in GFR before and after endovascular aortic surgery.
