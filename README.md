# setup-ec2-color

## Setup
To Run This on Your New EC2 Instance:
	1.	Copy this script and save it as setup_colors.sh on your new EC2 instance.
	2.	Give it execute permission:

1. Create a script on your local machine (e.g., setup-ec2-color.sh):

   ```bash
  	#!/bin/bash
   # Set terminal to 256 colors
   echo 'export TERM=xterm-256color' >> ~/.bashrc
   # Enable color support for ls
   echo 'if [ -f /etc/lsb-release -o -d /etc/lsb-release.d ]; then' >> ~/.bashrc
   echo '    alias ls="ls --color=auto"' >> ~/.bashrc
   echo 'fi' >> ~/.bashrc
   # Ensure .bashrc loads on SSH
   echo 'if [ -f ~/.bashrc ]; then' >> ~/.profile
   echo '    . ~/.bashrc' >> ~/.profile
   echo 'fi' >> ~/.profile
   # Apply changes
   source ~/.bashrc
   source ~/.profile
   ```

2. Give it execute permission:

   ```bash
   chmod +x setup-ec2-color.sh
   ```
3. Run the script:

   ```bash
   ./setup_colors.sh
   ```
4. Run the script:

   ```bash
   exit
   ssh -i "your-key.pem" ubuntu@your-ec2-public-ip
   ```
3. Verify settings:

   ```bash
   echo $TERM   # should return 'xterm-256color'
   ls --color=auto  # should show colored output
   ```


## Manually

- First create a docker image from Dockerfile
```bash
docker build -t flaskapp .
```

- Now, make sure that you have created a network using following command
```bash
docker network create  -d bridge flaskapp-ntwk
```
