# E-commerce Platform Deployment (MarketPeak_Ecommerce) with Git, Linux and AWS 

### MarketPeak_Ecommerce Project

You have been assigned to develop an e-commerce website for a new online marketplace named "MarketPeak." This platform will feature product listings, a shopping cart, and user authentication. Your objective is to utilize Git for version control, develop the platform in a Linux environment, and deploy it on an AWS EC2 instance. Click [here](https://www.tooplate.com/) to search for free HTML websitr template.

### 1.1 Initialize Git Repository

![](./Images/1.%20git%20init.png)

### 1.2 Obtanin and Prepare the E-commerce website Template

Download and prepare a website Template: Extract the downloaded template into your project directory, **MarketPeak_Ecommerce**

![](./Images/2.%20downloaded-template.png)

### 1.3 Stage and Commit the Template to github (create user and email on git)

![](./Images/3.%20git--global.png)

### 1.4 Push the Code to Github Repository

After initilizing the Git repository and adding the e-commerce website template, push your code to a report repository on Github, link your local repository to Github.

``` bash
git remote add origin https://github.com/Sandraolis/MarketPeak_Ecommerce.git
```
- Pushing the code and my commit from my local main branch to my remote repository on github.

``` bash
git push -u origin main
```

- create a `MarketPeak Ecommerce` repo on github and then pushed code and commit from my local to my remote repo.

![](./Images/5.%20code-pushed-togithub.png)

# 2. AWS Deployment

To deplay `Marketpeak_Ecommerce` platform, you will start by setting up the AWS EC2 Instance

![](./images/6.%20EC2-instance.png)


- Connect to instance using ssh

![](./images/7.%20ssh-into-local-terminal.png)


## 2.2 Clone the repository on the Linux server

Before deploying the Ecommerce website platform, you need to clone. clone the Github repo to the EC2 instance. On your EC2 instance, generate SSH keypair using ssh-keygen

![](./images/8.%20ssh-keygen.png)

- deploy and copu your publicl key

``` bash
cat /home/ubuntu/.ssh/id_rsa.pub
```
![](./images/9.%20display&cat-your-public-key.png)

- Add the SSH public key to your Github account.

![](./images/10.%20successfully-sshkey-togitbuh-added.png)

- Use the SSH clone url to clone the repository.

- clone remote repo on EC2 using ssh. you will have to `sudo yum install git` before you can clone git.

![](./images/11.%20sshclone-to-localrepo.png)


- clone to EC2

![](./images/12.%20git-clone-ssh.png)


## 2.3 Install a Web server on EC2

**Apache HTTP Server (httpd)** is a widely used web server that serves HTML files and content over the internet. Installing it on Linux EC2 server allows you to host `MarketPeak E-commerce` site:

Install Apache web server on the EC2 instance. Note that httpd is the software name for Apache on systerns using `yum package manager`.

``` bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

## 2.4 Configure httpd for Website

To serve the website from the EC2 instance, configure httpd to point to the directory on the Linux server where the website code files are stored. Usually in /var/www/html.

Prepare the Web Directory: Clear the default httpd web directory and copy.
MarketPeak Ecommerce website files to it.

- remove, copy and reload file in `/var/www/html`

![](./images/13.%20var-www-html.png)


The directory/var/www/html/is a standard directory structure on Linux systems that host web content, particularly for the Apache HTTP Server.

When you install Apache on a Linux system, the installation process automatically creates this directory. It's designated as the default document root in Apache's configuration, meaning that Apache is set up to serve web files (such as HTML, CSS, and JavaScript files) located in this directory to visitors of your website.

Reload httpd: Apply the changes by reloading the httpd service.

``` bash
sudo systemctl reload httpd
```

- Display the deployed website

![](./images/16.%20website2.png)


# 3. Continuous Integration and Deployment workflow

To ensure a smooth workflow for developing, testing, and deploying your e-commerce platform, follow this structured approach. It covers making changes in a development environment, utilizing version control with Git, and deploying updates to your production server on AWS.

### Step 1: Developing New Features and Fixes

- Create a Development Branch: Begin your development work by creating a separate branch. This isolates new features and bug fixes from the stable version of your website.

- Implement Changes: On the development branch, add your new features or bug fixes. This might include updating web pages, adding new products, or fixing known issues.

- create and switch into new branch
- stage, commit and push.

![](./images/14.%20change-branch.png)


### Step 2: Pull Requests and Merging to the Main branch

Create a Pull Request (PR): On GitHub, create a pull request to merge the development branch into the main branch. This process is crucial for cocde review and maintaining code quality.

Review and Merge the PR: Review the changes for any potential issues. Once satisfied, merge the pull request into the main branch, incorporating the new features or fixes into the production codebase.

- Create pull request.

![](./images/14.%20pull%20request.PNG)

- successfully merge pull request to the main branch

![](./images/15.%20merge%20request.PNG)

``` bash
git commit -m "Add new features or fix bugs"
```

![](./images/15.%20website-display.png)

