# Auto Deployment of Code from GitHub to AWS EC2

This guide explains how to set up automatic code deployment to an AWS EC2 instance using GitHub. You will switch your repository to use SSH for secure communication, configure your EC2 instance to work with GitHub via SSH, and ensure everything is properly set up for automated deployment.

## Prerequisites

- An AWS EC2 instance running and accessible via SSH.
- Git installed on your EC2 instance.
- A GitHub repository that you want to deploy.

## Step 1: Connect to Your EC2 Instance

To start, connect to your EC2 instance using SSH from your terminal:

```bash
ssh -i /path/to/your-key.pem ec2-user@your-ec2-ip-address
```

Replace `/path/to/your-key.pem` with the path to your EC2 key pair and `your-ec2-ip-address` with the public IP of your EC2 instance.

## Step 2: Check the Current Git Remote Configuration

Run the following command to check the remote URL of your repository:

```bash
git remote -v
```

If the output shows something like this (indicating you're using HTTPS):

```bash
origin  https://gitlab.com/your-username/your-repository.git (fetch)
origin  https://gitlab.com/your-username/your-repository.git (push)
```

You will need to switch to SSH for a more secure connection. Continue to the next step to change the remote URL.

## Step 3: Change Remote URL to Use SSH

To switch your repository to use SSH instead of HTTPS, run the following command:

```bash
git remote set-url origin git@github.com:your-username/your-repository.git
```

Now, verify the change:

```bash
git remote -v
```

The output should look like this:

```bash
origin  git@github.com:your-username/your-repository.git (fetch)
origin  git@github.com:your-username/your-repository.git (push)
```

## Step 4: Generate an SSH Key Pair (If Needed)

If you don’t already have an SSH key pair, you’ll need to generate one. Run the following command:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

This will generate two files in your current directory:

- `id_ed25519`: Your private key (keep this secure and do not share it).
- `id_ed25519.pub`: Your public key (this will be added to GitHub).

Make sure these files are in your `~/.ssh/` directory. If they are not, move them using the following commands:

```bash
mv id_ed25519 ~/.ssh/
mv id_ed25519.pub ~/.ssh/
```

## Step 5: Set Correct Permissions for SSH Keys

Once your keys are in the `~/.ssh/` directory, you need to set the appropriate permissions:

```bash
chmod 600 ~/.ssh/id_ed25519
```

## Step 6: Add the SSH Key to the SSH Agent

Start the SSH agent and add your private key to it:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

## Step 7: Add Your SSH Key to GitHub

Copy the contents of your public key file (`id_ed25519.pub`) and add it to GitHub. You can do this by running:

```bash
cat ~/.ssh/id_ed25519.pub
```

1. Copy the output.
2. Go to your GitHub account.
3. Navigate to **Settings** > **SSH and GPG keys** > **New SSH key**.
4. Paste the copied key into the "Key" field and give it a recognizable title.
5. Click **Add SSH key**.

## Step 8: Test Your SSH Connection to GitHub

To ensure everything is working correctly, test the SSH connection to GitHub:

```bash
ssh -T git@github.com
```

If everything is set up properly, you should see a message like this:

```bash
Hi <username>! You've successfully authenticated, but GitHub does not provide shell access.
```

This confirms that your EC2 instance can communicate with GitHub using SSH.

## Step 9: Set Up GitHub Actions for Auto Deployment

### Creating the `deploy.yml` File

To automate deployment, create a `.github/workflows/deploy.yml` file in your repository with the following content:

```yaml
name: Deploy to AWS EC2 (Single Production Instance)

on:
  push:
    branches:
      - master  # Trigger deployment on push to the master branch

jobs:
  deploy_production:
    if: github.ref == 'refs/heads/master'
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2  # Checks out the repository code

    - name: Set up Python
      uses: actions/setup-python@v2
      with:
        python-version: '3.10.12'  # Sets the Python version to use

    - name: Deploy to Production EC2
      env:
        AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}   # AWS Access Key
        AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}  # AWS Secret Access Key
        AWS_REGION: ${{ secrets.AWS_REGION }}  # AWS Region
        EC2_HOST: ${{ secrets.EC2_HOST_PROD }}  # Production EC2 Host
        SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}  # SSH Private Key
        EC2_USER: ${{ secrets.EC2_USER }}  # EC2 Username
      run: |
        # Create a temporary private key file for SSH access
        printf "%s" "${SSH_PRIVATE_KEY}" > private_key.pem
        chmod 600 private_key.pem  # Set permissions for the private key

        # SSH into the production EC2 instance
        ssh -o StrictHostKeyChecking=no -i private_key.pem $EC2_USER@$EC2_HOST << 'EOF'
          sudo -s  # Switch to superuser if needed
          cd /var/www/html/oridosai-api-backend  # Navigate to the project directory
          git stash  # Stash any local changes
          git pull origin master  # Pull the latest code from the master branch

          # Activate the Python virtual environment
          source /var/www/html/oridosai-api-backend/venv/bin/activate
          pip install -r requirements.txt  # Install the required Python packages

          # Uncomment the following lines to apply database migrations and collect static files
          # python manage.py migrate
          # python manage.py collectstatic --noinput

          # Restart application processes. Adjust command based on your process manager.
          echo "Make sure to restart your application process. Adjust the command below as necessary:"
          echo "sudo supervisorctl restart all  # This may not be correct for everyone."
          # Replace the above command with your process manager's restart command, e.g.:
          sudo supervisorctl restart all
        EOF

    - name: Cleanup private key
      run: rm private_key.pem  # Remove the private key file for security
```

### Adding GitHub Secrets

To securely store sensitive information, such as your EC2 SSH private key, add it to GitHub Secrets:

1. Go to your GitHub repository.
2. Click on **Settings**.
3. In the left sidebar, click on **Secrets and variables** > **Actions**.
4. Click **New repository secret**.
5. Name your secret (e.g., `EC2_SSH_PRIVATE_KEY`) and paste your private key.
6. Click **Add secret**.

Repeat the process for any other sensitive information your deployment might require (e.g., AWS_SECRET_ACCESS_KEY).

## Conclusion

With these steps, you have successfully set up SSH communication between your AWS EC2 instance and GitHub, allowing you to securely deploy code from your GitHub repository. By utilizing GitHub Actions with the `deploy.yml` configuration, you can automate your deployment process to both production and staging (if required) environments. You can now easily manage and deploy your applications as needed.
