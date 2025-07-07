# AWS S3 - Simple Storage Service

## Overview

- S3 stands for **Simple Storage Service**.
- It is an **object storage** service, where each object consists of **data, metadata, and a key**.
- Provides secure, durable, and highly scalable object storage for developers and IT teams.
- Easy to use with a simple web service interface to **store and retrieve any amount of data** from anywhere on the web.
- Supports **unlimited storage**, allowing you to store as much data as you need.
- **Data is accessible from anywhere, at any time**.
- You can **host static websites** using S3 buckets quickly and easily.
- **Data durability is ensured** through automatic replication across **multiple Availability Zones**.
- Supports **cost-effective storage** via S3 Glacier and S3 Glacier Deep Archive.
- **S3 Object Lock** can be enabled to prevent accidental deletion.
- **AWS Storage Gateway** allows seamless migration of on-premise data to S3 for backup.
- In **CDN architectures**, S3 can store production and development data for microservices.

---

## AWS S3 Storage Classes

### 1. S3 Standard

- Default storage class if none is specified during upload.
- Designed for **99.99% availability** and **11 9's (99.999999999%) durability**.
- Offers **low latency and high throughput**.
- Ideal for frequently accessed data that needs **immediate availability**.

### 2. S3 Standard-IA (Infrequent Access)

- For data that is **accessed less frequently** but still needs **immediate access** when required.
- **Cheaper than Standard**.
- Best for **large objects > 128 KB** kept for **at least 30 days**.
- Same availability and durability as S3 Standard.

### 3. S3 Intelligent-Tiering

- Automatically **moves data between S3 Standard and Standard-IA** based on usage.
- Transfers objects to IA if not accessed for **30 consecutive days**.
- **No charges for moving or retrieving objects** between tiers.

### 4. S3 One Zone-IA

- **20% cheaper** than Standard-IA.
- Stores data in **one availability zone only** (not three like other classes).
- Suitable for **non-critical**, easily reproducible data.
- Not as resilient as S3 Standard or IA.

### 5. S3 Glacier

- For **durable, secure, low-cost data archiving**.
- Used for **rarely accessed** data, where **immediate access is not required**.
- Retrieval models:
  - **Expedited**: Minutes (High cost)
  - **Standard**: 3-5 hours
  - **Bulk**: 5-12 hours
- Best for **public sector, financial services, and healthcare** needing long-term archival (7-10 years).

### 6. S3 Glacier Deep Archive

- Cheapest storage for **archiving data you rarely access**.
- Retrieval time is longer but ideal for **compliance archives**.

---

## S3 Bucket Versioning

- **Versioning** stores multiple variants of an object in the same bucket.
- Use it to **preserve, retrieve, and restore** all versions of an object.
- Helps recover from unintended deletions or application failures.
- Example:
  - `photos.jpg` with version ID `v1`
  - `photos.jpg` with version ID `v2` (updated version)

---

