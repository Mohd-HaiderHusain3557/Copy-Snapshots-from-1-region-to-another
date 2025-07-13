# Copy-Snapshots-from-1-region-to-another
This guide provides a step-by-step process to copy an Amazon EBS snapshot from one AWS region to another and attach it to an EC2 instance in the destination region. It is useful for scenarios such as disaster recovery, workload migration, and setting up pre-configured environments across regions. 

# 📦 Copying EBS Snapshot to Another AWS Region and Attaching It to a New EC2 Instance

This guide walks you through copying an Amazon EBS snapshot from one region to another and attaching it to an EC2 instance in the destination region. Useful for backup, disaster recovery, or migrating workloads.

---

## ✅ Steps Overview

---

### 1️⃣ Launch EC2 Instance in Source Region
Launch an EC2 instance (e.g., Windows/Linux) in your **source region** (e.g., `us-east-1` - N. Virginia).  
This will automatically create an EBS volume attached to the instance.

---

### 2️⃣ Create Snapshot of Attached Volume
Go to **EC2 → Elastic Block Store → Snapshots** and click **Create snapshot**.  
Select the EBS volume attached to the instance you just launched.

---

### 3️⃣ Create Volume from Snapshot (Optional)
If needed in the **same region**, select the snapshot and click **Actions → Create volume from snapshot**.  
Set size, IOPS, and Availability Zone.

> ✅ This step is optional if you're directly copying the snapshot to another region.

---

### 4️⃣ Launch EC2 Instance in Target Region
Switch to the **destination region** (e.g., `us-west-1` - N. California).  
Launch a new EC2 instance that will use the copied snapshot as a volume.

---

### 5️⃣ Go Back to Source Region & Open Snapshot Console
Return to the **source region** where the original snapshot exists.  
Go to **EC2 → Snapshots** to view it.

---

### 6️⃣ Confirm Snapshot Status as “Completed”
Ensure the snapshot’s status is **Completed** before initiating a copy.

---

### 7️⃣ Select Snapshot and Click "Copy Snapshot"
Select the snapshot, then click **Actions → Copy snapshot**.

---

### 8️⃣ Copy Snapshot to Another Region
In the copy snapshot dialog:
- Choose the **destination region** (e.g., `us-west-1`).
- Optionally, enter a **description**.
- Click **Copy snapshot** to begin cross-region transfer.

---

### 9️⃣ Verify Snapshot in Destination Region
Switch to the destination region.
Go to **EC2 → Snapshots** and confirm that the copied snapshot appears and its status is **Completed**.

---

### 🔟 Attach Volume Created from Copied Snapshot
Go to **EC2 → Volumes** in the destination region.  
Select the volume created from the copied snapshot and click **Actions → Attach volume**.

---

### 1️⃣1️⃣ Attach Volume to EC2 Instance
In the **Attach Volume** dialog:
- Select the new EC2 instance (in the same AZ).
- Choose a device name (e.g., `/dev/sdf`).
- Click **Attach volume**.

> 🎉 You're done! Your volume is now successfully copied and attached in a new region.

---

## 🔐 Benefits

- ✅ Cross-region disaster recovery
- 🔁 Reuse pre-configured volumes
- 🔒 Secure & encrypted snapshot transfers
- 🌍 Supports multi-region architecture

---

