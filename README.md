# Executive Summary

# Objective

To validate the abc.in performance under the load of 50000 transactions per hour and to identify the breaking point of the server.

### Load Test Result

Load test has been conducted with 50 users concurrently accessing the website to achieve the 50000 transactions per hour. This test is to validate whether the server can handle 50000 transactions per hour or not.

| Total Duration | 1 hour |
| --- | --- |

| **Label** | **# Samples** | **Average** | **Median** | **90% Line** | **95% Line** | **99% Line** | **Min** | **Max** | **Error %** | **Throughput** | **KB/sec** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 01\_HomePage | 9868 | 672 | 573 | 1177 | 1297 | 1904 | 290 | 6243 | 0.00% | 2.6 | 27.2 |
| 02\_Login | 9866 | 404 | 290 | 927 | 959 | 1326 | 284 | 14944 | 0.00% | 2.6 | 10.6 |
| 03\_Contacts | 9866 | 400 | 291 | 925 | 955 | 1300 | 283 | 5737 | 0.00% | 2.6 | 10.6 |
| 04\_Team | 9863 | 409 | 292 | 931 | 963 | 1298 | 284 | 12049 | 0.00% | 2.6 | 10.6 |
| 05\_UserProfile | 9863 | 403 | 291 | 926 | 964 | 1302 | 284 | 23931 | 0.00% | 2.6 | 10.6 |
| TOTAL | 49326 | 458 | 292 | 935 | 993 | 1543 | 283 | 23931 | 0.00% | 13 | 69.6 |

### Observations:

1. No errors encountered during load testing
2. Maximum response time is 23931 milliseconds
3. Minimum response time is 283 milliseconds
4. 99 percentile is less 1543 milliseconds

## Stress Test #1

In this test, more than 100 users have been injected concurrently at a regular interval of 30 seconds for the below transactions. When the concurrent users reached 125, the first error (Internal Server Error Code 500) occurred. Eventually all the transactions started failing. Below is the response time dashboard for the run 1. Similar observations for the run 2 as well.

**Run #1**

| **Label** | **# Samples** | **Average** | **Median** | **90% Line** | **95% Line** | **99% Line** | **Min** | **Max** | **Error %** | **Throughput** | **KB/sec** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 01\_HomePage | 4068 | 1992 | 1365 | 3067 | 4240 | 11402 | 66 | 235596 | 0.64% | 9.1 | 95.1 |
| 02\_Login | 4042 | 1417 | 948 | 2023 | 3428 | 12325 | 1 | 140924 | 0.59% | 9.1 | 37 |
| 03\_Contacts | 4017 | 1459 | 975 | 1971 | 3299 | 11753 | 2 | 105727 | 0.67% | 9.1 | 36.8 |
| 04\_Team | 3987 | 1289 | 963 | 1943 | 3289 | 10987 | 251 | 97139 | 0.53% | 9 | 36.6 |
| 05\_UserProfile | 3965 | 1333 | 976 | 2041 | 3297 | 10619 | 165 | 121944 | 0.68% | 9 | 36.4 |
| TOTAL | 20079 | 1500 | 1009 | 2343 | 3528 | 11507 | 1 | 235596 | 0.62% | 45.1 | 241.3 |

**Run #2**

| **Label** | **# Samples** | **Average** | **Median** | **90% Line** | **95% Line** | **99% Line** | **Min** | **Max** | **Error %** | **Throughput** | **KB/sec** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 01\_HomePage | 5820 | 2435 | 1576 | 3590 | 5386 | 17901 | 1 | 365617 | 0.65% | 9.2 | 96.3 |
| 02\_Login | 5780 | 1818 | 1007 | 2235 | 3777 | 16757 | 106 | 502888 | 0.64% | 9.2 | 37.4 |
| 03\_Contacts | 5741 | 2006 | 1001 | 2233 | 3819 | 21007 | 1 | 303103 | 0.63% | 9.1 | 37.2 |
| 04\_Team | 5705 | 1678 | 1006 | 2239 | 3833 | 17675 | 1 | 124876 | 0.49% | 9.1 | 37 |
| 05\_UserProfile | 5675 | 1814 | 1001 | 2209 | 3642 | 18025 | 1 | 379085 | 0.62% | 9.1 | 36.8 |
| TOTAL | 28721 | 1952 | 1033 | 2757 | 4324 | 18025 | 1 | 502888 | 0.61% | 45.6 | 244.2 |

### Observations:

1. No errors observed till 125 concurrent users performing the transactions.
2. First internal server error occurred after the 125 concurrent users trying to access the website.
3. System will eventually fail to respond after 125 concurrent users.

## Conclusion

Multiple rounds have been conducted to validate the server performance and to identify the breaking point. During the load test, the system is capable of handling 50000 transactions per hour.

No errors have been observed during the execution which resembles that the server will respond positively for the load of 50000 transactions per hour with the 99 percentile response time is 1.5 seconds.

During the stress test, the server responded positively till 125 concurrent users, and when the load increases, the first internal server 500 error code occurred and eventually all the transactions started failing. This behavior has been observed in the subsequent execution as well.

Load test reveals that the server can handle 50000 transactions per hour with minimal users accessed the website.

Stress test reveals that the server can handle 125 concurrent users accessing the website. Subsequent increase in the load will fail to fulfill the user&#39;s expectation.

**Next Steps**

It is advisable to monitor the performance of CPU, Memory, Network and Disk utilization. To handle more number of users, tuning or scaling the infrastructure is required.

![](RackMultipart20210119-4-1qablza_html_3e8d26981ffda8f7.gif)4
