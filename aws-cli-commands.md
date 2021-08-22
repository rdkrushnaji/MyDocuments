# aws s3 cli commands

     PS C:\Users\vicky> aws configure

AWS Access Key ID [****************XLDO]: xxxxxxxxxxxxxxxxxxxxxx

AWS Secret Access Key [****************aDn/]: xxxxxxxxxxxxxxxxxxxxxxxxxj


     aws s3 mb s3://krushnaji-s3

PS C:\Users\vicky> aws s3 mb s3://krushnaji-s3

make_bucket: krushnaji-s3

      aws s3 ls

2021-08-22 14:03:17 krushnaji-s3

PS C:\Users\vicky>

      aws s3 rb s3://krushnaji-s3

** remove_bucket failed: s3://krushnaji-s3 An error occurred (BucketNotEmpty) when calling the DeleteBucket operation: The bucket you tried to delete is not empty **
PS C:\Users\vicky> aws s3 rb s3://krushnaji-s3 --force

delete: s3://krushnaji-s3/terraformstate/vpc-statefile

remove_bucket: krushnaji-s3


     aws s3 rm s3://bucket-name/example/filename.txt --recursive
     

     aws s3 mv s3://bucket-name/example s3://my-bucket/


     aws s3 cp s3://bucket-name/example s3://my-bucket/
 



