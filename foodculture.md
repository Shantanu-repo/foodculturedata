

```python
import pandas as pd
```


```python
# reading dataset
ds = pd.read_csv('culturefood.csv')
```


```python
ds.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 275 entries, 0 to 274
    Data columns (total 19 columns):
    Timestamp                                                                                                                                                                                                                                                                                                    275 non-null object
    Name                                                                                                                                                                                                                                                                                                         275 non-null object
    Age                                                                                                                                                                                                                                                                                                          275 non-null int64
    City                                                                                                                                                                                                                                                                                                         275 non-null object
    Marital status                                                                                                                                                                                                                                                                                               275 non-null object
    Current Employment Status                                                                                                                                                                                                                                                                                    275 non-null object
    How many major meals a day do you usually consume? (such as breakfast, lunch, dinner, snacks, etc.)                                                                                                                                                                                                          275 non-null object
    How do you usually manage your meals throughout your day?                                                                                                                                                                                                                                                    275 non-null object
    Any of your meals are home cooked?                                                                                                                                                                                                                                                                           275 non-null object
    If you cook yourself, how much time is spent on cooking (approximately)? (If not, please select last option)                                                                                                                                                                                                 275 non-null object
    What kind dishes do you usually prefer "Home-cooked"? (You can select more than one option)                                                                                                                                                                                                                  275 non-null object
    What kind dishes do you prefer "ordering online"? (You can select more than one option)                                                                                                                                                                                                                      275 non-null object
    Why do you not prefer to cook? (If you do, please select last option)                                                                                                                                                                                                                                        275 non-null object
    How frequently do you use pre-cooked & packed meals or instant meals?                                                                                                                                                                                                                                        275 non-null object
    Rank the below factors ( in column) in order of the significance they hold, when it comes to your food/meal. (Select the most important factor amongst the 5 listed,  as first choice (row 1), and likewise rank the rest subsequently) **Please select a unique option against each row. [First Choice]     273 non-null object
    Rank the below factors ( in column) in order of the significance they hold, when it comes to your food/meal. (Select the most important factor amongst the 5 listed,  as first choice (row 1), and likewise rank the rest subsequently) **Please select a unique option against each row. [Second Choice]    274 non-null object
    Rank the below factors ( in column) in order of the significance they hold, when it comes to your food/meal. (Select the most important factor amongst the 5 listed,  as first choice (row 1), and likewise rank the rest subsequently) **Please select a unique option against each row. [Third Choice]     275 non-null object
    Rank the below factors ( in column) in order of the significance they hold, when it comes to your food/meal. (Select the most important factor amongst the 5 listed,  as first choice (row 1), and likewise rank the rest subsequently) **Please select a unique option against each row. [Fourth Choice]    273 non-null object
    Rank the below factors ( in column) in order of the significance they hold, when it comes to your food/meal. (Select the most important factor amongst the 5 listed,  as first choice (row 1), and likewise rank the rest subsequently) **Please select a unique option against each row. [Fifth Choice]     275 non-null object
    dtypes: int64(1), object(18)
    memory usage: 40.9+ KB





```python
City_names = ds.City.unique()
City_names
```




    array(['Mumbai ', 'Mumbai', 'Pune', 'Chandigarh', 'Kalimpong',
           'Bangalore', 'Gurgaon', 'Delhi', 'Manipal', 'Jalandhar ',
           'Bhubaneswar', 'New Delhi', 'Vizag', 'Surat', 'Ludhiana',
           'Hyderabad', 'Nagpur ', 'Ahmedabad ', 'Vadodara ', 'new Delhi',
           'Delhi ', 'Bhopal', 'Ahmedabad', 'Greenwich', 'Hyderabad ',
           'Nagpur', 'Kolkata', 'Indore', 'Gandhinagar/Ahmedabad',
           'Ludhiana ', 'Kathmandu', 'Thane', 'Navi mumbai', 'Navi Mumbai',
           'Kalyan', 'Gurugram', 'Mumbai, MH', 'Rishikesh ', 'Bangalore ',
           'New delhi', 'Visakhapatnam ', 'Chennai', 'Ranchi', 'Brampton ',
           'Latur', 'Bhusawal', 'New Delhi ', 'Navi Mumbai ', 'Ajmer',
           'Chicago Usa', 'Jaipur', 'Vadodara', 'Faridabad ', 'Nashik ',
           'Kharagpur', 'Bhusaval', 'Kalyan ', 'Kalyan District Thane',
           'Varanasi ', 'Vapi', 'Thane ', 'Jodhpur', 'Rajkot', 'Bengaluru ',
           'Bengaluru', 'Gurgaon ', 'BENGALURU', 'Ahmednagar', 'Noida',
           'Pune ', 'Goa', 'PUNE', 'New York', 'Melbourne ', 'Nashik',
           'Jodhpur ', 'East Blue', 'jaipur', 'Chandigarh ', 'Barmer ',
           'JAIPUR', 'Kuwait', 'Port Blair', 'Osmanabad', 'Udaipur ',
           'Kharghar, Navi Mumbai', 'VISAKHAPATNAM '], dtype=object)



Making the city names consistant:


```python
ds['City'] = ds['City'].str.strip()
```


```python

```


```python
ds.loc[ds['City'] == 'Kharghar, Navi Mumbai' , 'City'] = 'Navi Mumbai'
ds.loc[ds['City'] == 'Mumbai, MH' , 'City'] = 'Mumbai'
ds.loc[ds['City'] == 'PUNE' , 'City'] = 'Pune'
ds.loc[ds['City'] == 'new Delhi' , 'City'] = 'New Delhi'
```


```python
ds['City']
```




    0             Mumbai 
    1              Mumbai
    2                Pune
    3          Chandigarh
    4                Pune
    5           Kalimpong
    6           Bangalore
    7             Mumbai 
    8           Bangalore
    9           Bangalore
    10            Gurgaon
    11               Pune
    12            Mumbai 
    13              Delhi
    14            Manipal
    15               Pune
    16         Jalandhar 
    17            Manipal
    18        Bhubaneswar
    19              Delhi
    20          New Delhi
    21               Pune
    22               Pune
    23               Pune
    24              Vizag
    25              Surat
    26             Mumbai
    27               Pune
    28           Ludhiana
    29          Hyderabad
                ...      
    245         Bangalore
    246            Kuwait
    247         New Delhi
    248          Jodhpur 
    249           Gurgaon
    250            Jaipur
    251        Port Blair
    252             Delhi
    253           Jodhpur
    254            Jaipur
    255           Gurgaon
    256           Gurgaon
    257              Pune
    258          Jodhpur 
    259              Pune
    260         Osmanabad
    261             Surat
    262             Delhi
    263         Bengaluru
    264         New Delhi
    265            Mumbai
    266         Ahmedabad
    267      Navi Mumbai 
    268          Udaipur 
    269            Indore
    270         Bengaluru
    271       Navi Mumbai
    272    VISAKHAPATNAM 
    273            Nagpur
    274       Navi Mumbai
    Name: City, Length: 275, dtype: object




```python
print("Number of entries citywise: ")
print("Mumbai: " , ds.City.value_counts()['Mumbai'])
```

    Number of entries citywise: 
    Mumbai 25



```python

```
