# Application Load Balancer Setup for EC2

#### Tasks <a href="#heading-tasks" id="heading-tasks"></a>

* Set up an Application Load Balancer named `xfusion-alb`.
* Create a target group named `xfusion-tg`.
* Create a security group named `xfusion-sg` to open port `80` for the public.
* Attach this security group to the ALB.
* Configure the ALB to route traffic on port `80` to port `80` of the `xfusion-ec2` instance.
* Make necessary changes to the default security group attached to the EC2 instance if needed.

#### Steps <a href="#heading-steps" id="heading-steps"></a>

1. Checkout the ec2 → instance (xfusion-ec2)
2.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733025099799/af828985-7dbd-4b45-8e57-37acef08d83b.png?auto=compress,format\&format=webp)

    Select load balancer.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733025455086/678c758c-4fbb-4a8b-bbde-108f9a0aa7b8.png?auto=compress,format\&format=webp)
3.  Create **Application Load Balancer**

    EC2 → Load balancers → Compare and select load balancer type

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733025540496/7414eb5b-8ac9-47c6-9042-d452d8298390.png?auto=compress,format\&format=webp)
4.  Pick subnet from our ec2

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733025676282/c3b4738d-ccb3-4015-a5c4-f091d9487f02.png?auto=compress,format\&format=webp)
5.  Name the **load balancer**.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733025736747/5f2d3e92-cef0-4abc-9c35-7a7a76f2556f.png?auto=compress,format\&format=webp)
6.  Select availability zone, atleast two; one from our ec2 subnet and another any of remaining subnet.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733025788204/4232c252-fec1-4a2f-b8c7-61c8675bfc22.png?auto=compress,format\&format=webp)
7.  Create target group.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733025910966/aefef575-230b-491f-a859-a2fbf681e185.png?auto=compress,format\&format=webp)

    EC2 → Target groups → Create target group

    *   **Choose a target type → Instances**

        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733025996655/6435d288-035e-4502-89f6-9f4b0306fce7.png?auto=compress,format\&format=webp)
8.  Name the group, xfusion-tg.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733026093775/50657d47-fe75-4a3c-9449-f805582e8b3f.png?auto=compress,format\&format=webp)
9. Select **Next**
10.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733026131480/86f9dbd2-505a-49c4-bb40-6490b7c5949f.png?auto=compress,format\&format=webp)

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733026164854/53a110bc-ce57-430f-bb59-1712f1c5739f.png?auto=compress,format\&format=webp)

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733026210486/b04df738-1af3-4453-ab92-eb654011812b.png?auto=compress,format\&format=webp)

    Successfully created the target group: **xfusion-tg**.
11.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733026239055/5a8d4146-039f-431d-a6f0-546af085413f.png?auto=compress,format\&format=webp)

    Now, select a target group.
12.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733026302316/e2543bcb-71b3-42df-973d-6fc57f2d713f.png?auto=compress,format\&format=webp)

    **Successfully created load balancer: xfusion-alb**
13.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733026395126/0374af96-7367-4008-8f9e-ab67c5cbec66.png?auto=compress,format\&format=webp)

    **Security group (**[**sg-097258aa3bafd5395 | xfusion-sg) was created successfully**](https://us-east-1.console.aws.amazon.com/ec2/home?region=us-east-1#SecurityGroup:groupId=sg-097258aa3bafd5395)

    EC2 → Security Groups → sg-097258aa3bafd5395 - xfusion-sg
14.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733026936389/c7c89673-f984-4086-9437-8475e8299bc1.png?auto=compress,format\&format=webp)
15. Let’s config security group on instance[s to for alb.](https://us-east-1.console.aws.amazon.com/ec2/home?region=us-east-1#SecurityGroup:groupId=sg-097258aa3bafd5395)

    [EC2 → Security Gro](https://us-east-1.console.aws.amazon.com/ec2/home?region=us-east-1#SecurityGroup:groupId=sg-097258aa3bafd5395)ups → sg-05a1bf9fe7738fdb5 - default → Edit inbound rules

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733027010056/3f7c9206-1317-4813-bb84-82d77e111636.png?auto=compress,format\&format=webp)
16. **Inbound security group rules successfully modified on security group** [**(sg-05a1bf9fe7738fdb5 | default)**](https://us-east-1.console.aws.amazon.com/ec2/home?region=us-east-1#SecurityGroup:group-id=sg-05a1bf9fe7738fdb5)
17.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733027037481/f3dc49d3-3e2e-4d30-870f-01c41142ce23.png?auto=compress,format\&format=webp)

    Register targets
18.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733027153834/fe87566d-af33-40b8-bfd5-279ec56a56bc.png?auto=compress,format\&format=webp)

    EC2 → Target groups → xfusion-tg → Register targets
19.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733027189661/419fae20-4690-4698-ab8a-a348fceb9c35.png?auto=compress,format\&format=webp)

    Register pending targets
20.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733027267513/ccb3671a-04ec-4696-bef9-39fdcdc7f86d.png?auto=compress,format\&format=webp)

    One target registered successfully to **xfusion-tg**. And health status is **healthy**

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733027361274/2e703bf4-f1d2-4caf-a0cb-ebcb037b0189.png?auto=compress,format\&format=webp)
21. We have load balancer now.
22.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733027453770/de85acfa-d46d-4d95-9d22-410b3d24585a.png?auto=compress,format\&format=webp)

    Now checkout the dns name.

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733027534918/5bac7b36-733f-4fab-8899-1ef3f5e2b13b.png?auto=compress,format\&format=webp)

    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1733027872450/7332af85-62f6-4ddc-89c9-db7e57be730b.png?auto=compress,format\&format=webp)

Boom!! We finally did this: Setting Up an Application Load Balancer for an EC2 Instance. :)

\#happylearning #loadbalancer #alb