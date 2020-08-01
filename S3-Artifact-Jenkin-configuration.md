
#  S3 as a artifactory for Jenkins


### Prerequisites
1. Need to have Jenkins Server

### Setup steps 
2. Create a S3 bucket to store artifacts  
    `S3 --> Create bucket `
      ```sh 
   Bucket name: s3-artifact 
   Region: Mumbai
   ```
3. Create new IAM role with "S3 full access" and assign it to jenkins server  
   `IAM --> Create role --> EC2` 
   ```ssh 
   Permission: AmazonS3FullAccess 
   Tags: key - Name, Value - S3FullAccess Role 
   name: S3_Full_Access
   
   Then go to EC2 portal select the jenkins EC2 and Action --> instance settings --> attach/replace IAM role then attach the S3FullAccess Role
   ```
   
4. Install "S3 Publisher" plugin on Jenkins  
  `Manage Jenkins --> Manage Plugins --> Availabe --> S3 publisher`

5. Configure S3 profile on Jenkins  
  `Manage Jenkins --> Configure Systems --> Amazon S3 profiles` 
   ```sh
   Profile name : s3-artifact-repository 
   Use IAM Role : chose
   ```

6. Create a job to store artifacts under S3.
