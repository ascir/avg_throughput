# avg_throughput
Code for everlytics test to calculate average throughput of the given dataset.
1. Formula for Throughput used by you in the code:
### Steps to calculate the throughput:
First and foremost, create a coloumn called throughput and perform the following calculations:
#### Step 1
* Convert the window size from bytes to bits by multiplying the number of bytes by 8 (1 byte = 8 bits)
#### Step 2
* Divide the window size by the latency (Send/Time)
#### Step 3
* Convert the result from step 2 to megabits per second by dividing the result by 1,000,000
**Throughput = Bytes*8/Send/Time)/1000000**
---

2. Average throughput is achieved by using python groupby function
* Groupby ASN
~~~
data2= (data1.groupby('ASN').Throughput.mean())
data2.coloumns= ["ASN", "Throughput"]
data2
~~~
Result: 
~~~
ASN
1901     12.043268
3301           inf
3320     12.184800
3329           inf
6830           inf
8447           inf
9050      4.808444
9121           inf
9198           inf
12635          inf
15685     8.998243
21246          inf
31334     0.010675
50231          inf
Name: Throughput, dtype: float64
~~~

* Groupby Co Server
~~~
data2= (data1.groupby('ASN').Throughput.mean())
data2.coloumns= ["ASN", "Throughput"]
data2
~~~
Result:
~~~
Co Server
200         inf
206         inf
302    0.010675
Name: Throughput, dtype: float64
~~~

3. Some additional keys by which the data can be grouped:
* Country
* TimeStamp

