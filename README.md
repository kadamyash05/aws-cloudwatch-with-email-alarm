# 📈 Monitor EC2 CPU Utilization with CloudWatch and Email Alerts

This setup configures AWS CloudWatch to monitor the CPU utilization of an EC2 instance and sends an email alert when the utilization crosses 50%.

---

## ✅ Prerequisites

Make sure the following are ready:
- An EC2 instance running 
- Python installed on the instance
- A file named `cpu_utilization.py` in your project (refer to your repo)

---

## ⚙️ Step 2: Set Up CloudWatch Alarm for CPU Utilization

1. Go to **CloudWatch > Alarms > Create Alarm**
2. **Select Metric**:
   - Browse → EC2 → Per-Instance Metrics → CPUUtilization
   - Select your EC2 instance
3. **Specify metric & conditions**:
   - Threshold type: Static
   - Whenever CPUUtilization is **greater than 50**
   - Period: 5 minutes
   - Evaluation period: 1
4. Click **Next**

   <img width="940" height="294" alt="image" src="https://github.com/user-attachments/assets/84a42bc5-c56f-4f03-9d2c-f90e5e66bfd8" />

   <img width="940" height="376" alt="image" src="https://github.com/user-attachments/assets/ff9a62cd-30dd-4b7e-b41e-104d32528724" />

---

## 📩 Step 3: Configure Notification

1. **Create SNS topic** or use an existing one
   - Topic name: `cpu-alert-topic`
   - Protocol: Email
   - Endpoint: your email address (e.g., `youremail@example.com`)
2. Check your email inbox and confirm the SNS subscription

   <img width="940" height="364" alt="image" src="https://github.com/user-attachments/assets/e94132df-5695-4ca2-8e45-1cdff1e4dfa8" />


---

## 📜 Step 4: Trigger Alarm via Python (cpu_utilization.py)

Use the provided `cpu_utilization.py` from your repo. This script simulates or tracks CPU usage and can be scheduled via cron or run manually.

Example crontab entry (optional):
```bash
crontab -e
*/5 * * * * python3 /home/ec2-user/cpu_utilization.py
```

---

## ✅ Result

Once CPU utilization crosses 50%, CloudWatch triggers the alarm, SNS sends a notification email to your inbox, and you're alerted instantly.

<img width="940" height="417" alt="image" src="https://github.com/user-attachments/assets/e5eed15a-1c96-4953-92dc-ff87b429056d" />

