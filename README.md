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
[\\\Fig.1]
</div>
* type `CFDDFC`
<div>
[\\\Fig.2]
</div>
* Select the CFD Direct From the Cloud (CAUSION! Free tier eligible)
<div>
[\\\Fig.3]
</div>
* Choose an instance type
<div>
[\\\Fig.4]
</div>
* (additional) configure security group 
<div>
[\\\Fig.5]
</div>
* Review and click Launch button at the right end
<div>
[\\\Fig7]
</div>
* Choose an existing key pair or create new one
<div>
[\\\Fig8]
</div>
* Connect to your instance
<div>
[\\\Fig9]
</div>
* 1st option) connect from the Amazon EC2 console 
> click Connect button at the right end
<div>
[\\\Fig10]
</div>
> Following terminal window opens
<div>
[\\\Fig10_2]
</div>
* 2nd option) connect with SSH client
> copy `ssh -i "your key.pem" ubuntu@your-instance-id.compute.amazonaws.com` 
<div>
[\\\Fig11]
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
[\\\Fig12]
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
?coming soon...




Enjoy :)
