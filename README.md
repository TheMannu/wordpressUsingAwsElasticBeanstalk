# Project  → Deploying wordpress website on AWS using elastic beanstalk
### Elastic beanstalk →
It is simply called serverless computing or you just need to provide a code of your application to aws and aws itself manage everything in their end such as managing load on server,storage,type of instance etc…

### Prerequisites →
In this project we assume that you have basic knowledge of Elastic beanstalk and aws and have some hands on linux operating system

### Launch RDS database →
step 1 → Search RDS on aws console and then click on create database

step 2 → choose standard create and then mysql engine


![Screenshot (243)](https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk/assets/84488161/97e07011-62b9-437d-b0aa-ef671b37f233)



step 3 →set your master name and password you could also autogenerate the password

step 4 → give the name to your database in the additional configuration and remain everything as it is and click on create database it takes up to 3 to 4 minutes to configure everything


![Screenshot (244)](https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk/assets/84488161/4caf3c68-77f2-455f-abe9-904bd1d586f1)



### Launch elastic beanstalk environment →
step 1 →Search Elastic beanstalk on aws console and then click on create application

step 2 →choose web server environment and then give name to your application

step 3 →choose php from managed platform and then click next


![Screenshot (245)](https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk/assets/84488161/a4c39e67-8b53-480d-909f-9a751b440aa4)


step 4 → In service role click create and use new service role and select aws-elasticbeanstalk-service-role from it

step 5 →choose your ec2 keypair and your ec2 instance profile to ec2accessdemoapp


![word4](https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk/assets/84488161/3eb8f2a0-ea3a-4932-84fb-1db871f236d3)


### note: key pair must be present in your localhost


step 6 → In VPC choose default vpc and then select your instance subnet and database subnets

click next

step 7 →select the default security group from the options and click next


![word5](https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk/assets/84488161/9aeaf443-2348-4559-9593-81533fad285f)



step 8 → in health reporting choose basic and untick the manged updates options

![word6](https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk/assets/84488161/57e8d3e1-a616-457b-a58d-e604d78c7c64)



step 9 → Now connect your database by adding environment properties

## 1. RDS_HOSTNAME

The hostname of the DB instance.

where to find →On the Connectivity & security tab on the Amazon RDS console: Endpoint.

## 2. RDS_PORT

The port where the DB instance accepts connections. The default value varies among DB engines.

where to find →On the Connectivity & security tab on the Amazon RDS console: Port.

## 3. RDS_DB_NAME

The database name, ebdb.

where to find →On the Configuration tab on the Amazon RDS console: DB Name.

## 4.RDS_USERNAME

The username that you configured for your database.

where to find →On the Configuration tab on the Amazon RDS console: Master username.

## RDS_PASSWORD

The password that you configured for your database.

Not available for reference in the Amazon RDS console.


![word7](https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk/assets/84488161/8612bee2-b46f-4fb5-9d4a-0ff8dfe402c5)


Step 10 → review your configuration and click on sumbit

### It takes around 5 min to create your application

### click on url provided by elastic beanstalk you will find a page 



![word8](https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk/assets/84488161/d9729217-ecff-4c7c-b6d1-c755845cd44e)



### Download Wordpress →
step 1 → go to your ubuntu terminal and create dir mkdir git run

cd git
apt install git
git clone https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk.git
zip ../your_folder_name.zip -r * .[^.]*

### Upload and deploy →
step 1 →go to your elastic beanstalk console choose the environment you created above and select upload and deploy option choose your wordpress file that you just downloaded and click on deploy


![word9](https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk/assets/84488161/00be3927-eb87-4fcf-8317-d20d34bdf2a5)



It also takes around 5 min to deploy the application

after it successful deployment click on url but it shows 404 ngnix not found


![word10](https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk/assets/84488161/96b6c119-3e5a-4e69-8f75-046905aa08e0)



to overcome this error →
step 1 → go to your ec2 dashboard and choose the instance created by elastic beanstalk

step 2 → copy the public ip and take ssh of that machine from your terminal by running

ssh -i <your key pair name > ec2-user@<public ip>


![word11](https://github.com/TheMannu/wordpressUsingAwsElasticBeanstalk/assets/84488161/c2071f29-6835-4375-a709-c994a718550b)


step 3 → run the following commands

sudo su
cd /var/www/html/
### this will let you to go to the location where the actual file is present that you uploaded from console

3. mv wordpress/* / var/www/html/

### this command will move the entire files from from wordpress folder

4. rm -rf wordpress

### this command will delete the wordpress folder

now again click on url you will find a web page where you wordpress application running

# congratulations!!




