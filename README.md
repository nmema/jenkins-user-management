# Jenkins User Managment Pipelines
Jenkins jobs for managing Linux system users, including tasks such as creating and removing user accounts.

### Requirements
- [Configuration as Code](https://plugins.jenkins.io/configuration-as-code/) Plugin
- [Job DSL](https://plugins.jenkins.io/job-dsl/) Plugin


### Set Up
Jenkins needs to be in the sudoers group to execute admin commands for management of users. To achive that:
1. Create a `/etc/sudoers.d/jenkins`  
```bash
sudo touch /etc/sudoers.d/jenkins
```
2. Open the file:
```bash
sudo vim /etc/sudoers.d/jenkins
```
3. Paste the following content.
```bash
jenkins ALL=(ALL) NOPASSWD: /usr/sbin/useradd, /usr/bin/passwd
```

This will restrict Jenkins access to a set of commands.

4. Now we need to load the jobs. Copy the raw format of the [jenkins.yaml](./jenkins.yaml)
```bash
https://raw.githubusercontent.com/nmema/jenkins-user-management/refs/heads/main/jenkins.yaml
```

5. In the Jenkins UI, go to `Manage Jenkins` -> `Configuration as Code` -> Paste the URL -> Click on `Apply new configuration`

Now you should see the `UserManagement` folder on the Dashboard.