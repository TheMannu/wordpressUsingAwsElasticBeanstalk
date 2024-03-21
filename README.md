# Project  → Deploying wordpress website on AWS using elastic beanstalk
### Elastic beanstalk →
It is simply called serverless computing or you just need to provide a code of your application to aws and aws itself manage everything in their end such as managing load on server,storage,type of instance etc…

### Prerequisites →
In this project we assume that you have basic knowledge of Elastic beanstalk and aws and have some hands on linux operating system

### Launch RDS database →
step 1 → Search RDS on aws console and then click on create database

step 2 → choose standard create and then mysql engine

step 3 →set your master name and password you could also autogenerate the password

step 4 → give the name to your database in the additional configuration and remain everything as it is and click on create database it takes up to 3 to 4 minutes to configure everything

### Launch elastic beanstalk environment →
step 1 →Search Elastic beanstalk on aws console and then click on create application

step 2 →choose web server environment and then give name to your application

step 3 →choose php from managed platform and then click next

step 4 → In service role click create and use new service role and select aws-elasticbeanstalk-service-role from it

step 5 →choose your ec2 keypair and your ec2 instance profile to ec2accessdemoapp

step 6 → In VPC choose default vpc and then select your instance subnet and database subnets

click next

step 7 →select the default security group from the options and click next

step 8 → in health reporting choose basic and untick the manged updates options

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

Step 10 → review your configuration and click on sumbit

### It takes around 5 min to create your application

### click on url provided by elastic beanstalk you will find a page 

### Download Wordpress →
step 1 → go to your ubuntu terminal and create dir mkdir git run

cd git
apt install git
git clone https://github.com/Aakibgithuber/deploy-wordpress-
zip ../your_folder_name.zip -r * .[^.]*

### Upload and deploy →
step 1 →go to your elastic beanstalk console choose the environment you created above and select upload and deploy option choose your wordpress file that you just downloaded and click on deploy

It also takes around 5 min to deploy the application

after it successful deployment click on url but it shows 404 ngnix not found

to overcome this error →
step 1 → go to your ec2 dashboard and choose the instance created by elastic beanstalk

step 2 → copy the public ip and take ssh of that machine from your terminal by running

ssh -i <your key pair name > ec2-user@<public ip>

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




