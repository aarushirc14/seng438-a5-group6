**SENG 438- Software Testing, Reliability, and Quality**

**Lab. Report #5 – Software Reliability Assessment**

|                 |
| --------------- |
| Group: 6        |
| Jonathan        |
| Dongwook (Luke) |
| Aarushi         |


# Introduction

In this lab we learnt about assessing the reliability of a hypothetical system given its failure data collected during integration testing. We used two methods to assess the failure data, including Reliability Growth Testing (RGT or RGA) and Reliability Demonstration Chart (RDC) with tools like C-SFRAT, SRTAT. 


# Assessment Using Reliability Growth Testing


## Result of model comparison (selecting top two models)

**Top 2 models:**

1. DW3 with Covariate F 
2. IFRGSB with Covariates E,F

For this part of the assignment we used C-SFRAT and the first step was compiling a CSV file with the following values: Time interval (T), Failure Count (FC), Execution time measured in hours (E), Failure identification work measured in person hours(F) and Computer time failure identification measured in hours(C). A mix of different data sets from the one’s provided in the assignment artifacts were combined to get the values for the CSV file.

  
  
  
  
  
  
  
  


The imported data initially looked like this:

![](https://lh6.googleusercontent.com/BilyUjxhNH-N2NuYOfaSQ0pu5Vu00um4JWO7wII6S5MltQ0qIDVyKrPr0Y0wE6kmBu2lDNLFIqg1Nqc_-zHkz9qoii6hixnxEQ26CP1YZO_Ksnl9DYxVuyKswtyFxXHIk0m_TA-lrVL574UB3puWRtQ)

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  


Then we generated the models with all the “hazard function” and “covariates” to get the maximum number of model possibilities so we can find the closest fit:

![](https://lh4.googleusercontent.com/EBq91uSQqWHJv-DBDG-QGq77cWQk1S2HyC0e_GHAyLMYOQ9zhr2o4U8Eql6ecex1dmSvnVQKHyAsVe31-FJ0pbbCnGRymOjsv226LGSVFNv88rPhG_m0gfPDgVPj2XlmEg8GZSee7ykA3tX0upMmLoE)

Then we sorted the log-likelihood values in descending order to find which models had the greatest log-likelihood:

![](https://lh6.googleusercontent.com/SNXRquqISZo9q1XfL5ps2SPw0RAM_kbKD79bJMYNyFcGhFoX4dMChb8bYum2yj6IanyhnF1HTBY_qCLurme4lOgcvLlY0Nh_z86d-DAkxATjS4HOLK7elrPk_S8ZYlHOwcFaDC-cuVYcpkK6knlvEBo)

From the chart above we can see that model 32 and 11 are the **top 2 closest fit: DW3 with Covariate F and IFRGSB with Covariates E,F**. DW3 stands for Discrete Weibull (Type III) and IFRGSB stands for IFR generalized Salvia and Bollinger.


## Result of range analysis (an explanation of which part of the data is good for proceeding with the analysis)

We used the Laplace trend test to analyze the range of data. A score greater than 1.96 indicates we are at least 95% confident that there is a significant trend upward and that this data is good for proceeding with the analysis.

Formula for laplace test:

![](https://lh5.googleusercontent.com/DY7QhR3LIgPVkrKPuJYW-iofw4XrZSTioFPlNgB9xMI8EnBxdNdYMhLUvAD_9u-5bo4-LHKJjyR40Qx6V1P1WK_1wonl-x5MCwKogUpye0dt26TGDAyASk1IHccwV_tndwpKzK14IKnEictZpNJ1mYM)

Results of the Laplace Test

|              |              |                       |                   |
| ------------ | ------------ | --------------------- | ----------------- |
| **Time (T)** | **FC**       | **Cumulative FC (n)** | **Laplace Score** |
| 1            | 2            | 2                     | \-0.724744871     |
| 2            | 11           | 13                    | \-0.249615231     |
| 3            | 2            | 15                    | \-0.047213595     |
| 4            | 4            | 19                    | 0.128956082       |
| 5            | 3            | 22                    | 0.312543709       |
| 6            | 1            | 23                    | 0.551885919       |
| 7            | 1            | 24                    | 0.813113276       |
| 8            | 2            | 26                    | 1.044932274       |
| 9            | 4            | 30                    | 1.183772234       |
| 10           | 0            | 30                    | 1.517105567       |
| 11           | 4            | 34                    | 1.644132208       |
| 12           | 1            | 35                    | 1.935801407       |
| 13           | 3            | 38                    | 2.113761099       |
| 14           | 0            | 38                    | 2.482182151       |
| 15           | 1            | 39                    | 2.799572979       |
| 16           | 1            | 40                    | 3.126138721       |
| 17           | 2            | 42                    | 3.375595901       |
| 18           | 1            | 43                    | 3.712608914       |
| 19           | 8            | 51                    | 3.482954571       |
| 20           | 9            | 60                    | 3.276393202       |
| 21           | 6            | 66                    | 3.286799284       |
| 22           | 7            | 73                    | 3.263032211       |
| 23           | 4            | 77                    | 3.387030076       |

From the table above we can see the range from T=13 to T=23 has scores greater than 1.96 so this data is good for proceeding with the analysis.


## 


## 


## Plots for failure rate and reliability of the SUT for the test data provided

**MVF (Mean Value Function Graph) of imported data and top 2 models in C-SFRAT**

![](https://lh6.googleusercontent.com/jqjuXgAYWBJe0atZmBa2gQTiS7SZ3Ycwqz6s8TeBL162VYpKIlGio9W6OoU5pqOruNLcPTj74Cc2ObjnY321VZy5ialeDGtCrZFNuI8kBZmm_gKzDTbZgZ45Hde3YEFDtREi-SjgFzkjgMeleTA_xjQ)

**Intensity Graph of imported data and top 2 models in C-SFRAT**

![](https://lh5.googleusercontent.com/RFaC8tcukn6drSdixug7ZVdrbUyszU_bPZM7C5vMu_KYQig7aLn7PEkjUUVMBk2bnKPRaU3MZH6dbmSAs9Edf4gvMZNdIlzEUA-t-olheuBJsNf7KEMBSofgRmEK09QtR47lfRGrPsTMlRdxPVLMVLI)

  


**Geometric Trend Analysis Graph using time between failure option with SRTAT**

![](https://lh5.googleusercontent.com/EM9z6cUz7zwUB_Fk7FBGS84RpCwu2cztT-YzDfNCu9_KMnR5DfyCmd_kdNf-jbdxHwIJITmUpa3cBw59heVnWb2Glr6xgQPvMcjuPNCYgUmgeH1sva-CywRfabh1ijWNMCrAWBZm6BqaiZw94Tq0PmY)

**Littlewood and Varral’s Bayesian Reliability Prediction Graph with SRTAT**

![](https://lh3.googleusercontent.com/omcwjYfPskyqzWNXH_hlTyCjVE5J1u_gwdfGUWMQXk1V2Z4Y1OhBqe-2ybSGqjDNv8MH-cSO0zoMZS0nldY7ZuruWFGh5p4edBvVcGpRX5aFS8GzksjoaTA6BLhiamJ224mWZUgEbIaS79pRrTNk9k8)


## A discussion on decision making given a target failure rate

Given a target failure rate and model parameters we can predict the remaining failures in the system and estimate the time to release. The selected reliability models from the previous sections fit the failure data against a model. Through reliability acceptance analysis a decision can be made on whether the system is acceptable to be released. A target failure rate ensures reliability and by identifying the lowest failure intensity for the models in the failure intensity graph, a desired failure rate prediction using C-SFRAT was set to 0.5 to be predicted in 50 intervals. This target failure rate can be said to be MTTF = 0.5/50 = 0.01.


## A discussion on the advantages and disadvantages of reliability growth analysis

Reliability growth analysis (RGA) is a statistical method used to assess the reliability of a system, product or process over time. It involves the analysis of data collected during testing and evaluation of the system, and it aims to identify and quantify improvements in system reliability that occur during the testing process. 

Advantages:

- The graphs show trends so we can make decisions based on the system’s past behavior and use that data to predict its future behavior.
- Allows us to measure improvements and estimate release dates plus how much more time and resources may be required to do more testing/development.
- Easier to capture and examine changes/failures at a specific point in time and to assess the impact of that change.

Disadvantages:

- Can be tedious or time consuming which increases the cost of testing.
- Choice of tool can have a big impact. Different tools can visualize the same data in different ways and produce different results for the graphs.
- The prediction models can differ based on the mathematical functions used in determining a target failure for the system.








# Assessment Using Reliability Demonstration Chart

Using CSR1.DAT in Time_Between_Failures Folder:

minMTTF = Failure time / Normalized Failure Data (Tn)

When Failure Time = 1, Normalized Measure (MTTFs) = 30

Thus minMTTF = 1/30 = 0.0333…


## 3 plots for MTTFmin, twice and half of it for your test data

**MTTFmin**

**![](https://lh5.googleusercontent.com/cH7U4GXmzbRQ_73G8ZyvFwatLdeZbPVJwTNLKU3dncf-xycjqQFsOQuflHzqilTLWo-yvN87ioAQcezLlqKhpJOSTPtjK9_8X6Y-e9zEAeKkRSgvHrv6y2cXyCRvJsrqjCI-RbUcFWXjrUIGGKxY3F0)**

  
  


**Half MTTFmin**

**![](https://lh3.googleusercontent.com/GT79BR_BvuaROQCwIA3_-ZjcDjS-BPQ2sAgxY9LtkeDUJo3h6UL6O_W_UTonfN513VN9vIKuYaEUwHCsZ97QzVCh9cFUFqs6d8FfphG7X2v36sjAA90e2N636dxx6zg0xIu69mxfTfAolf2kY3vaEPs)**

This graph shows that when the minimum MTTF is halved, the data points from the SUT slide to the left, rejecting part of the system.

  
  
  
  
  
  
  
  
  
  
  


**Twice MTTFmin**

**![](https://lh5.googleusercontent.com/pbRAE8rGqrgjX8MI9_HsMwR5H-puMp-NeW_B3_i1HdqOuAaxJOX0I-x0pMxZt08vgoqepFsT7zDVKecCQtIkGl3knz8TMS0Wg4vE6O8xLfQiyhRaCN0b8_l4DTdETCnoZybJSrL-hNugNF8GM2Tlt9w)**

This graph shows that when the minimum MTTF is doubled, the data points from the SUT slide to the right making the entire system acceptable. 













## Explain your evaluation and justification of how you decide the MTTFmin

We identified the Mean Time To Failure (MTTF) based on where the data points would be on the border of being accepted. This meant that the data point closest to the accepted border would be where the minimum MTTF would be assigned. This is because it is the minimum in which the system under test becomes acceptable. Given that the normalized failure data is equal to the failure time divided by MTTF. We were then able to produce the Twice MTTFmin and Half MTTFmin graphs. Thus by changing the maximum acceptable number of failures we plotted the  Twice MTTFmin and Half MTTFmin graphs. 


## A discussion on the advantages and disadvantages of RDC

**Advantages:**

- Can be used to predict the reliability of a system over time through estimations and trends
- Allows for a quantitative metric as to how reliable a system is 
- Visually appealing and easy to understand 

**Disadvantages:** 

- Requires lots of data to create making it potentially expensive and timely
- Limited data such as the severity of the failures within the system is presented.


# Comparison of Results with Part 1

In part 1, we used RGA in order to determine coefficients that are closely related to the failures. These coefficients were Execution time measured in hours (E) and Failure identification work measured in person hours (F). This means that by controlling these variables, we should theoretically be able to lower the failure rate. With the given target failure rate and model parameters, we set a desired failure rate prediction in C-SFRAT to 0.5, which was predicted in 50 intervals. This means that the MTTF determined was 0.5/50 = 0.01. On the other hand, in our RDC we calculated the minMTTF using an expected failure time of 1, then dividing it by the normalized measures which was 30. This gave us a minMTTF = 1/30 = 0.0333…  In this methodology, we normalized our failure data in order to compare the actual reliability performance of the system against the expected reliability level. We can clearly see that RDC focuses on meeting a certain bar for reliability (since we are using normalized data), and RGA focuses on identifying the underlying issue in order to improve the overall reliability.


# Discussion on Similarity and Differences of the Two Techniques

Similarities of RDC and RGT:

- Both techniques evaluate the system based on failure data which is collected during integration testing. This data doesn’t need a lot of context other than the frequency of failure, which is determined through time stamps and number of failures.
- MTTF is used in both techniques. In RDC, it was used as a target metric that the system needed to abide by. In RGT, it was used to identify improvements in the reliability of a system over time.

Differences of RDC and RGT:

- RDC determines if a system has satisfied a certain requirement that can deem it reliable. Whereas RGT looks at iterative data points and evaluates the reliability over time. 
- RDC should be used when you want to determine the trend for reliability of a system, given a few failures and their times. 
- RDC is typically used in mature systems, and RGT is typically used in systems still in development.


# How the Team Work/Effort was Divided and Managed

We found this lab a little more difficult to divide compared to previous ones because our fourth teammate dropped the course. Thus the three of us decided to divide the work accordingly:

**Aarushi:** Did the graphs and report for part 1 including: model comparison, laplace test, 

failure rate/intensity/prediction plots, decision making given a target failure rate, pros and cons of RGA.

**Luke:** I validated and compared the results from RGT and RDC, and also discussed the similarity and differences of the two techniques.

**Jonathan:** Created the 3 RDC graphs MTTFmin, 2\*MTTFmin and 0.5\*MTTF min. Also calculated the MTTF and conducted analysis on the RDC graph results.


# Difficulties Encountered, Challenges Overcome, and Lessons Learned

**Jonathan:** I found this lab to be difficult due to the outdated tools being used and vague instructions. Firstly, the SFRAT program was incompatible with Windows 11, Windows 10 and Mac OS. The C-SFRAT program was usable but incompatible with the data provided. Additionally, the Reliability-Demonstration-Chart excel sheet had limited capabilities as it was created on Excel 2003 and only allows you to plot 16 data points at a time. 

**Aarushi:** It was a challenge to run most of the softwares due OS incompatibilities and I had to create a Virtual Machine with Windows XP. CASRE did not run at all on any OS so I had to use Excel to do the Laplace Trend Tests. Additionally so many data files were provided in various formats and all had to be changed before being imported into the softwares. The tools provided had barely any documentation so it was difficult to understand what data inputs are needed and what the results mean.

**Luke:** With the outdated software being used in the lab, it was difficult to conduct several procedures within the lab. I encountered many problems when using the SFRAT program on MacOS and Windows 10 which hindered my ability to perform analysis. When I turned to the excel sheet instead, it was also in a very old format which was limited in functionality when opened up in Excel 2022. 


# Comments/Feedback on the Lab Itself

**Jonathan:** There could have been better communication as to which OS systems are supported by a program. Compatible datasets without the need to manipulate them would save time and energy. 

**Luke:** Overall, this lab was a bit more disorganized and unclear than the previous ones. The software in the instructions was very hard to run and had many OS/environmental restrictions that prevented some of us from conducting parts of the lab.

**Aarushi:** The lab manual should have more detailed instructions and formatted data sets compatible with each tool should be provided.
