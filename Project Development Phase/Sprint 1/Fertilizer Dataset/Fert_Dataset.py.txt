import pandas as pd

def get_fert_dataset(loc_Fert):
    
    #read FertPrediction dataset
    data_Fert =pd.read_csv(loc_Fert)
    
    #drop the column Ca,Mg,S,lime,C,Moisture
    data_Fert.drop(['Ca','Mg','S','Lime','C','Moisture'],axis=1,inplace=True)
    
    #drop class =1 row 
    data_Fert.drop(data_Fert[data_Fert['class'] == 1].index, inplace = True) 
    
    #Replace [2,3,4] to [1,2,3]
    data_Fert["class"].replace({ 2 :  1, 3 : 2 , 4 : 3 }, inplace=True)

    return data_Fert