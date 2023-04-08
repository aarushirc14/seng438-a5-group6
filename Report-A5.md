# Assignment 5

**SENG 438- Software Testing, Reliability, and Quality**

**Lab. Report #5 – Software Reliability Assessment**

Group: 6

---

Jonathan

---

Dongwook (Luke)

---

Aarushi

---

# Introduction

In this lab we learnt about assessing the reliability of a hypothetical system given its failure data collected during integration testing. We used two methods to assess the failure data, including Reliability Growth Testing (RGT or RGA) and Reliability Demonstration Chart (RDC) with tools like C-SFRAT, SRTAT.

# Assessment Using Reliability Growth Testing

## **Result of model comparison (selecting top two models)**

**Top 2 models:**

1. DW3 with Covariate F
2. IFRGSB with Covariates E,F

For this part of the assignment we used C-SFRAT and the first step was compiling a CSV file with the following values: Time interval (T), Failure Count (FC), Execution time measured in hours (E), Failure identification work measured in person hours(F) and Computer time failure identification measured in hours(C). A mix of different data sets from the one’s provided in the assignment artifacts were combined to get the values for the CSV file.

The imported data initially looked like this:

[https://lh3.googleusercontent.com/thEldHIXV052khefwZhHbmSPUGS7YIOOjp5s4kQ4VGPwLNd7vlRn4dU9iV3F9mDla2BGDWrko4yqhCT5ekq_cTjOfHRvwL8eWbft-qn5ygxGAVG3YJbncxSnwcAFO8BF7h4jexrp38bRFRaFMLu3z8c](https://lh3.googleusercontent.com/thEldHIXV052khefwZhHbmSPUGS7YIOOjp5s4kQ4VGPwLNd7vlRn4dU9iV3F9mDla2BGDWrko4yqhCT5ekq_cTjOfHRvwL8eWbft-qn5ygxGAVG3YJbncxSnwcAFO8BF7h4jexrp38bRFRaFMLu3z8c)

Then we generated the models with all the “hazard function” and “covariates” to get the maximum number of model possibilities so we can find the closest fit:

[https://lh6.googleusercontent.com/qDfgha3fhw6thaxX4XbOrmNm5fYMqrui4DEyNR5KvslyOb7wSL-Mn8xkYkgLAE8WQSNReGx7SubP0LkW3sBB8S4HI_szaad6ptAFV5CWQsHZ4CO-tK7I8p_ocRARLel5loMnyZUTtvHNUsAmDivWI6Q](https://lh6.googleusercontent.com/qDfgha3fhw6thaxX4XbOrmNm5fYMqrui4DEyNR5KvslyOb7wSL-Mn8xkYkgLAE8WQSNReGx7SubP0LkW3sBB8S4HI_szaad6ptAFV5CWQsHZ4CO-tK7I8p_ocRARLel5loMnyZUTtvHNUsAmDivWI6Q)

Then we sorted the log-likelihood values in descending order to find which models had the greatest log-likelihood:

[https://lh4.googleusercontent.com/uX4fqIFdOuv5NPKVP8HSLDv9P_jpC5yq4HFkARm04ppG0wTzHXpT_tJ0PpzMlrXy8hcI80XaXDu_SGo1alL2ybp7eMxTTxrz5pygmomE3mB6hfWb-d758LjGXTSTGxvmATvgCGE_QsEK4oo7n8I5bzQ](https://lh4.googleusercontent.com/uX4fqIFdOuv5NPKVP8HSLDv9P_jpC5yq4HFkARm04ppG0wTzHXpT_tJ0PpzMlrXy8hcI80XaXDu_SGo1alL2ybp7eMxTTxrz5pygmomE3mB6hfWb-d758LjGXTSTGxvmATvgCGE_QsEK4oo7n8I5bzQ)

From the chart above we can see that model 32 and 11 are the **top 2 closest fit: DW3 with Covariate F and IFRGSB with Covariates E,F**. DW3 stands for Discrete Weibull (Type III) and IFRGSB stands for IFR generalized Salvia and Bollinger.

## **Result of range analysis (an explanation of which part of the data is good for proceeding with the analysis)**

We used the Laplace trend test to analyze the range of data. A score greater than 1.96 indicates we are at least 95% confident that there is a significant trend upward and that this data is good for proceeding with the analysis.

Formula for laplace test:

[https://lh4.googleusercontent.com/d7CXBFLitsw0a-rWiKpEEMczg5TaiFbYcEGOciW0tQ4pTIBpb9htDJIgeOg7vZwPVPz6GOWLom6aqYzmYMEeENWrodj0gED0rtjteGyYDEpndzfzPCWGx0dEoxyqsrGffV6Kw1ZaCr6jiURNLPJvRn8](https://lh4.googleusercontent.com/d7CXBFLitsw0a-rWiKpEEMczg5TaiFbYcEGOciW0tQ4pTIBpb9htDJIgeOg7vZwPVPz6GOWLom6aqYzmYMEeENWrodj0gED0rtjteGyYDEpndzfzPCWGx0dEoxyqsrGffV6Kw1ZaCr6jiURNLPJvRn8)

Results of the Laplace Test

| Time (T) | FC | Cumulative FC (n) | Laplace Score |
| --- | --- | --- | --- |
| 1 | 2 | 2 | -0.724744871 |
| 2 | 11 | 13 | -0.249615231 |
| 3 | 2 | 15 | -0.047213595 |
| 4 | 4 | 19 | 0.128956082 |
| 5 | 3 | 22 | 0.312543709 |
| 6 | 1 | 23 | 0.551885919 |
| 7 | 1 | 24 | 0.813113276 |
| 8 | 2 | 26 | 1.044932274 |
| 9 | 4 | 30 | 1.183772234 |
| 10 | 0 | 30 | 1.517105567 |
| 11 | 4 | 34 | 1.644132208 |
| 12 | 1 | 35 | 1.935801407 |
| 13 | 3 | 38 | 2.113761099 |
| 14 | 0 | 38 | 2.482182151 |
| 15 | 1 | 39 | 2.799572979 |
| 16 | 1 | 40 | 3.126138721 |
| 17 | 2 | 42 | 3.375595901 |
| 18 | 1 | 43 | 3.712608914 |
| 19 | 8 | 51 | 3.482954571 |
| 20 | 9 | 60 | 3.276393202 |
| 21 | 6 | 66 | 3.286799284 |
| 22 | 7 | 73 | 3.263032211 |
| 23 | 4 | 77 | 3.387030076 |

From the table above we can see the range from T=13 to T=23 has scores greater than 1.96 so this data is good for proceeding with the analysis.

## 

## 

## **Plots for failure rate and reliability of the SUT for the test data provided**

**MVF (Mean Value Function Graph) of imported data and top 2 models in C-SFRAT**

[https://lh3.googleusercontent.com/xM3ZvrzaKqPnglwAM8NLVj4gVju_tU7SpYyv2ez9xXIAIUs0csTc5FIOZk2d-4xQw1srM3kGEeja4Vq6Ubhia4Ep4QazqWBcllLFSJ5VYRMn1s5K2vSmM84Vjm3dabMlVwovdUY8EGGMlOs5c7uhhxU](https://lh3.googleusercontent.com/xM3ZvrzaKqPnglwAM8NLVj4gVju_tU7SpYyv2ez9xXIAIUs0csTc5FIOZk2d-4xQw1srM3kGEeja4Vq6Ubhia4Ep4QazqWBcllLFSJ5VYRMn1s5K2vSmM84Vjm3dabMlVwovdUY8EGGMlOs5c7uhhxU)

**Intensity Graph of imported data and top 2 models in C-SFRAT**

[https://lh5.googleusercontent.com/BX3QmceBZDiaPSRHPIvQ7Vmg5tYY067u4doCqwmnRApNAMWY521BXe-JfZPj_XRxgLyd4bw9lnsznk1zrWGNgn8ulyCtZyJ9lWlwUctFS1FRVqNsXro8z0x_pvG4qxmqZ-uOWfj4nbrmbeVpPF0L9bw](https://lh5.googleusercontent.com/BX3QmceBZDiaPSRHPIvQ7Vmg5tYY067u4doCqwmnRApNAMWY521BXe-JfZPj_XRxgLyd4bw9lnsznk1zrWGNgn8ulyCtZyJ9lWlwUctFS1FRVqNsXro8z0x_pvG4qxmqZ-uOWfj4nbrmbeVpPF0L9bw)

**Geometric Trend Analysis Graph using time between failure option with SRTAT**

[https://lh5.googleusercontent.com/ZiEyQ7d4kMlXZLucmiTHqpJe_3PyBYQHv6cGkuPa1XeUNL2pDsLXpw9ZO8iWyE1Gp0mXs1mohqVdvOZVEOs76e6va_xUE_AEUwzK3v3LSfQCy7MU1tZc1rLMJzTcWxXpGHIhChvFrzlgjljqdzrBhqc](https://lh5.googleusercontent.com/ZiEyQ7d4kMlXZLucmiTHqpJe_3PyBYQHv6cGkuPa1XeUNL2pDsLXpw9ZO8iWyE1Gp0mXs1mohqVdvOZVEOs76e6va_xUE_AEUwzK3v3LSfQCy7MU1tZc1rLMJzTcWxXpGHIhChvFrzlgjljqdzrBhqc)

**Littlewood and Varral’s Bayesian Reliability Prediction Graph with SRTAT**

[https://lh4.googleusercontent.com/sI5R7VOg_6WOOBOeZVmf4OEhAEqOmxMX6-NZHiM2UN-LkU7mn0pDaEGPIWNlyg_JFQverYtNqRMWFOKxIA8cKFXuEXGaj8oFF96gYhVS-Fx8-GvZq4WWxmR0QLUp9zIDt7GbMgiyBFnEQM3fXI9AZX0](https://lh4.googleusercontent.com/sI5R7VOg_6WOOBOeZVmf4OEhAEqOmxMX6-NZHiM2UN-LkU7mn0pDaEGPIWNlyg_JFQverYtNqRMWFOKxIA8cKFXuEXGaj8oFF96gYhVS-Fx8-GvZq4WWxmR0QLUp9zIDt7GbMgiyBFnEQM3fXI9AZX0)

## **A discussion on decision making given a target failure rate**

Given a target failure rate and model parameters we can predict the remaining failures in the system and estimate the time to release. The selected reliability models from the previous sections fit the failure data against a model. Through reliability acceptance analysis a decision can be made on whether the system is acceptable to be released. A target failure rate ensures reliability and by identifying the lowest failure intensity for the models in the failure intensity graph, a desired failure rate prediction using C-SFRAT was set to 0.5 to be predicted in 50 intervals. This target failure rate can be said to be MTTF = 0.5/50 = 0.01.

## **A discussion on the advantages and disadvantages of reliability growth analysis**

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

## **3 plots for MTTFmin, twice and half of it for your test data**

**MTTFmin**

[https://lh4.googleusercontent.com/WV5OYQDqWbCSBYl_g8fgAV4o_pJpmAA6r_QMPIRm2rXvp7-WqeN-41y1_5QZOxRH0QPdEkKqrK06OCG-2fO7w_YaSHSkpfz9it0AdJAuXqUNpRblOKKCGYZBJrlW88TdAqLhrLp82qs2mt5ioBKVPaw](https://lh4.googleusercontent.com/WV5OYQDqWbCSBYl_g8fgAV4o_pJpmAA6r_QMPIRm2rXvp7-WqeN-41y1_5QZOxRH0QPdEkKqrK06OCG-2fO7w_YaSHSkpfz9it0AdJAuXqUNpRblOKKCGYZBJrlW88TdAqLhrLp82qs2mt5ioBKVPaw)

**Half MTTFmin**

[https://lh3.googleusercontent.com/RLYGcmWHYS_f_1XVVG6D4Ihxni97srW9RnTizDlcIggTPhGhji_Xhwd_ZASEviPh6XAOmFxfUMWYAMC8D94_BKVQyu6lpsBmJPgIKpyDhgKxxTcSFiI4MrXA84ByZhhJUruBZVtyfGY0kcq3NykNfvk](https://lh3.googleusercontent.com/RLYGcmWHYS_f_1XVVG6D4Ihxni97srW9RnTizDlcIggTPhGhji_Xhwd_ZASEviPh6XAOmFxfUMWYAMC8D94_BKVQyu6lpsBmJPgIKpyDhgKxxTcSFiI4MrXA84ByZhhJUruBZVtyfGY0kcq3NykNfvk)

This graph shows that when the minimum MTTF is halved, the data points from the SUT slide to the left, rejecting part of the system.

**Twice MTTFmin**

[https://lh4.googleusercontent.com/_mlUyVsTO_9rj1W5G3sjuh8FSPAM6psEaAAYbGmmrX5S7s_A8lrqf15AGpZDYW4In7D0EPE3zYTMwe6T7L0VLjA0BKcf4sIoN_WUd6jUWYEXQFkjqk87jyatnIL_eQpVI4hCY-5DRJ6cFjeeHHd2ZPY](https://lh4.googleusercontent.com/_mlUyVsTO_9rj1W5G3sjuh8FSPAM6psEaAAYbGmmrX5S7s_A8lrqf15AGpZDYW4In7D0EPE3zYTMwe6T7L0VLjA0BKcf4sIoN_WUd6jUWYEXQFkjqk87jyatnIL_eQpVI4hCY-5DRJ6cFjeeHHd2ZPY)

This graph shows that when the minimum MTTF is doubled, the data points from the SUT slide to the right making the entire system acceptable.

## **Explain your evaluation and justification of how you decide the MTTFmin**

We identified the Mean Time To Failure (MTTF) based on where the data points would be on the border of being accepted. This meant that the data point closest to the accepted border would be where the minimum MTTF would be assigned. This is because it is the minimum in which the system under test becomes acceptable. Given that the normalized failure data is equal to the failure time divided by MTTF. We were then able to produce the Twice MTTFmin and Half MTTFmin graphs. Thus by changing the maximum acceptable number of failures we plotted the  Twice MTTFmin and Half MTTFmin graphs.

## **A discussion on the advantages and disadvantages of RDC**

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

**Jonathan:** Created the 3 RDC graphs MTTFmin, 2*MTTFmin and 0.5*MTTF min. Also calculated the MTTF and conducted analysis on the RDC graph results.

# Difficulties Encountered, Challenges Overcome, and Lessons Learned

**Jonathan:** I found this lab to be difficult due to the outdated tools being used and vague instructions. Firstly, the SFRAT program was incompatible with Windows 11, Windows 10 and Mac OS. The C-SFRAT program was usable but incompatible with the data provided. Additionally, the Reliability-Demonstration-Chart excel sheet had limited capabilities as it was created on Excel 2003 and only allows you to plot 16 data points at a time.

**Aarushi:** It was a challenge to run most of the softwares due OS incompatibilities and I had to create a Virtual Machine with Windows XP. CASRE did not run at all on any OS so I had to use Excel to do the Laplace Trend Tests. Additionally so many data files were provided in various formats and all had to be changed before being imported into the softwares. The tools provided had barely any documentation so it was difficult to understand what data inputs are needed and what the results mean.

**Luke:** With the outdated software being used in the lab, it was difficult to conduct several procedures within the lab. I encountered many problems when using the SFRAT program on MacOS and Windows 10 which hindered my ability to perform analysis. When I turned to the excel sheet instead, it was also in a very old format which was limited in functionality when opened up in Excel 2022.

# Comments/Feedback on the Lab Itself

**Jonathan:** There could have been better communication as to which OS systems are supported by a program. Compatible datasets without the need to manipulate them would save time and energy.

**Luke:** Overall, this lab was a bit more disorganized and unclear than the previous ones. The software in the instructions was very hard to run and had many OS/environmental restrictions that prevented some of us from conducting parts of the lab.

**Aarushi:** The lab manual should have more detailed instructions and formatted data sets compatible with each tool should be provided.