# Amazon Machine Images (AMIs)



```
~ on ☁️  (us-east-1) ➜  aws ec2 create-image --instance-id i-044585485181b0205 --name "devops-ec2-ami" --no-reboot
{
    "ImageId": "ami-01c6e45f4122e061f"
} 

~ on ☁️  (us-east-1) ➜  aws ec2 deregister-image --image-id ami-01c6e45f4122e061f

~ on ☁️  (us-east-1) ➜  aws ec2 create-image --instance-id i-044585485181b0205 --name "devops-ec2-ami" --no-reboot
{
    "ImageId": "ami-042747609b3340df1"
}

~ on ☁️  (us-east-1) ➜  aws ec2 describe-images --filters "Name=name,Values=devops-ec2-ami" --query 'Images[*].[ImageId, State]'
[
    [
        "ami-042747609b3340df1",
        "pending"
    ]
]

~ on ☁️  (us-east-1) ➜  
```
