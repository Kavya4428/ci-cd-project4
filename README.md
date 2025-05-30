# 🐳 CI/CD Pipeline with GitHub Actions & Docker (Local Deployment)

This project demonstrates a complete CI/CD pipeline using GitHub **Actions**, **Docker**, and **Docker Hub**, with deployment on a **local VM** — no cloud provider needed.


## 🚀 Project Objective

- Automatically build a Docker image on every push to the `main` branch
- Push the built image to **Docker Hub**
- Deploy and run the image on a **local VM** using Docker


## 🛠️ Tools Used

- [GitHub Actions](https://github.com/features/actions) – for CI/CD automation
- [Docker](https://www.docker.com/) – containerization and deployment
- [Docker Hub](https://hub.docker.com/) – to store images
- Local VM (Ubuntu/Linux) – for deployment (no cloud)


## 📁 Project Structure

ci-cd-project/
│
├── app.py # Sample Flask app
├── Dockerfile # Docker image definition
├── docker-compose.yml # (optional) for local multi-container setup
├── requirements.txt # Python dependencies
└── .github/
└── workflows/
└── docker.yml # GitHub Actions CI/CD workflow

## Process

**Step 1**: Create Project Folder & Files
bash
mkdir ci-cd-project
cd ci-cd-project

touch app.py requirements.txt Dockerfile docker-compose.yml .github/workflows/ci-cd.yml

**Step 2**: Edit app.py
bash
vi app.py

**Step 3**: Edit requirements.txt
bash
vi requirements.txt

**Step 4**: Edit Dockerfile
bash
vi Dockerfile


**Step 5**: Initialize Git & Push to GitHub
bash
git init
git remote add origin https://github.com/Kavya4428/ci-cd-project4.git
git add .
git commit -m "Initial commit - CI/CD setup"
git branch -M main
git push -u origin main


**Step 6**: Create GitHub Actions Workflow
bash
mkdir -p .github/workflows
vi .github/workflows/docker.yml

Replace your_dockerhub_username with your actual Docker Hub username.
Save and exit.

**Step 7**: To push the workflows into the github

git add .github/workflows/docker.yml
git commit -m "Add CI/CD workflow"
git push

**Step 8**: Set Secrets on GitHub
In your GitHub repo:

Go to Settings → Secrets and variables → Actions → New repository secret
Add:
Name: DOCKER_USERNAME
Value: your Docker Hub username (e.g., Kavya5229)
Do the same for your password:

Name: DOCKER_PASSWORD
Value: your Docker Hub password or access token(better to create access token and use that) or dockerhub password

To create access token: Dockerhub account --> On profile click on Account settings --> Personal Access Tokens --> Generate new token --> Give some token description(name) --> Now, change Access permissions as read & write --> Generate --> copy the token and use it in github secrets


**Step 9**: Set Up Local VM for Deployment
On your VM:
bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

Add your user to Docker group:
bash
sudo usermod -aG docker $USER
Log out & log back in for group changes to apply.

## 🧪 Test Locally on Your VM
Deploy the App on Your VM
On your VM:
## Pull the Docker image:
bash
docker login
give username and token

docker pull your_dockerhub_username/ci-cd-vm:latest
docker run -d -p 5000:5000 your_dockerhub_username/ci-cd-vm:latest

Access the app in your browser:
bash
http://<your-vm-ip>:5000
Use ip a or hostname -I to get your VM's IP.


📸 Deliverables
✅ GitHub repository with working CI/CD pipeline

✅ Docker image: precilitha10/ci-cd-vm

✅ Local deployment screenshots (add below if available)

✅ CI/CD pipeline status shown in Actions tab

## Results:
![Screenshot (174)](https://github.com/user-attachments/assets/737a0f28-15fa-4921-b6cb-2262df283c6f)
![Screenshot (173)](https://github.com/user-attachments/assets/2ce2ed6f-0376-49ce-bb2f-bd0d49d43022)
![Screenshot (172)](https://github.com/user-attachments/assets/5716cf6b-9c84-4f66-bc1f-3f0f23ad141c)
![Screenshot (171)](https://github.com/user-attachments/assets/bd5a1b5b-28d7-4433-ac18-c47a5520b9e8)
![Screenshot (170)](https://github.com/user-attachments/assets/bcdeea84-8925-4c03-ae7c-5af15687339b)
![Screenshot (169)](https://github.com/user-attachments/assets/6525c263-0a11-40ca-a72e-7d59bd7671de)








