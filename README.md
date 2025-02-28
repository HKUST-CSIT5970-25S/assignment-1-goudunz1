# CSIT5970 Assignment-1: EC2 Measurement (2 questions, 4 marks)

### Deadline: 11:59PM, Feb, 28, Friday

---

### Name: ZENG Yuxiang
### Student Id: 21076301
### Email: yzengbl@connect.ust.hk

---

## Question 1: Measure the EC2 CPU and Memory performance

1. (1 mark) Report the name of measurement tool used in your measurements (you are free to choose *any* open source measurement software as long as it can measure CPU and memory performance). Please describe your configuration of the measurement tool, and explain why you set such a value for each parameter. Explain what the values obtained from measurement results represent (e.g., the value of your measurement result can be the execution time for a scientific computing task, a score given by the measurement tools or something else).

    > sysbench

2. (1 mark) Run your measurement tool on general purpose `t2.micro`, `t2.medium`, and `c5d.large` Linux instances, respectively, and find the performance differences among these instances. Launch all the instances in the **US East (N. Virginia)** region. Does the performance of EC2 instances increase commensurate with the increase of the number of vCPUs and memory resource?

    In order to answer this question, you need to complete the following table by filling out blanks with the measurement results corresponding to each instance type.

    | Size        | CPU performance | Memory performance |
    | ----------- | --------------- | ------------------ |
    | `t2.micro` | events per second:  2321.30 | 540.92 MiB/sec |
    | `t2.medium`  | events per second:  4454.55 | 906.77 MiB/sec |
    | `c5d.large` | events per second:  1911.29 | 8126.36 MiB/sec |

    > Region: US East (N. Virginia). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI.

## Question 2: Measure the EC2 Network performance

1. (1 mark) The metrics of network performance include **TCP bandwidth** and **round-trip time (RTT)**. Within the same region, what network performance is experienced between instances of the same type and different types? In order to answer this question, you need to complete the following table.

    | Type                      | TCP b/w (Mbps) | RTT (ms) |
    | ------------------------- | -------------- | -------- |
    | `t3.medium` - `t3.medium` | 4.62 Gbits/sec | 0.235 ms |
    | `m5.large` - `m5.large`   | 4.96 Gbits/sec | 0.239 ms |
    | `c5n.large` - `c5n.large` | 4.96 Gbits/sec | 0.171 ms |
    | `t3.medium` - `c5n.large` | 4.80 Gbits/sec | 0.638 ms |
    | `m5.large` - `c5n.large`  | 4.96 Gbits/sec | 0.161 ms |
    | `m5.large` - `t3.medium`  | 4.72 Gbits/sec | 0.736 ms |

    > Region: US East (N. Virginia). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI. Note: Use private IP address when using iPerf within the same region. You'll need iPerf for measuring TCP bandwidth and Ping for measuring Round-Trip time.

2. (1 mark) What about the network performance for instances deployed in different regions? In order to answer this question, you need to complete the following table.

    | Connection                | TCP b/w (Mbps) | RTT (ms) |
    | ------------------------- | -------------- | -------- |
    | N. Virginia - Oregon      | 481 Mbits/sec | 62.4 ms |
    | N. Virginia - N. Virginia | 4.71 Gbits/sec | 0.295 ms |
    | Oregon - Oregon           | 4.78 Gbits/sec | 0.209 ms |

    > Region: US East (N. Virginia), US West (Oregon). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI. All instances are `c5.large`. Note: Use public IP address when using iPerf within the same region.
