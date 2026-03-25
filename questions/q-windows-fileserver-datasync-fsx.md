# Q-WINDOWS-FILESERVER-DATASYNC-FSX

## Original question

A company is using an on-premises Windows file server to store 1 TB of data. About 5 GB worth of new data is being produced every day. The company has an AWS Direct Connect connection from the on-premises network to the AWS VPC. As part of the ongoing migration process, about half of its Windows-based workload has been migrated to the AWS cloud. The data stored on the on-premises server needs to be available on a **file system for the servers in AWS**.

Which of the following options is the **recommended migration strategy** for this scenario?

**Option A:** Create an Amazon FSx for Windows File Server share on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon FSx.

**Option B:** Create a new Amazon Elastic File System (EFS) share on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon EFS. Mount the EFS share on the Windows servers.

**Option C:** Create an Amazon S3 bucket on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon S3. Use AWS Transfer Family to access the files.

**Option D:** Use AWS Storage Gateway - File Gateway to create an SMB share on the on-premises data center to replace the existing Windows file server. Point the existing file shares to the new file gateway share.

## Correct answer
- **A**

## Why it is correct
- Stem needs **SMB file system in VPC** for **Windows instances in AWS**.
- **FSx for Windows** = managed SMB/NTFS semantics.
- **DataSync** + **daily task** = incremental over **DX** after **1 TB** bulk.
- **5 GB/day** = incremental sync pattern.

## Why the other options are wrong
- **B:** **EFS** = **NFS/Linux** fit; wrong primary for Windows file-server stem.
- **C:** **S3** = object; **Transfer** = SFTP/FTP-style, not general SMB share for apps.
- **D:** **File Gateway** = on-prem SMB front to S3; stem wants **AWS-resident** Windows FS for **servers in VPC** → **FSx**.

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
- **EFS vs FSx**; **object+Transfer vs file**; **Gateway on-prem vs FSx in VPC**.

## Confidence / review status
- Matches highlighted practice key.

## Source asset
- `/Users/james/.cursor/projects/Users-james-work-aws-cert/assets/Screenshot_2026-03-24_at_8.43.40_PM-5d86702b-204b-477c-8535-c53776663600.png`

## Related pages
- [Services template](../.cursor/rules/services-template.mdc)
- [Patterns template](../.cursor/rules/patterns-template.mdc)
- [Questions template](../.cursor/rules/questions-template.mdc)
