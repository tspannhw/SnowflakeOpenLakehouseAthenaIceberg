## SnowflakeOpenLakehouseAthenaIceberg

Snowflake Open Lakehouse on AWS with Athena and Apache Iceberg Tables


### AWS Athena

* Create a database
* Create an iceberg table in the S3 Bucket we have setup and a new directory for that table
* Describe this new table in detail
* Insert two records
* Example query


`````
create database tspann

CREATE TABLE sales_data (sales_id BIGINT, item_name STRING,
sale_date DATE, revenue double)
LOCATION 's3://se-tspann-apacheiceberg/sales_data/'
TBLPROPERTIES ( 'table_type' = 'ICEBERG','format' = 'PARQUET')

describe formatted sales_data

# Table schema:		
# col_name	data_type	comment
sales_id	bigint	
item_name	string	
sale_date	date	
revenue	double	
		
# Partition spec:		
# field_name	field_transform	column_name
		
Name:	iceberg.tspann.sales_data	
Location:	s3://se-tspann-apacheiceberg/sales_data	
		
# Table properties:		
# key	value	
format	PARQUET	
write_compression	zstd	
		
# Iceberg storage table properties:		
# key	value	
write.format.default	PARQUET	
write.object-storage.enabled	true	
write.object-storage.path	s3://se-tspann-apacheiceberg/sales_data/data	
write.parquet.compression-codec	zstd

INSERT INTO sales_data
VALUES 
    (103, 'Laptop', DATE '2025-11-04', 1800.00),
    (104, 'Mouse', DATE '2025-11-05', 15.20)

select * 
from sales_data
order by sale_date desc

#	sales_id	item_name	sale_date	revenue
1	2400	Resistance Bands	2025-12-05	37.1
2	106	Mouse	2025-12-05	17.61
3	2100	Water Bottle	2025-12-04	11.08
4	105	Laptop	2025-12-04	2250.99
5	5055	Water Bottle	2025-12-02	13.05
6	3935	Whiteboard	2025-11-29	85.05
7	2406	Bluetooth Speaker	2025-11-29	518.88
8	5895	Magazine Subscription	2025-11-28	25.34
9	2075	Bluetooth Speaker	2025-11-27	273.05
10	5234	Mechanical Keyboard	2025-11-26	171.57
11	1739	Protein Powder	2025-11-25	73.25
12	1096	Dumbbells Set	2025-11-24	487.6
13	2951	Standing Desk	2025-11-23	912.61
14	1948	Technical Book	2025-11-22	157.88
15	4920	Humidifier	2025-11-19	164.33
16	5553	Printer Paper	2025-11-19	65.46
17	5347	Toaster	2025-11-19	65.58
18	4454	Wireless Mouse	2025-11-18	45.79
19	3155	Whiteboard	2025-11-18	134.77
20	4855	RAM Module	2025-11-17	140.4
21	4778	External SSD	2025-11-17	225.91
22	2470	Protein Powder	2025-11-16	43.14
23	2932	Bluetooth Speaker	2025-11-14	1013.86
24	2633	Printer	2025-11-14	134.97
25	5506	Blender	2025-11-13	99.21
26	3501	Robot Vacuum	2025-11-12	796.95
27	4822	Water Bottle	2025-11-11	25.29
28	3223	RAM Module	2025-11-11	177.92
29	1737	Toaster	2025-11-09	82.04
30	5730	Air Purifier	2025-11-09	168.25
31	4873	Graphics Card	2025-11-09	1054.49
32	5385	Electric Kettle	2025-11-09	58.37
33	5032	Graphics Card	2025-11-08	821.94
34	2082	Tablet	2025-11-07	205.47
35	1499	Bluetooth Speaker	2025-11-07	156.3
36	4796	Running Shoes	2025-11-06	107.42
37	4747	Magazine Subscription	2025-11-06	42.66
38	3264	Treadmill	2025-11-06	704.29
39	4485	Graphics Card	2025-11-06	716.34
40	5774	Protein Powder	2025-11-05	45.4
41	5364	Filing Cabinet	2025-11-05	211.89
42	104	Mouse	2025-11-05	15.2
43	1688	Smartwatch	2025-11-05	383.75
44	3408	Gaming Monitor	2025-11-04	915.32
45	1693	Water Bottle	2025-11-04	14.29
46	103	Laptop	2025-11-04	1800.0
47	2169	Bluetooth Speaker	2025-11-04	119.57
48	3251	Coffee Maker	2025-11-02	134.91
49	2170	Air Purifier	2025-11-02	383.03
50	102	Mouse	2025-11-02	25.5
51	3641	Vacuum Cleaner	2025-11-02	452.97
52	3244	External SSD	2025-11-01	225.08
53	101	Laptop	2025-11-01	1200.0
54	4556	Microwave	2025-10-31	119.81
55	3337	Notebooks	2025-10-31	24.71
56	4544	Blender	2025-10-30	143.11
57	5542	Dumbbells Set	2025-10-30	139.34
58	4965	Business Book	2025-10-30	40.92
59	3638	Printer	2025-10-30	226.27
60	4460	Paper Shredder	2025-10-30	107.68
61	2018	Business Book	2025-10-29	34.44
62	3486	Notebooks	2025-10-29	45.38
63	3045	Mechanical Keyboard	2025-10-29	118.2
64	1567	Sports Bag	2025-10-28	369.53
65	2445	Standing Desk	2025-10-28	430.63
66	1704	Exercise Bike	2025-10-28	242.61
67	4041	Smartphone	2025-10-28	941.55
68	3389	External SSD	2025-10-27	258.79
69	1147	Filing Cabinet	2025-10-27	95.17
70	5612	Water Bottle	2025-10-26	13.8
71	2217	Filing Cabinet	2025-10-26	128.56
72	5389	Whiteboard	2025-10-25	83.29
73	3820	Smartphone	2025-10-25	908.25
74	2740	Filing Cabinet	2025-10-24	117.43
75	1253	Yoga Mat	2025-10-24	31.46
76	1495	Vacuum Cleaner	2025-10-24	359.31
77	5440	External SSD	2025-10-23	83.01
78	5026	Whiteboard	2025-10-23	236.49
79	3691	Toaster	2025-10-23	67.6
80	2808	Bluetooth Speaker	2025-10-21	28.82
81	4137	Running Shoes	2025-10-21	173.42
82	1555	Dumbbells Set	2025-10-21	266.02
83	4133	Standing Desk	2025-10-21	757.86
84	4863	Air Purifier	2025-10-20	152.82
85	2010	Microwave	2025-10-20	214.95
86	1707	Robot Vacuum	2025-10-20	772.67
87	5452	Laptop	2025-10-20	1137.54
88	5876	Graphics Card	2025-10-19	1385.66
89	3966	Desk Lamp	2025-10-19	34.3
90	5236	Online Course	2025-10-19	223.64
91	4784	Tablet	2025-10-18	745.3
92	1893	Notebooks	2025-10-18	20.14
93	5964	Printer	2025-10-18	256.92
94	3707	Desk Lamp	2025-10-17	88.37
95	2915	Air Fryer	2025-10-17	148.7
96	5535	Paper Shredder	2025-10-16	55.16
97	4449	Office Chair	2025-10-16	295.44
98	2487	Gaming Monitor	2025-10-16	641.28
99	4481	Paper Shredder	2025-10-16	160.95
100	1904	Wireless Mouse	2025-10-15	58.03


`````


<img width="2503" height="1247" alt="image" src="https://github.com/user-attachments/assets/86bd3719-ef6f-475a-b719-b5629e2bdb37" />



### AWS Configuration - Role


<img width="2223" height="982" alt="image" src="https://github.com/user-attachments/assets/a327ca3c-6c4b-4218-a4f5-0d5c3e7f051c" />

<img width="1657" height="625" alt="image" src="https://github.com/user-attachments/assets/a841557d-4b97-4318-8354-5adbaa589f5a" />




### AWS Configuration - IAM Policy


<img width="2247" height="790" alt="image" src="https://github.com/user-attachments/assets/2e2f6d81-ed05-439d-add0-6dd67e835340" />

<img width="1642" height="1035" alt="image" src="https://github.com/user-attachments/assets/2aaa0174-169d-4bae-a511-a633f03c3060" />


### AWS S3 Apache Iceberg

<img width="2230" height="888" alt="image" src="https://github.com/user-attachments/assets/efd7b148-0c44-4915-8e46-10d74ae00e15" />

<img width="2226" height="402" alt="image" src="https://github.com/user-attachments/assets/40d3f9a9-b6e4-4897-a213-d53f04ed32cf" />

<img width="2238" height="619" alt="image" src="https://github.com/user-attachments/assets/a94dfb6e-7c59-4804-b772-86bd4c797d91" />



### Snowflake Tables


### Snowflake Create Catalog Integration to AWS Glue

`````
CREATE CATALOG INTEGRATION glue_rest_catalog_int
  CATALOG_SOURCE = ICEBERG_REST
  TABLE_FORMAT = ICEBERG
  CATALOG_NAMESPACE = 'tspann'
  REST_CONFIG = (
    CATALOG_URI = 'https://glue.us-east-1.amazonaws.com/iceberg'
    CATALOG_API_TYPE = AWS_GLUE
    CATALOG_NAME = 'YOUR12DIGITAWSACCOUNT'
  )
  REST_AUTHENTICATION = (
    TYPE = SIGV4
    SIGV4_IAM_ROLE = 'arn:aws:iam::YOUR12DIGITAWSACCOUNT:role/tspann-glue-athena-s3-iceberg-role'
    SIGV4_SIGNING_REGION = 'us-east-1'
  )
  ENABLED = TRUE;

`````

### Snowflake Examine New Glue REST Integration 

* Get values and set in role
* API_AWS_IAM_USER_ARN
* API_AWS_EXTERNAL_ID

`````
  DESCRIBE CATALOG INTEGRATION glue_rest_catalog_int;

`````


### Snowflake - Create table

`````

CREATE ICEBERG TABLE SALES_DATA_ICEBERG_RW
CATALOG = glue_rest_catalog_int
EXTERNAL_VOLUME = TRANSCOM_TSPANNICEBERG_EXTVOL
CATALOG_TABLE_NAME = 'sales_data'
CATALOG_NAMESPACE = 'tspann';


`````

### Snowflake - Query and Examine Table


`````

SELECT item_name, SUM(revenue) AS total_revenue
FROM DEMO.DEMO.SALES_DATA_ICEBERG_RW
GROUP BY 1;

SHOW ICEBERG TABLES
->> SELECT *
FROM $1
WHERE "catalog_name" = 'glue_rest_catalog_int';


`````


### Snowflake - Test an Insert

`````

INSERT INTO DEMO.DEMO.SALES_DATA_ICEBERG_RW
VALUES 
    (105, 'Laptop', DATE '2025-12-04', 2250.99),
    (106, 'Mouse', DATE '2025-12-05', 17.61);

`````
  
<img width="926" height="1190" alt="image" src="https://github.com/user-attachments/assets/b9a9fa47-c84b-4cff-9f2d-7fe6395f1df5" />


### Resources

* https://www.snowflake.com/en/engineering-blog/snowflake-platform-data-lake/
* https://docs.snowflake.com/en/sql-reference/sql/create-iceberg-table-aws-glue
* https://docs.snowflake.com/en/user-guide/tables-iceberg-configure-catalog-integration-glue 




### Parquet File Rapid Copy



<img width="3494" height="1683" alt="image" src="https://github.com/user-attachments/assets/c3b54cc9-1f72-4b4a-ba7a-28463aa77545" />
