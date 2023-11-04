# Parcels-Delivery-Analysis

*Note: Github cannot render plotly charts. To see the plots in the jypyter notebook file "analysis.ipynb", download and open the file on your local computer.*

## Dataset
This project contains 2 datasets:
- parcel_table: information about parcels such as pickup_date, final_delivery_date, origin_country, carrier_name, etc..
- log_table: detailed logs of delivery date prediction

## Outline
1. Import & Setup
2. Questions to analyze
3. Preprocessing
4. Analysis
5. Conclusoin

### 1. Questions 
1. Which carrier has the highest EDD accuracy percentage
2. How accurate is EDD?
3. Successful delivery rate
4. Are there any abnormality in the parcels?
5. Characteristics of the accurate EDDs vs inaccurate EDDs.

### 2. Data Pre-processing
Parcel table:
- drop duplicates
- drop cols with lots of missing values
- fillna for some columns
- abnormal values

Log table:
- drop duplicates
- extract columns from json
- remove duplicated consecutive EDD

Final table:
- merge parcel_table & log_table
- add columns: EDD_is_accurate, is_abnormal, daydiff_bw_FDD_EDD, daydiff_log_FDD,...
- remove abnormal EDDs/parcels

### 3. Explorative Data Analysis
Some examples of my analysis:

i. EDD frequency
![EDD-frequency](https://github.com/thuminhle59/Parcels-Delivery-Analysis/blob/main/Images/EDD-freq.png)
- Among 80.67% (2,576) parcels having only 1 unique EDD, there are 994 (31.01%) parcels have accurate EDDs.

- Only 19.63% (629) parcels have more than 1 unique EDD, and 6.74% (216) of which have accurate EDDs.

ii. Delivery duration
![Delivery-duration](https://github.com/thuminhle59/Parcels-Delivery-Analysis/blob/main/Images/Delivery-duration.png)

- Longer delivery duration has higher edd accuracy per parcel and vice versa.

- Delivery duration > 7.49 hrs has the highest accuracy percentage (46.57 %)

- Whereas duration 0 - 2.27 hrs has the lowest accuracy percentage (26.93 %).

iii. Delivery time
![Delivery-time](https://github.com/thuminhle59/Parcels-Delivery-Analysis/blob/main/Images/Delivery-time.png)

- 75% total parcels (2,382 parcels) were delivered during midnight hours from 0am to 6am, and 41.39% of them (986 parcels) have accurate EDDs.

- Only 25% total parcels (823 parcels) were delivered during daytime from 6am to 0am, and only 27.22% of them (224 parcels) have accurate EDDs
  
### 4. Conclusion

**1. CARRIERS' VOLUME AND EDD ACCURACY**

- 37.75% of total volume (1,210 parcels) have accurate EDDs.

- Globex has the lowest parcels volume (45 parcels), but highest percentage of accurate EDD parcels (93.33%).

- Initech has the highest parcels volume (3,069 parcels), but low percentage of accurate EDD parcels (37.15%).

**2. SUCCESSFUL DELIVERY RATE**

- 86.05% (2,758) of total parcels were delivered on first attempt.

- All 3 carriers has > 85% successful delivery percentage on first attempt.

**3. CHARACTERISTICS OF ACCURATE EDDs PARCELS**

i. EDDs Frequency

- Among 80.67% (2,576) parcels having only 1 unique EDD, there are 994 (31.01%) parcels have accurate EDDs.

- Only 19.63% (629) parcels have more than 1 unique EDD, and 6.74% (216) of which have accurate EDDs.

ii. Earliest day that all EDDs per parcel were predicted accurately is 8.84 days before the final delivery date.

iii. Longer delivery duration has higher EDD accuracy per parcel.

iv. Final delivery time of day

- 75% total parcels (2,382 parcels) were delivered during midnight hours from 0am to 6am, and 41.39% of them (986 parcels) have accurate EDDs.

- Only 25% total parcels (823 parcels) were delivered during daytime from 6am to 0am, and only 27.22% of them (224 parcels) have accurate EDDs

**4. CHARACTERISTICS OF INACCURATE EDDs PARCELS**

- EDD predicted closer to final delivery date has higher edd inaccuracy per parcel and vice versa.

- Delivery time of day from 6am to 0am has highest inaccuratcy edd percentage.

- 1.28% parcels were predicted to be delivered before prediction date, which is obviously inaccurate.
