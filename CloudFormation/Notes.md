
# AWS CloudFormation Detailed Notes

## 🧠 1. What is AWS CloudFormation?

**CloudFormation** is an AWS service that lets you **model, provision, and manage infrastructure as code (IaC)** in a safe, predictable, and repeatable way using **YAML or JSON templates**.

---

## 🏗️ 2. Key Concepts

| Term           | Description                                              |
|----------------|----------------------------------------------------------|
| **Template**   | The YAML/JSON file defining AWS resources and configurations |
| **Stack**      | A single deployment of resources defined in a template   |
| **Change Set** | A preview of changes that CloudFormation will make to a stack |
| **Resource**   | An AWS service like EC2, S3, IAM defined in the template |
| **Parameter**  | User inputs to customize stacks during deployment        |
| **Output**     | Useful info like resource names, URLs exported from the stack |
| **Mapping**    | Fixed value pairs, like region → AMI ID                  |
| **Condition**  | Controls which resources are created based on parameters |

---

## 📄 3. CloudFormation Template Structure (YAML)

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Description: Description of the stack

Parameters:
  # Input values provided by user

Mappings:
  # Static mapping of values (region to AMI ID, etc.)

Conditions:
  # Logical conditions for resource creation

Resources:
  # Mandatory section: All AWS services you want to create

Outputs:
  # Useful info to return (e.g. URL, resource ID)
```

---

## ⚙️ 4. Resources Section Example

```yaml
Resources:
  MyBucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: my-demo-bucket-123
```

---

## 🧩 5. Parameters Example

```yaml
Parameters:
  BucketNameParam:
    Type: String
    Description: Name of the S3 bucket
```

Use in `Resources`:

```yaml
Resources:
  MyBucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: !Ref BucketNameParam
```

---

## 🔃 6. Mappings Example

```yaml
Mappings:
  RegionMap:
    us-east-1:
      AMI: ami-0ff8a91507f77f867
    us-west-1:
      AMI: ami-0bdb828fd58c52235
```

Use:

```yaml
ImageId: !FindInMap [RegionMap, !Ref "AWS::Region", AMI]
```

---

## 🔁 7. Conditions Example

```yaml
Parameters:
  CreateProdResources:
    Type: String
    AllowedValues: [true, false]
    Default: false

Conditions:
  IsProd: !Equals [!Ref CreateProdResources, true]

Resources:
  ProdOnlyBucket:
    Type: AWS::S3::Bucket
    Condition: IsProd
```

---

## 📤 8. Outputs Example

```yaml
Outputs:
  BucketName:
    Description: "Name of the S3 bucket"
    Value: !Ref MyBucket
    Export:
      Name: MyBucketName
```

---

## 🔄 9. Change Sets

- Used for **safe updates**
- Shows what will change before applying
- CLI: `aws cloudformation create-change-set`

---

## 🔐 10. Stack Policies

Protect critical resources:

```json
{
  "Statement": [
    {
      "Effect": "Deny",
      "Action": "Update:*",
      "Principal": "*",
      "Resource": "*"
    }
  ]
}
```

---

## 💡 11. Nested Stacks

- Break large templates into reusable modules
- Use `AWS::CloudFormation::Stack`

---

## 🧪 12. Best Practices

- Use YAML (easier to read than JSON)
- Validate templates:  
  `aws cloudformation validate-template --template-body file://template.yaml`
- Store large templates in S3
- Add `Metadata` for documentation
- Use naming conventions and tags

---

## 💻 13. Deployment Methods

- **Console**
- **AWS CLI**

```bash
aws cloudformation create-stack \
  --stack-name my-stack \
  --template-body file://s3-bucket.yaml \
  --capabilities CAPABILITY_NAMED_IAM
```

- **AWS SDKs (e.g., Boto3)**
- **CI/CD pipelines**

---

## 🔥 14. CloudFormation vs Terraform

| Feature            | CloudFormation | Terraform |
|--------------------|----------------|-----------|
| Language           | YAML/JSON      | HCL       |
| Provider support   | Only AWS       | Multi-cloud |
| State management   | Managed by AWS | Local or remote |
| Drift detection    | Yes            | Yes       |
| Community modules  | Fewer          | More      |

---
