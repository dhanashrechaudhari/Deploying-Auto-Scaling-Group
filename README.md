# Auto Scaling with Application Load Balancer (ALB)
## Introduction.
Efficient traffic management and scalability are essential for modern cloud applications. By combining an **Application Load Balancer(ALB)** with multiple **Auto Scaling Groups (ASGs)**, workloads can be distributed intelligently across different user categories **Home, Laptop, and Mobile.** Each group uses a unique scaling strategy (Static, Dynamic, and Scheduled) to ensure consistent performance, high availability, and optimized resource utilization.

## Architecture Components.
1. Application Load Balancer (ALB)
    - Distributes incoming traffic across multiple targets (EC2 instances) in different Auto Scaling Groups.
    - Ensures high availability and fault tolerance.
    - Routes requests based on listener rules to the appropriate Target Group (Home, Laptop, or Mobile).
2. Target Groups
    - Logical groups of instances that receive traffic from the ALB.
    - Each target group is associated with an Auto Scaling Group.

| Target Group | Description                       | Scaling Strategy       |
| ------------ | --------------------------------- | ---------------------- |
| **Home**     | Handles traffic from home devices | Static Auto Scaling    |
| **Laptop**   | Manages traffic from laptops      | Dynamic Auto Scaling   |
| **Mobile**   | Serves mobile users               | Scheduled Auto Scaling |

![ASG](ASG.drawio%20(2).png)

## Step-by-Step Deployment Guide.
### Step 1: Create Launch Template.
#### Launch Template (Home-TG).

![ASG](images/1.png)


![ASG](images/5.png)

#### Launch Template (Laptop-TG).
![ASG](images/6.png)

![ASG](images/7.png)

#### Launch Template(Mobile-TG).

![ASG](images/8.png)

![ASG](images/9.png)

![ASG](images/10.png)

### Step 2: Create Auto Scaling Groups (ASGs).
#### **Home ASG**: Use Static Scaling for a fixed number of instances. 
![ASG](images/11.png)

![ASG](images/12.png)

![ASG](images/13.png)

![ASG](images/14.png)

#### **Laptop ASG**: Implement Dynamic Scaling based on performance metrics.

![ASG](images/15.png)

![ASG](images/16.png)

![ASG](images/17.1.png)

![ASG](images/17.2.png)

#### **Mobile ASG**: Apply Scheduled Scaling for predictable workloads.
![ASG](images/18.png)

![ASG](images/19.png)

![ASG](images/20.png)

![ASG](images/21.png)

### Step 3: Create scheduled action.

![ASG](images/22.png)

![ASG](images/23.png)

![ASG](images/24.png)

![ASG](images/25.png)

### Step 4: Create Target Groups.
#### Home-Target-Group
![ASG](images/26.png)

#### Laptop-Target-Group
![ASG](images/27.png)

![ASG](images/28.png)

#### Mobile-Target-Group

![ASG](images/29.png)

![ASG](images/30.png)

![ASG](images/31.png)

### Step 5: Set Up Application Load Balancer (ALB).
![ASG](images/35.png)

![ASG](images/36.png)

![ASG](images/37.png)

![ASG](images/38.png)

### Step 6: Attach ALB to ASGs.
Connect each Auto Scaling Group with its corresponding target group.
![ASG](images/32.png)

![ASG](images/33.png)

![ASG](images/34.png)

### Step 7: Test and Verify.

![ASG](images/39.png)

![ASG](images/40.png)

![ASG](images/41.png)

![ASG](images/42.png)

![ASG](images/43.png)

![ASG](images/44.png)

## Conclusion
This setup provides a flexible and robust cloud architecture combining the power of **AWS Auto Scaling** and **Application Load Balancer**. By using different scaling strategies for various workloads, organizations can achieve both performance optimization and cost efficiency across all user categories.

