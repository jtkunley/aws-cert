# Q-WINDOWS-FILESERVER-DATASYNC-FSX

## Original question

A company is using an on-premises Windows file server to store 1 TB of data. About 5 GB worth of new data is being produced every day. The company has an AWS Direct Connect connection from the on-premises network to the AWS VPC. As part of the ongoing migration process, about half of its Windows-based workload has been migrated to the AWS cloud. The data stored on the on-premises server needs to be available on a **file system for the servers in AWS**.

Which of the following options is the **recommended migration strategy** for this scenario?

**Option A:** Create an Amazon FSx for Windows File Server share on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon FSx.

**Option B:** Create a new Amazon Elastic File System (EFS) share on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon EFS. Mount the EFS share on the Windows servers.

**Option C:** Create an Amazon S3 bucket on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon S3. Use AWS Transfer Family to access the files.

**Option D:** Use AWS Storage Gateway - File Gateway to create an SMB share on the on-premises data center to replace the existing Windows file server. Point the existing file shares to the new file gateway share.

## Correct answer

**Option A** — FSx for Windows File Server provides a **fully managed SMB/Windows-native file system in AWS** for instances in the VPC; **DataSync** handles **scheduled, incremental** replication over the existing **Direct Connect** path.

## Why it is correct

- The requirement is a **file system** (not only object storage) that **Windows workloads in AWS** can use like a traditional share.
- **FSx for Windows File Server** is purpose-built for **SMB, AD integration, and Windows semantics** (permissions, NTFS-style behavior).
- **DataSync** is the standard exam answer for **ongoing or scheduled copy** from on-premises NFS/SMB to AWS file or object stores, with bandwidth control and verification.
- **~5 GB/day** fits incremental replication; initial **1 TB** can be seeded over Direct Connect with scheduled syncs afterward.

## Why the other options are wrong

- **Option B:** **EFS** is **NFS-oriented** and optimized for **Linux** elastic workloads; it is a **poor primary fit** for “Windows file server” semantics versus **FSx for Windows**. Exam distractor: “EFS + DataSync + mount on Windows” ignores the usual **workload/storage pairing**.
- **Option C:** **S3** is **object storage**, not a POSIX/SMB **file system** for typical Windows app expectations. **Transfer Family** is **FTP/SFTP/FTPS** style access to S3—not a substitute for a **managed Windows file share** in VPC for general file-server replacement.
- **Option D:** **File Gateway** exposes **on-premises SMB** backed primarily by **S3**; it **does not** deliver the stem’s goal of having the corpus on an **AWS-resident Windows file system** for **servers in AWS** as cleanly as **FSx**. It also frames **replacing** the on-prem server with a **local** gateway share rather than landing data in **FSx in the VPC** for migrated workloads.

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

**Workload/storage mismatch:** EFS vs FSx for Windows; **object vs file** (S3 + Transfer vs FSx); **hybrid gateway on-prem** vs **cloud file system** for AWS compute.

## Confidence / review status

Matches highlighted practice answer; align with current AWS exam wording if question source updates.

## Source asset

- `/Users/james/.cursor/projects/Users-james-work-aws-cert/assets/Screenshot_2026-03-24_at_8.43.40_PM-5d86702b-204b-477c-8535-c53776663600.png`

## Related pages

- [Services template](../.cursor/rules/services-template.mdc)
- [Patterns template](../.cursor/rules/patterns-template.mdc)
- [Questions template](../.cursor/rules/questions-template.mdc)

