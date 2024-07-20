# AtliQ-Hardware-Sales-Finance-Analytics

# About: 
AtliQ Hardware is a company that sales hardware like PC, Mouse, Printer etc. to different customer, then this store sells hardware to the end consumer. They have two types of customers which 

**1.	Brick & Mortar**(Croma)

**2.	E-Commerce** (Flipkart)

They run their business through three different channels

**1.	Retailer** (Croma, Flipkart)

**2.	Distributor** (Neptune in south Korea)

**3.	Direct** (AtliQ E-store, AtliQ Exclusive)

# Objective: 

Now the Management of AtliQ Hardware onboard analytics to know the Sales and Financial health of the company to expand their business in others segment. They want majorly two reports

**A.	Customer Performance**

**B.	Market Performance vs.Target**

# Sales Analytics: 
The analysis process starts through the **ETL (Extract, Transform and Load)** process in power query by load the datasets given the data engineer of AtliQ Hardware, which are

**1.	Fact_sales_monthly**

**2.	Dim_product**
	
**3.	Dim_market**

**4. Dim_customer**

After performing some important transformation, a new data set this added, which is, dim_date by this formula 
               
            = {Number. Form (#date (2018,9,1)) ……Number. Form (#date (2021,8,1))}
            

When all the transformation is completed, the next important step is starting which data modelling, to get correct DAX measures for our analysis. In the entire modelling process, we were trying to maintain the star schema to make it simple for the analysis. 

After that using multiple DAX measure (which I mention below) finally we got our desired output, which are,


**1.	Customer Performance Report**

**2.	Market performance vs Target**

**3.	Division Report**

**4.	Top & Bottom products** 

**5.	New product in 2021**

**6.	Top 10 products**

**7.	Top 5 countries**


# Finance Analytics:

For the Finance part we continue our problem-solving approach in the same the project where we stop our sales analytics. We add **fiscal year and performance target for 2021** provided by the data engineering department of AtliQ Hardware. 

The analysis in finance data give us four important reports which are,

**1.	P & L By Fiscal Year**

**2.	P & L By Month & Quarter**

**3.	GM% by Quarters (sub_zone)**

**4.	P & L for Markets**

# Key Takeaways: 

1.	AtliQ Hardware launch **16** new products in **2021**
2.	**Amazon** is the best customer in terms of net sales.
3.	**P & A** division is the most demandable division in terms of net sales in **2020** and **2021** both.
4.	In market **India** performs very well in terms of net sales

# DAX Measures use in this project: 

        =SUM (fact_sales_monthly)[net_sales_amount]

        =CALCULATE ([net sales], dim_date[FY] = “2019”)
        
        =DIVIDE ([net sales 21],[net sales 20],0)

        =SUM (ns_target_2021[ns_target])

        =FORMAT([date],” mmm”)

        =MONTH(DATE(YEAR([date]), MONTH([date])+4,1))

        =“Q” & ROUNDUP([fy_month_no]/3,0)
