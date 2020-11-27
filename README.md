:black_heart: Run Open▽FOAM ON AWS

### Motivation?
* Play with CFD program
* But do not want to install a program on my personal laptop (memory problem)
* AWS provides free tier for a year, 750h (Hooray)
* Find OpenFOAM on AWS marketplace (high efficiency)
* Do not waste time and effort of struggling and installing all package
* User friendly 
* BUT, MUSH PAY TO DOWNLOAD YOUR DATA


### Launch AWS EC2 instances (FREE) and connect to instance
* Create [AWS account](https://aws.amazon.com/free/?nc1=h_ls&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc)
* Check [CFDDFC on AWS: Launch an Instance with the Console](https://cfd.direct/cloud/aws/launch/)
* Launch an instance 
* Select AWS Marketplace
<div>
<img width="1308" alt="01_AWS_marketplace" src="https://user-images.githubusercontent.com/40614421/100488285-9b9c9c00-310d-11eb-8ae4-2c528ece5a47.png">
</div>

* type `CFDDFC`
<div>
<img width="1306" alt="02_AWS_CFD_direct from the cloud" src="https://user-images.githubusercontent.com/40614421/100488296-a9522180-310d-11eb-9f05-dd1d362831f7.png">
</div>

* Select the CFD Direct From the Cloud (CAUSION! Free tier eligible)
<div>
<img width="1306" alt="03_select_free_tier" src="https://user-images.githubusercontent.com/40614421/100488299-ace5a880-310d-11eb-870f-89ddb64888a9.png">
</div>

* Choose an instance type
<div>
<img width="1309" alt="04_instance type" src="https://user-images.githubusercontent.com/40614421/100488307-b7a03d80-310d-11eb-8738-c5ae7c69de97.png">
</div>

* (additional) configure security group 
<div>
<img width="1308" alt="05_configure_security group" src="https://user-images.githubusercontent.com/40614421/100488312-be2eb500-310d-11eb-9162-1258dc71ff1b.png">
</div>

* Review and click Launch button at the right end
<div>
<img width="1307" alt="07_review instance" src="https://user-images.githubusercontent.com/40614421/100488316-c2f36900-310d-11eb-8292-6c0ae4c92a55.png">
</div>

* Choose an existing key pair or create new one
<div>
<img width="1306" alt="08_key pair" src="https://user-images.githubusercontent.com/40614421/100488320-ca1a7700-310d-11eb-80f8-b902cd57893b.png">
</div>

* Connect to your instance
<div>
<img width="1306" alt="09_connect" src="https://user-images.githubusercontent.com/40614421/100488324-d272b200-310d-11eb-9c73-d0986e19a57b.png">
</div>

* 1st option) connect from the Amazon EC2 console 
> click Connect button at the right end
<div>
<img width="1306" alt="10_connect" src="https://user-images.githubusercontent.com/40614421/100488335-de5e7400-310d-11eb-8712-aa59cf7fc729.png">
</div>

> Following terminal window opens
<div>
<img width="1306" alt="10_2" src="https://user-images.githubusercontent.com/40614421/100488340-e61e1880-310d-11eb-95d2-aa0ea7470b1f.png">
</div>

* 2nd option) connect with SSH client
> copy `ssh -i "your key.pem" ubuntu@your-instance-id.compute.amazonaws.com` 
<div>
<img width="1289" alt="11_connect_ssh" src="https://user-images.githubusercontent.com/40614421/100488346-ecac9000-310d-11eb-9366-013d50da1742.png">
</div>

> open terminal and go to directory where your key.pem locates
```
(base) ist-xxxxxx:~ $ ssh -i "your key.pem" ubuntu@your-instance-id.compute.amazonaws.com
```

### Test OpenFOAM
now, test an [simple example of steady, incompressible, turbulent flow over a backward facing step](https://cfd.direct/cloud/aws/connect/).
```
ip-xxxxx:~ >> run
ip-xxxxx:~ >> cp -r $FOAM_TUTORIALS/incompressible/simpleFoam/pitzDaily .
ip-xxxxx:~ >> cd pitzDaily
ip-xxxxx:~ >> blockMesh
ip-xxxxx:~ >> simpleFoam
```
<div>
<img width="830" alt="12_simple case" src="https://user-images.githubusercontent.com/40614421/100488357-fb934280-310d-11eb-963e-fc82323b7f96.png">
</div>

Now, check results. Folders and files are generated
```
ip-xxxxx:~ >> ls
0 100 200 287 Allrun constant postProcessing system
```
go to one of the folder,
```
ip-xxxxx:~ >> cd 0
ip-xxxxx:~ >> ls
U  epsilon  f  k  nuTilda  nut  omega  p  v2
```
> coming soon...




Enjoy :)
