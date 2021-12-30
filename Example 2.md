```python
#Import Python Libraries 
import numpy as np
import scipy as sp
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```


```python
df = pd.read_csv("sales_data_sample.csv")
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ORDERNUMBER</th>
      <th>QUANTITYORDERED</th>
      <th>PRICEEACH</th>
      <th>ORDERLINENUMBER</th>
      <th>SALES</th>
      <th>ORDERDATE</th>
      <th>STATUS</th>
      <th>QTR_ID</th>
      <th>MONTH_ID</th>
      <th>YEAR_ID</th>
      <th>...</th>
      <th>ADDRESSLINE1</th>
      <th>ADDRESSLINE2</th>
      <th>CITY</th>
      <th>STATE</th>
      <th>POSTALCODE</th>
      <th>COUNTRY</th>
      <th>TERRITORY</th>
      <th>CONTACTLASTNAME</th>
      <th>CONTACTFIRSTNAME</th>
      <th>DEALSIZE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10107</td>
      <td>30</td>
      <td>95.70</td>
      <td>2</td>
      <td>2871.00</td>
      <td>2/24/2003 0:00</td>
      <td>Shipped</td>
      <td>1</td>
      <td>2</td>
      <td>2003</td>
      <td>...</td>
      <td>897 Long Airport Avenue</td>
      <td>NaN</td>
      <td>NYC</td>
      <td>NY</td>
      <td>10022</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Yu</td>
      <td>Kwai</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10121</td>
      <td>34</td>
      <td>81.35</td>
      <td>5</td>
      <td>2765.90</td>
      <td>5/7/2003 0:00</td>
      <td>Shipped</td>
      <td>2</td>
      <td>5</td>
      <td>2003</td>
      <td>...</td>
      <td>59 rue de l'Abbaye</td>
      <td>NaN</td>
      <td>Reims</td>
      <td>NaN</td>
      <td>51100</td>
      <td>France</td>
      <td>EMEA</td>
      <td>Henriot</td>
      <td>Paul</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2</th>
      <td>10134</td>
      <td>41</td>
      <td>94.74</td>
      <td>2</td>
      <td>3884.34</td>
      <td>7/1/2003 0:00</td>
      <td>Shipped</td>
      <td>3</td>
      <td>7</td>
      <td>2003</td>
      <td>...</td>
      <td>27 rue du Colonel Pierre Avia</td>
      <td>NaN</td>
      <td>Paris</td>
      <td>NaN</td>
      <td>75508</td>
      <td>France</td>
      <td>EMEA</td>
      <td>Da Cunha</td>
      <td>Daniel</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>3</th>
      <td>10145</td>
      <td>45</td>
      <td>83.26</td>
      <td>6</td>
      <td>3746.70</td>
      <td>8/25/2003 0:00</td>
      <td>Shipped</td>
      <td>3</td>
      <td>8</td>
      <td>2003</td>
      <td>...</td>
      <td>78934 Hillside Dr.</td>
      <td>NaN</td>
      <td>Pasadena</td>
      <td>CA</td>
      <td>90003</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Young</td>
      <td>Julie</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10159</td>
      <td>49</td>
      <td>100.00</td>
      <td>14</td>
      <td>5205.27</td>
      <td>10/10/2003 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>10</td>
      <td>2003</td>
      <td>...</td>
      <td>7734 Strong St.</td>
      <td>NaN</td>
      <td>San Francisco</td>
      <td>CA</td>
      <td>NaN</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Brown</td>
      <td>Julie</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2818</th>
      <td>10350</td>
      <td>20</td>
      <td>100.00</td>
      <td>15</td>
      <td>2244.40</td>
      <td>12/2/2004 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>12</td>
      <td>2004</td>
      <td>...</td>
      <td>C/ Moralzarzal, 86</td>
      <td>NaN</td>
      <td>Madrid</td>
      <td>NaN</td>
      <td>28034</td>
      <td>Spain</td>
      <td>EMEA</td>
      <td>Freyre</td>
      <td>Diego</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2819</th>
      <td>10373</td>
      <td>29</td>
      <td>100.00</td>
      <td>1</td>
      <td>3978.51</td>
      <td>1/31/2005 0:00</td>
      <td>Shipped</td>
      <td>1</td>
      <td>1</td>
      <td>2005</td>
      <td>...</td>
      <td>Torikatu 38</td>
      <td>NaN</td>
      <td>Oulu</td>
      <td>NaN</td>
      <td>90110</td>
      <td>Finland</td>
      <td>EMEA</td>
      <td>Koskitalo</td>
      <td>Pirkko</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>2820</th>
      <td>10386</td>
      <td>43</td>
      <td>100.00</td>
      <td>4</td>
      <td>5417.57</td>
      <td>3/1/2005 0:00</td>
      <td>Resolved</td>
      <td>1</td>
      <td>3</td>
      <td>2005</td>
      <td>...</td>
      <td>C/ Moralzarzal, 86</td>
      <td>NaN</td>
      <td>Madrid</td>
      <td>NaN</td>
      <td>28034</td>
      <td>Spain</td>
      <td>EMEA</td>
      <td>Freyre</td>
      <td>Diego</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>2821</th>
      <td>10397</td>
      <td>34</td>
      <td>62.24</td>
      <td>1</td>
      <td>2116.16</td>
      <td>3/28/2005 0:00</td>
      <td>Shipped</td>
      <td>1</td>
      <td>3</td>
      <td>2005</td>
      <td>...</td>
      <td>1 rue Alsace-Lorraine</td>
      <td>NaN</td>
      <td>Toulouse</td>
      <td>NaN</td>
      <td>31000</td>
      <td>France</td>
      <td>EMEA</td>
      <td>Roulet</td>
      <td>Annette</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2822</th>
      <td>10414</td>
      <td>47</td>
      <td>65.52</td>
      <td>9</td>
      <td>3079.44</td>
      <td>5/6/2005 0:00</td>
      <td>On Hold</td>
      <td>2</td>
      <td>5</td>
      <td>2005</td>
      <td>...</td>
      <td>8616 Spinnaker Dr.</td>
      <td>NaN</td>
      <td>Boston</td>
      <td>MA</td>
      <td>51003</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Yoshido</td>
      <td>Juri</td>
      <td>Medium</td>
    </tr>
  </tbody>
</table>
<p>2823 rows × 25 columns</p>
</div>




```python
df.head(100)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ORDERNUMBER</th>
      <th>QUANTITYORDERED</th>
      <th>PRICEEACH</th>
      <th>ORDERLINENUMBER</th>
      <th>SALES</th>
      <th>ORDERDATE</th>
      <th>STATUS</th>
      <th>QTR_ID</th>
      <th>MONTH_ID</th>
      <th>YEAR_ID</th>
      <th>...</th>
      <th>ADDRESSLINE1</th>
      <th>ADDRESSLINE2</th>
      <th>CITY</th>
      <th>STATE</th>
      <th>POSTALCODE</th>
      <th>COUNTRY</th>
      <th>TERRITORY</th>
      <th>CONTACTLASTNAME</th>
      <th>CONTACTFIRSTNAME</th>
      <th>DEALSIZE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10107</td>
      <td>30</td>
      <td>95.70</td>
      <td>2</td>
      <td>2871.00</td>
      <td>2/24/2003 0:00</td>
      <td>Shipped</td>
      <td>1</td>
      <td>2</td>
      <td>2003</td>
      <td>...</td>
      <td>897 Long Airport Avenue</td>
      <td>NaN</td>
      <td>NYC</td>
      <td>NY</td>
      <td>10022</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Yu</td>
      <td>Kwai</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10121</td>
      <td>34</td>
      <td>81.35</td>
      <td>5</td>
      <td>2765.90</td>
      <td>5/7/2003 0:00</td>
      <td>Shipped</td>
      <td>2</td>
      <td>5</td>
      <td>2003</td>
      <td>...</td>
      <td>59 rue de l'Abbaye</td>
      <td>NaN</td>
      <td>Reims</td>
      <td>NaN</td>
      <td>51100</td>
      <td>France</td>
      <td>EMEA</td>
      <td>Henriot</td>
      <td>Paul</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2</th>
      <td>10134</td>
      <td>41</td>
      <td>94.74</td>
      <td>2</td>
      <td>3884.34</td>
      <td>7/1/2003 0:00</td>
      <td>Shipped</td>
      <td>3</td>
      <td>7</td>
      <td>2003</td>
      <td>...</td>
      <td>27 rue du Colonel Pierre Avia</td>
      <td>NaN</td>
      <td>Paris</td>
      <td>NaN</td>
      <td>75508</td>
      <td>France</td>
      <td>EMEA</td>
      <td>Da Cunha</td>
      <td>Daniel</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>3</th>
      <td>10145</td>
      <td>45</td>
      <td>83.26</td>
      <td>6</td>
      <td>3746.70</td>
      <td>8/25/2003 0:00</td>
      <td>Shipped</td>
      <td>3</td>
      <td>8</td>
      <td>2003</td>
      <td>...</td>
      <td>78934 Hillside Dr.</td>
      <td>NaN</td>
      <td>Pasadena</td>
      <td>CA</td>
      <td>90003</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Young</td>
      <td>Julie</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>4</th>
      <td>10159</td>
      <td>49</td>
      <td>100.00</td>
      <td>14</td>
      <td>5205.27</td>
      <td>10/10/2003 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>10</td>
      <td>2003</td>
      <td>...</td>
      <td>7734 Strong St.</td>
      <td>NaN</td>
      <td>San Francisco</td>
      <td>CA</td>
      <td>NaN</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Brown</td>
      <td>Julie</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>95</th>
      <td>10285</td>
      <td>27</td>
      <td>100.00</td>
      <td>8</td>
      <td>5438.07</td>
      <td>8/27/2004 0:00</td>
      <td>Shipped</td>
      <td>3</td>
      <td>8</td>
      <td>2004</td>
      <td>...</td>
      <td>39323 Spinnaker Dr.</td>
      <td>NaN</td>
      <td>Cambridge</td>
      <td>MA</td>
      <td>51247</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Hernandez</td>
      <td>Marta</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>96</th>
      <td>10299</td>
      <td>29</td>
      <td>100.00</td>
      <td>11</td>
      <td>6683.34</td>
      <td>9/30/2004 0:00</td>
      <td>Shipped</td>
      <td>3</td>
      <td>9</td>
      <td>2004</td>
      <td>...</td>
      <td>Keskuskatu 45</td>
      <td>NaN</td>
      <td>Helsinki</td>
      <td>NaN</td>
      <td>21240</td>
      <td>Finland</td>
      <td>EMEA</td>
      <td>Karttunen</td>
      <td>Matti</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>97</th>
      <td>10308</td>
      <td>20</td>
      <td>100.00</td>
      <td>1</td>
      <td>4570.40</td>
      <td>10/15/2004 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>10</td>
      <td>2004</td>
      <td>...</td>
      <td>3758 North Pendale Street</td>
      <td>NaN</td>
      <td>White Plains</td>
      <td>NY</td>
      <td>24067</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Frick</td>
      <td>Steve</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>98</th>
      <td>10318</td>
      <td>37</td>
      <td>100.00</td>
      <td>3</td>
      <td>7667.14</td>
      <td>11/2/2004 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>11</td>
      <td>2004</td>
      <td>...</td>
      <td>7586 Pompton St.</td>
      <td>NaN</td>
      <td>Allentown</td>
      <td>PA</td>
      <td>70267</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Yu</td>
      <td>Kyung</td>
      <td>Large</td>
    </tr>
    <tr>
      <th>99</th>
      <td>10329</td>
      <td>26</td>
      <td>100.00</td>
      <td>3</td>
      <td>5868.20</td>
      <td>11/15/2004 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>11</td>
      <td>2004</td>
      <td>...</td>
      <td>897 Long Airport Avenue</td>
      <td>NaN</td>
      <td>NYC</td>
      <td>NY</td>
      <td>10022</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Yu</td>
      <td>Kwai</td>
      <td>Medium</td>
    </tr>
  </tbody>
</table>
<p>100 rows × 25 columns</p>
</div>




```python
#Display last 10 records
df.tail(20)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ORDERNUMBER</th>
      <th>QUANTITYORDERED</th>
      <th>PRICEEACH</th>
      <th>ORDERLINENUMBER</th>
      <th>SALES</th>
      <th>ORDERDATE</th>
      <th>STATUS</th>
      <th>QTR_ID</th>
      <th>MONTH_ID</th>
      <th>YEAR_ID</th>
      <th>...</th>
      <th>ADDRESSLINE1</th>
      <th>ADDRESSLINE2</th>
      <th>CITY</th>
      <th>STATE</th>
      <th>POSTALCODE</th>
      <th>COUNTRY</th>
      <th>TERRITORY</th>
      <th>CONTACTLASTNAME</th>
      <th>CONTACTFIRSTNAME</th>
      <th>DEALSIZE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2803</th>
      <td>10177</td>
      <td>40</td>
      <td>50.23</td>
      <td>6</td>
      <td>2009.20</td>
      <td>11/7/2003 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>11</td>
      <td>2003</td>
      <td>...</td>
      <td>Merchants House, 27-30 Merchant's Quay</td>
      <td>NaN</td>
      <td>Madrid</td>
      <td>NaN</td>
      <td>28023</td>
      <td>Spain</td>
      <td>EMEA</td>
      <td>Fernandez</td>
      <td>Jesus</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2804</th>
      <td>10185</td>
      <td>28</td>
      <td>64.43</td>
      <td>6</td>
      <td>1804.04</td>
      <td>11/14/2003 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>11</td>
      <td>2003</td>
      <td>...</td>
      <td>4575 Hillside Dr.</td>
      <td>NaN</td>
      <td>New Bedford</td>
      <td>MA</td>
      <td>50553</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Tam</td>
      <td>Wing C</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2805</th>
      <td>10197</td>
      <td>42</td>
      <td>50.23</td>
      <td>12</td>
      <td>2109.66</td>
      <td>11/26/2003 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>11</td>
      <td>2003</td>
      <td>...</td>
      <td>Rambla de Catalu�a, 23</td>
      <td>NaN</td>
      <td>Barcelona</td>
      <td>NaN</td>
      <td>8022</td>
      <td>Spain</td>
      <td>EMEA</td>
      <td>Saavedra</td>
      <td>Eduardo</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2806</th>
      <td>10208</td>
      <td>42</td>
      <td>63.88</td>
      <td>6</td>
      <td>2682.96</td>
      <td>1/2/2004 0:00</td>
      <td>Shipped</td>
      <td>1</td>
      <td>1</td>
      <td>2004</td>
      <td>...</td>
      <td>2, rue du Commerce</td>
      <td>NaN</td>
      <td>Lyon</td>
      <td>NaN</td>
      <td>69004</td>
      <td>France</td>
      <td>EMEA</td>
      <td>Saveley</td>
      <td>Mary</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2807</th>
      <td>10222</td>
      <td>36</td>
      <td>63.34</td>
      <td>18</td>
      <td>2280.24</td>
      <td>2/19/2004 0:00</td>
      <td>Shipped</td>
      <td>1</td>
      <td>2</td>
      <td>2004</td>
      <td>...</td>
      <td>361 Furth Circle</td>
      <td>NaN</td>
      <td>San Diego</td>
      <td>CA</td>
      <td>91217</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Thompson</td>
      <td>Valarie</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2808</th>
      <td>10232</td>
      <td>24</td>
      <td>49.69</td>
      <td>3</td>
      <td>1192.56</td>
      <td>3/20/2004 0:00</td>
      <td>Shipped</td>
      <td>1</td>
      <td>3</td>
      <td>2004</td>
      <td>...</td>
      <td>Garden House Crowther Way</td>
      <td>NaN</td>
      <td>Cowes</td>
      <td>Isle of Wight</td>
      <td>PO31 7PJ</td>
      <td>UK</td>
      <td>EMEA</td>
      <td>Bennett</td>
      <td>Helen</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2809</th>
      <td>10248</td>
      <td>23</td>
      <td>65.52</td>
      <td>9</td>
      <td>1506.96</td>
      <td>5/7/2004 0:00</td>
      <td>Cancelled</td>
      <td>2</td>
      <td>5</td>
      <td>2004</td>
      <td>...</td>
      <td>897 Long Airport Avenue</td>
      <td>NaN</td>
      <td>NYC</td>
      <td>NY</td>
      <td>10022</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Yu</td>
      <td>Kwai</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2810</th>
      <td>10261</td>
      <td>29</td>
      <td>50.78</td>
      <td>7</td>
      <td>1472.62</td>
      <td>6/17/2004 0:00</td>
      <td>Shipped</td>
      <td>2</td>
      <td>6</td>
      <td>2004</td>
      <td>...</td>
      <td>43 rue St. Laurent</td>
      <td>NaN</td>
      <td>Montreal</td>
      <td>Quebec</td>
      <td>H1J 1C3</td>
      <td>Canada</td>
      <td>NaN</td>
      <td>Fresnisre</td>
      <td>Jean</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2811</th>
      <td>10273</td>
      <td>37</td>
      <td>45.86</td>
      <td>10</td>
      <td>1696.82</td>
      <td>7/21/2004 0:00</td>
      <td>Shipped</td>
      <td>3</td>
      <td>7</td>
      <td>2004</td>
      <td>...</td>
      <td>Rue Joseph-Bens 532</td>
      <td>NaN</td>
      <td>Bruxelles</td>
      <td>NaN</td>
      <td>B-1180</td>
      <td>Belgium</td>
      <td>EMEA</td>
      <td>Dewey</td>
      <td>Catherine</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2812</th>
      <td>10283</td>
      <td>33</td>
      <td>51.32</td>
      <td>12</td>
      <td>1693.56</td>
      <td>8/20/2004 0:00</td>
      <td>Shipped</td>
      <td>3</td>
      <td>8</td>
      <td>2004</td>
      <td>...</td>
      <td>23 Tsawassen Blvd.</td>
      <td>NaN</td>
      <td>Tsawassen</td>
      <td>BC</td>
      <td>T2F 8M4</td>
      <td>Canada</td>
      <td>NaN</td>
      <td>Lincoln</td>
      <td>Elizabeth</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2813</th>
      <td>10293</td>
      <td>32</td>
      <td>60.06</td>
      <td>1</td>
      <td>1921.92</td>
      <td>9/9/2004 0:00</td>
      <td>Shipped</td>
      <td>3</td>
      <td>9</td>
      <td>2004</td>
      <td>...</td>
      <td>Via Monte Bianco 34</td>
      <td>NaN</td>
      <td>Torino</td>
      <td>NaN</td>
      <td>10100</td>
      <td>Italy</td>
      <td>EMEA</td>
      <td>Accorti</td>
      <td>Paolo</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2814</th>
      <td>10306</td>
      <td>35</td>
      <td>59.51</td>
      <td>6</td>
      <td>2082.85</td>
      <td>10/14/2004 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>10</td>
      <td>2004</td>
      <td>...</td>
      <td>Fauntleroy Circus</td>
      <td>NaN</td>
      <td>Manchester</td>
      <td>NaN</td>
      <td>EC2 5NT</td>
      <td>UK</td>
      <td>EMEA</td>
      <td>Ashworth</td>
      <td>Victoria</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2815</th>
      <td>10315</td>
      <td>40</td>
      <td>55.69</td>
      <td>5</td>
      <td>2227.60</td>
      <td>10/29/2004 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>10</td>
      <td>2004</td>
      <td>...</td>
      <td>67, rue des Cinquante Otages</td>
      <td>NaN</td>
      <td>Nantes</td>
      <td>NaN</td>
      <td>44000</td>
      <td>France</td>
      <td>EMEA</td>
      <td>Labrune</td>
      <td>Janine</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2816</th>
      <td>10327</td>
      <td>37</td>
      <td>86.74</td>
      <td>4</td>
      <td>3209.38</td>
      <td>11/10/2004 0:00</td>
      <td>Resolved</td>
      <td>4</td>
      <td>11</td>
      <td>2004</td>
      <td>...</td>
      <td>Vinb'ltet 34</td>
      <td>NaN</td>
      <td>Kobenhavn</td>
      <td>NaN</td>
      <td>1734</td>
      <td>Denmark</td>
      <td>EMEA</td>
      <td>Petersen</td>
      <td>Jytte</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>2817</th>
      <td>10337</td>
      <td>42</td>
      <td>97.16</td>
      <td>5</td>
      <td>4080.72</td>
      <td>11/21/2004 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>11</td>
      <td>2004</td>
      <td>...</td>
      <td>5905 Pompton St.</td>
      <td>Suite 750</td>
      <td>NYC</td>
      <td>NY</td>
      <td>10022</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Hernandez</td>
      <td>Maria</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>2818</th>
      <td>10350</td>
      <td>20</td>
      <td>100.00</td>
      <td>15</td>
      <td>2244.40</td>
      <td>12/2/2004 0:00</td>
      <td>Shipped</td>
      <td>4</td>
      <td>12</td>
      <td>2004</td>
      <td>...</td>
      <td>C/ Moralzarzal, 86</td>
      <td>NaN</td>
      <td>Madrid</td>
      <td>NaN</td>
      <td>28034</td>
      <td>Spain</td>
      <td>EMEA</td>
      <td>Freyre</td>
      <td>Diego</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2819</th>
      <td>10373</td>
      <td>29</td>
      <td>100.00</td>
      <td>1</td>
      <td>3978.51</td>
      <td>1/31/2005 0:00</td>
      <td>Shipped</td>
      <td>1</td>
      <td>1</td>
      <td>2005</td>
      <td>...</td>
      <td>Torikatu 38</td>
      <td>NaN</td>
      <td>Oulu</td>
      <td>NaN</td>
      <td>90110</td>
      <td>Finland</td>
      <td>EMEA</td>
      <td>Koskitalo</td>
      <td>Pirkko</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>2820</th>
      <td>10386</td>
      <td>43</td>
      <td>100.00</td>
      <td>4</td>
      <td>5417.57</td>
      <td>3/1/2005 0:00</td>
      <td>Resolved</td>
      <td>1</td>
      <td>3</td>
      <td>2005</td>
      <td>...</td>
      <td>C/ Moralzarzal, 86</td>
      <td>NaN</td>
      <td>Madrid</td>
      <td>NaN</td>
      <td>28034</td>
      <td>Spain</td>
      <td>EMEA</td>
      <td>Freyre</td>
      <td>Diego</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>2821</th>
      <td>10397</td>
      <td>34</td>
      <td>62.24</td>
      <td>1</td>
      <td>2116.16</td>
      <td>3/28/2005 0:00</td>
      <td>Shipped</td>
      <td>1</td>
      <td>3</td>
      <td>2005</td>
      <td>...</td>
      <td>1 rue Alsace-Lorraine</td>
      <td>NaN</td>
      <td>Toulouse</td>
      <td>NaN</td>
      <td>31000</td>
      <td>France</td>
      <td>EMEA</td>
      <td>Roulet</td>
      <td>Annette</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>2822</th>
      <td>10414</td>
      <td>47</td>
      <td>65.52</td>
      <td>9</td>
      <td>3079.44</td>
      <td>5/6/2005 0:00</td>
      <td>On Hold</td>
      <td>2</td>
      <td>5</td>
      <td>2005</td>
      <td>...</td>
      <td>8616 Spinnaker Dr.</td>
      <td>NaN</td>
      <td>Boston</td>
      <td>MA</td>
      <td>51003</td>
      <td>USA</td>
      <td>NaN</td>
      <td>Yoshido</td>
      <td>Juri</td>
      <td>Medium</td>
    </tr>
  </tbody>
</table>
<p>20 rows × 25 columns</p>
</div>




```python
# Identify the type of df object
type(df)
```




    pandas.core.frame.DataFrame




```python
# Total number of elements in the Data Frame
df.size
```




    70575




```python
# Number of rows and columns (similar to dim() function in R)
df.shape
```




    (2823, 25)




```python
df.info

```




    <bound method DataFrame.info of       ORDERNUMBER  QUANTITYORDERED  PRICEEACH  ORDERLINENUMBER    SALES  \
    0           10107               30      95.70                2  2871.00   
    1           10121               34      81.35                5  2765.90   
    2           10134               41      94.74                2  3884.34   
    3           10145               45      83.26                6  3746.70   
    4           10159               49     100.00               14  5205.27   
    ...           ...              ...        ...              ...      ...   
    2818        10350               20     100.00               15  2244.40   
    2819        10373               29     100.00                1  3978.51   
    2820        10386               43     100.00                4  5417.57   
    2821        10397               34      62.24                1  2116.16   
    2822        10414               47      65.52                9  3079.44   
    
                ORDERDATE    STATUS  QTR_ID  MONTH_ID  YEAR_ID  ...  \
    0      2/24/2003 0:00   Shipped       1         2     2003  ...   
    1       5/7/2003 0:00   Shipped       2         5     2003  ...   
    2       7/1/2003 0:00   Shipped       3         7     2003  ...   
    3      8/25/2003 0:00   Shipped       3         8     2003  ...   
    4     10/10/2003 0:00   Shipped       4        10     2003  ...   
    ...               ...       ...     ...       ...      ...  ...   
    2818   12/2/2004 0:00   Shipped       4        12     2004  ...   
    2819   1/31/2005 0:00   Shipped       1         1     2005  ...   
    2820    3/1/2005 0:00  Resolved       1         3     2005  ...   
    2821   3/28/2005 0:00   Shipped       1         3     2005  ...   
    2822    5/6/2005 0:00   On Hold       2         5     2005  ...   
    
                           ADDRESSLINE1  ADDRESSLINE2           CITY STATE  \
    0           897 Long Airport Avenue           NaN            NYC    NY   
    1                59 rue de l'Abbaye           NaN          Reims   NaN   
    2     27 rue du Colonel Pierre Avia           NaN          Paris   NaN   
    3                78934 Hillside Dr.           NaN       Pasadena    CA   
    4                   7734 Strong St.           NaN  San Francisco    CA   
    ...                             ...           ...            ...   ...   
    2818             C/ Moralzarzal, 86           NaN         Madrid   NaN   
    2819                    Torikatu 38           NaN           Oulu   NaN   
    2820             C/ Moralzarzal, 86           NaN         Madrid   NaN   
    2821          1 rue Alsace-Lorraine           NaN       Toulouse   NaN   
    2822             8616 Spinnaker Dr.           NaN         Boston    MA   
    
         POSTALCODE  COUNTRY TERRITORY CONTACTLASTNAME CONTACTFIRSTNAME DEALSIZE  
    0         10022      USA       NaN              Yu             Kwai    Small  
    1         51100   France      EMEA         Henriot             Paul    Small  
    2         75508   France      EMEA        Da Cunha           Daniel   Medium  
    3         90003      USA       NaN           Young            Julie   Medium  
    4           NaN      USA       NaN           Brown            Julie   Medium  
    ...         ...      ...       ...             ...              ...      ...  
    2818      28034    Spain      EMEA          Freyre            Diego    Small  
    2819      90110  Finland      EMEA       Koskitalo           Pirkko   Medium  
    2820      28034    Spain      EMEA          Freyre            Diego   Medium  
    2821      31000   France      EMEA          Roulet          Annette    Small  
    2822      51003      USA       NaN         Yoshido             Juri   Medium  
    
    [2823 rows x 25 columns]>




```python

```
