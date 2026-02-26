<img width="1918" height="910" alt="Screenshot 2026-02-25 143245" src="https://github.com/user-attachments/assets/69a23d28-71ac-4996-9ff9-7df0ab1c013d" />


✅ Method 1: S3 Static Website Hosting (Best for HTML/CSS/JS)
🔹 Step 1: ZIP Extract Cheyyi

Mundu Solar-system-explorer.zip ni extract cheyyi.

Lopala index.html file undali (main page).

🔹 Step 2: S3 Bucket Create Cheyyi

AWS Console → S3

Create Bucket click cheyyi

Bucket name → solar-system-explorer-unique-name

Region → Mumbai (ap-south-1) select cheyyachu

“Block all public access” → ❌ uncheck cheyyi

Create Bucket

🔹 Step 3: Files Upload Cheyyi

Bucket open cheyyi

Upload → extracted files (HTML, CSS, JS, images anni) select cheyyi

Upload complete avvali

🔹 Step 4: Static Website Hosting Enable Cheyyi

Bucket → Properties

Scroll down → Static Website Hosting

Enable

Index document → index.html

Save

Ikkada neeku oka Website Endpoint URL vastundi.

Example:

http://solar-system-explorer.s3-website-ap-south-1.amazonaws.com

Adhi open chesthe nee website live avuthundi 🎉

🔹 Step 5: Public Access Policy Add Cheyyi (Important) --> if bucket is private then you use this step

Bucket → Permissions → Bucket Policy → Paste this:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}

your-bucket-name place lo nee bucket name pettu.

Save ✅

🔄 Website Update Ela Cheyyali?

Future lo changes chesina tarvatha:

HTML file edit cheyyi

S3 bucket ki malli upload cheyyi

Existing file replace avuthundi

Browser lo refresh cheyyi

Deploy automatic ga avuthundi.


note : if u getting any error make sure file must be "public acl enable" make enable  








#DevOps Deployment Flow (CI/CD Pipeline)

Developer → GitHub → Jenkins → Docker Build → EC2 Deploy

👉 GitHub
👉 Jenkins
👉 Docker
👉 Amazon Web Services (EC2)

🔹 STEP 1: EC2 Instance Create Cheyyi

Amazon Linux 2
Ports allow:
22 (SSH)
8080 (Jenkins)
80 (Website)
🔹 STEP 2: git installastion 

sudo yum update -y
sudo yum install git -y
git --version
#git clone https://github.com/username/solar-system-explorer.git

🔹 STEP 3: Jenkins Install Cheyyi

EC2 lo SSH login ayi:

sudo yum update -y
sudo yum install java-17-amazon-corretto -y
sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins

Browser lo open:
http://your-public-ip:8080
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Unlock Jenkins → setup complete cheyyi.

🔹 STEP 4: Docker Install Cheyyi
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ec2-user

Logout → Login again

🔹 STEP 5: Dockerfile Create Cheyyi (Project lo)

Nee HTML project folder lo Dockerfile create cheyyi:

FROM nginx:latest
COPY . /usr/share/nginx/html

STEP 6: Jenkins Pipeline Create Cheyyi

Jenkins → New Item → Pipeline

Pipeline script:

pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/your-username/solar-system-explorer.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t solar-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop solar-container || true
                docker rm solar-container || true
                docker run -d -p 80:80 --name solar-container solar-app
                '''
            }
        }
    }
}

Save → Build Now click cheyyi.

PHASE : Jenkins Pipeline Setup
✅ Step 8: Install Required Plugins

Jenkins → Manage Jenkins → Plugins

Install:

Git plugin

Docker Pipeline plugin

Restart Jenkins.
✅ Step 9: Create Pipeline Job

Jenkins → New Item → Pipeline → Name: solar-project

step 10: go to pipeline syntax ( snippet genereter --> steps 

1) simple step --> git
2) Reposotiry url -->
3) Brand name : EX: main
4) Genarete pipeline script --> then you wil get a git url copy and paste in pipeline script (inside the step 6 jenkins script )

   🎉 Deployment Done

Browser lo open cheyyi:

http://your-public-ip

Website live 🚀

chmod 777 /var/run/docker.sock --> docker run permision deamon permistion 

docker ps






