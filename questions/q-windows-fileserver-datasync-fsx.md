# Q-WINDOWS-FILESERVER-DATASYNC-FSX

## Original question

A company is using an on-premises Windows file server to store 1 TB of data. About 5 GB worth of new data is being produced every day. The company has an AWS Direct Connect connection from the on-premises network to the AWS VPC. As part of the ongoing migration process, about half of its Windows-based workload has been migrated to the AWS cloud. The data stored on the on-premises server needs to be available on a **file system for the servers in AWS**.

Which of the following options is the **recommended migration strategy** for this scenario?

**Option A:** Create an Amazon FSx for Windows File Server share on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon FSx.

**Option B:** Create a new Amazon Elastic File System (EFS) share on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon EFS. Mount the EFS share on the Windows servers.

**Option C:** Create an Amazon S3 bucket on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon S3. Use AWS Transfer Family to access the files.

**Option D:** Use AWS Storage Gateway - File Gateway to create an SMB share on the on-premises data center to replace the existing Windows file server. Point the existing file shares to the new file gateway share.

## Correct answer

- **Option A** is the recommended approach for this scenario.
- **Amazon FSx for Windows File Server** gives you a **fully managed**, **SMB-native** file system **inside the VPC** that **Windows instances** can use like a traditional corporate share.
- **AWS DataSync** runs **scheduled** jobs with **incremental** updates, **bandwidth** controls, and **verification**, which fits **ongoing replication** from the **on-premises Windows file server** over the **Direct Connect** path that is already in place.

## Why it is correct

- The stem asks for a **file system for the servers in AWS**, not merely a place to store **objects** in a **bucket**.
- **FSx for Windows File Server** is built for **SMB**, **Active Directory** integration, and **Windows-style** permissions and behavior.
- **DataSync** is the usual exam answer when you need **scheduled** or **repeated** copy jobs from **on-premises NFS or SMB** into **S3**, **EFS**, or **FSx**, with **throttling** and **integrity checks**.
- About **5 GB per day** of new data is a good fit for **incremental** sync after you seed the initial **1 TB** over **Direct Connect**.

## Why the other options are wrong

- **Option B:** **Amazon EFS** is **NFS-oriented** and fits **Linux-elastic** file workloads best. It is a **weak** primary answer for classic **Windows file server** language compared with **FSx for Windows**. The combination **EFS plus DataSync plus mount on Windows** is a common **workload and storage mismatch** distractor.
- **Option C:** **Amazon S3** is **object storage**. It does not give **Windows applications** the same **SMB file share** experience the stem describes. **AWS Transfer Family** adds **FTP, SFTP, or FTPS** access into **S3**, which still does not replace a **managed Windows file share in the VPC** for general-purpose file serving.
- **Option D:** **AWS Storage Gateway File Gateway** presents **SMB** **on premises** with **S3** as the backing store. That design keeps the **emphasis at the edge** and does **not** meet the goal of hosting the data on an **AWS-resident Windows file system** for **instances in the VPC** as cleanly as **FSx**. It also describes **replacing** the on-premises server with a **local gateway** share instead of **landing** the dataset in **FSx** for **migrated** workloads.

## Services involved

- [Amazon VPC](../services/amazon-vpc.md)
- [Amazon FSx for Windows File Server](../services/amazon-fsx-for-windows-file-server.md)
- [AWS DataSync](../services/aws-datasync.md)
- [AWS Direct Connect](../services/aws-direct-connect.md)
- [Amazon Elastic File System (EFS)](../services/amazon-efs.md)
- [Amazon S3](../services/amazon-s3.md)
- [AWS Transfer Family](../services/aws-transfer-family.md)
- [AWS Storage Gateway](../services/aws-storage-gateway.md)

## Pattern tags

- [Hybrid cloud storage migration](../patterns/hybrid-cloud-storage-migration.md)
- [DataSync migration and replication](../patterns/datasync-migration-replication.md)
- [Windows managed file storage (SMB)](../patterns/windows-managed-file-storage-smb.md)
- [File storage vs object storage](../patterns/file-storage-vs-object-storage.md)
- [Storage Gateway hybrid access](../patterns/storage-gateway-hybrid-access.md)

## Trap type

- **Workload and storage mismatch:** **EFS** versus **FSx for Windows**; **object** versus **file** (**S3** plus **Transfer Family** versus **FSx**); **hybrid gateway on premises** versus a **cloud file system** for **AWS** compute.

## Confidence / review status

- Matches the **highlighted** practice answer; re-check if the **exam** or **question bank** wording changes.

## Source asset

- `/Users/james/.cursor/projects/Users-james-work-aws-cert/assets/Screenshot_2026-03-24_at_8.43.40_PM-5d86702b-204b-477c-8535-c53776663600.png`

## Related pages

- [Services template](../.cursor/rules/services-template.mdc)
- [Patterns template](../.cursor/rules/patterns-template.mdc)
- [Questions template](../.cursor/rules/questions-template.mdc)

