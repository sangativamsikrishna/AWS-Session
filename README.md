# Deploying a Node Js Application on AWS EC2

### Testing the project locally

1. Clone this project
```
git clone https://github.com/verma-kunal/AWS-Session.git
```
2. Setup the following environment variables - `(.env)` file
```
DOMAIN= ""
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY=""
SECRET_KEY=""
```
3. Initialise and start the project
```
npm install
npm run start
```

### Set up an AWS EC2 instance

1. Create an IAM user & login to your AWS Console
    - Access Type - Password
    - Permissions - Admin
2. Create an EC2 instance
    - Select an OS image - Ubuntu
    - Create a new key pair & download `.pem` file
    - Instance type - t2.micro
3. Connecting to the instance using ssh
```
ssh -i instance.pem ubunutu@<IP_ADDRESS>
```

### Configuring Ubuntu on remote VM

1. Updating the outdated packages and dependencies
```
sudo apt update
```
3. Install Git - [Guide by DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-22-04) 
4. Configure Node.js and `npm` - [Guide by DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-22-04)

### Deploying the project on AWS

1. Clone this project in the remote VM
```
git clone https://github.com/verma-kunal/AWS-Session.git
```
2. Setup the following environment variables - `(.env)` file
```

This .env file contains the details of Publishable Key and Secret Key from stripe Website . Got to developrs and API Keys , you will get the keys their and paste it in bottom of your .env file

 After creating .env file you shoud run the following commands  to execute it
  $ npm install - It will install all packages
  $ npm run start - It will start the application on port no 3000 and you should open it in EC2 Security Gropus. 
  
   Then finally run the app in web browser http:// <public Ip:3000>/
   
DOMAIN= "http:// <public Ip:3000>/"
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY="pk_test_51N9SecSHA1SReqCrhVasZywYf4x5v3Wz9EKaiwVEn0sXwjTggZHH8TCttpP8VnX5mZjlFhULYsw9wBUpupcT9i0u00SAUD4ilD"
SECRET_KEY="sk_test_51N9SecSHA1SReqCrs5dwLOCJNGWGj3rRhG1QbYfRybuT5jh6u7GKZFNNTUzbQ2oTGpOEB6payPBZFC90CxXHT29Q00SwjlKM6G"
```
> For this project, we'll have to set up an [Elastic IP Address](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html) for our EC2 & that would be our `DOMAIN`

3. Initialise and start the project
```
npm install
npm run start
```

> NOTE - We will have to edit the **inbound rules** in the security group of our EC2, in order to allow traffic from our particular port

### Project is deployed on AWS 🎉
