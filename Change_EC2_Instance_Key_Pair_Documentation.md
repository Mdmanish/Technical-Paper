### **Documentation for Changing the Key Pair of an Already Created AWS EC2 Instance**

This documentation outlines the steps to securely replace an existing key pair for an AWS EC2 instance. It includes considerations for cases where multiple `.ssh` directories exist.

---

## **Steps to Replace Key Pair**

### **1. Generate a New Key Pair**
1. **Using AWS Management Console**:
   - Navigate to **EC2 Dashboard** → **Key Pairs**.
   - Click **Create Key Pair**.
   - Provide a name for the key pair and choose the **PEM** format (for Linux).
   - Click **Create** and download the private key file (`<new-key>.pem`).
   - **Important**: Keep the private key secure and set appropriate permissions:
     ```bash
     chmod 400 <new-key>.pem
     ```

2. **Using AWS CLI**:
   - Run the following command to create a new key pair and save the private key:
     ```bash
     aws ec2 create-key-pair --key-name <new-key-name> --query "KeyMaterial" --output text > <new-key-name>.pem
     ```
   - Ensure proper permissions for the private key:
     ```bash
     chmod 400 <new-key-name>.pem
     ```

---

### **2. Add the New Key to the Instance**

#### **Case 1: Single `.ssh` Directory**
If the instance has a single `.ssh` directory (usually `~/.ssh`):
1. **SSH into the Instance** using the existing key pair:
   ```bash
   ssh -i <old-key.pem> <username>@<instance-ip>
   ```

2. **Extract the New Public Key**:
   - Generate the public key from the new private key:
     ```bash
     ssh-keygen -y -f <new-key.pem> > <new-key.pub>
     ```

3. **Add the New Public Key to the `authorized_keys` File**:
   - Append the new public key to the `authorized_keys` file:
     ```bash
     echo "<new-public-key-content>" >> ~/.ssh/authorized_keys
     ```
   - Ensure the file has the correct permissions:
     ```bash
     chmod 600 ~/.ssh/authorized_keys
     ```

4. **Test the New Key**:
   - Open a new terminal and test the new key:
     ```bash
     ssh -i <new-key.pem> <username>@<instance-ip>
     ```

5. **Revoke the Old Key**:
   - Once the new key is verified, remove the old key from the `authorized_keys` file:
     ```bash
     nano ~/.ssh/authorized_keys
     ```
   - Delete the line containing the old key and save the file.

---

#### **Case 2: Multiple `.ssh` Directories**
Instances may have multiple `.ssh` directories depending on the users or configurations (e.g., `/root/.ssh`, `/home/ubuntu/.ssh`).

1. **Identify the Active User**:
   - Determine the user you're connecting with (`root`, `ubuntu`, or another user).
   - Check the SSH command you use to connect:
     ```bash
     ssh -i <old-key.pem> root@<instance-ip>
     ssh -i <old-key.pem> ubuntu@<instance-ip>
     ```

2. **Find the Correct `.ssh/authorized_keys` File**:
   - Check the `.ssh` directories for each user:
     ```bash
     ls -l /root/.ssh
     ls -l /home/ubuntu/.ssh
     ```
   - Locate the file containing the public key used for your current connection:
     ```bash
     cat ~/.ssh/authorized_keys
     ```

3. **Add the New Key**:
   - Append the new public key to the correct `authorized_keys` file:
     ```bash
     echo "<new-public-key-content>" >> /path/to/correct/authorized_keys
     ```
   - Ensure the file has proper permissions:
     ```bash
     chmod 600 /path/to/correct/authorized_keys
     ```

4. **Test and Revoke Old Key**:
   - Test the new key with the appropriate user (e.g., `root` or `ubuntu`).
   - Remove the old key after verifying the new key works.

---

### **3. Handling Instances Without Key-Based Access**
If you cannot access the instance with an existing key:
- **Use EC2 Instance Connect** (for supported AMIs):
  1. Go to the EC2 Dashboard, select the instance.
  2. Click **Connect** → **EC2 Instance Connect**.
  3. Use the terminal to add the new public key to the correct `authorized_keys` file.

- **Use a User Data Script** (if EC2 Instance Connect is unavailable):
  1. Stop the instance.
  2. Detach its root volume and attach it to a temporary instance.
  3. Mount the volume and navigate to the `.ssh` directory.
  4. Add the new public key to the `authorized_keys` file.
  5. Reattach the volume to the original instance and start it.

---

### **4. Update the AWS Console Key Pair (Optional)**
AWS does not automatically manage keys within the instance. You can update documentation or tags to indicate the new key pair in use.

---

### **5. Automating with Scripts**
For environments with multiple instances, consider automating key rotation using a script or AWS Systems Manager:
1. Use Systems Manager to distribute and update public keys across instances.
2. Automate the process with an Ansible playbook or a custom script.

---

### **6. Verify and Document**
- **Verification**:
  - Confirm the new key works and all old keys are removed.
  - Ensure SSH access is limited to trusted users and IPs.
- **Documentation**:
  - Record the new key pair name and the users/instances it applies to.
  - Update AWS tags or notes to reflect the key pair change.
