# Energy-poverty-hotspots-eu
energy poverty low income poor housing efficiency climate exposure (heat/cold stress)
import pandas as pd
from sklearn.preprocessing import MinMaxScaler

df = pd.DataFrame({
'region':['Andalusia','Attica','Silesia','Bavaria'],
'energy_poverty':[18,26,15,5],
'low_income':[22,29,20,8],
'poor_housing':[14,19,17,6],
'heat_stress':[21,30,11,7]
})

scaler=MinMaxScaler()

vars=[
'energy_poverty',
'low_income',
'poor_housing',
'heat_stress'
]

df[vars]=scaler.fit_transform(df[vars])

df['hotspot_score']=df[vars].mean(axis=1)

print(
df[['region','hotspot_score']]
.sort_values(
'hotspot_score',
ascending=False
))
