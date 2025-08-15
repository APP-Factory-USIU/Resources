# A step-by-step guide to set up and use SSH with GitHub (Shoutout to Haymanot77 for the original wiki):

### Note 1: Every command below will be run in default shell environment except the xclip installation for Linux.
### Note 2: The following commands or the git commands don't need sudo privileges, however if prompted run every command as sudo cause the key generated is different for your normal user and the super user.

## Step 1: Check for Existing SSH Keys

First, check if you already have SSH keys on your system:

	sh
	
	ls -al ~/.ssh
	
	(Look for files named id_rsa and id_rsa.pub (or similar with different names like id_ed25519).)

## Step 2: Generate a New SSH Key

If you don’t have an SSH key, generate one:

	ssh-keygen -t ed25519 -C "your_email@example.com"
	
	OR 

	ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
	
	You’ll be prompted to enter a file path to save the key. Press Enter to accept the default options.
	
	After here, use the command that corresponds to the key you generated in this step.

## Step 3: Add Your SSH Key to the SSH Agent

Start the SSH agent in the background:

	eval "$(ssh-agent -s)"

Add your SSH private key to the SSH agent:

	ssh-add ~/.ssh/id_ed25519 
	
	Or
	
	ssh-add ~/.ssh/id_rsa
	
## Step 4: Add Your SSH Key to GitHub. Copy it to the clipboard:

On MacOS: 
	
	pbcopy < ~/.ssh/id_ed25519.pub
	
	OR
	
	pbcopy < ~/.ssh/id_rsa.pub
	
On Linux:

	First install xclip using one of these commands depending on what distro you use.
	
	sudo apt-get install xclip (For Debian)
	sudo pacman -S xclip (For Arch)
	sudo dnf install xclip (For Fedora)
	
	xclip -sel clip < ~/.ssh/id_ed25519.pub
	
	OR
	
	xclip -sel clip < ~/.ssh/id_rsa.pub
	
On Windows: 

    cat ~/.ssh/id_ed25519.pub | clip
    
    OR
    
    cat ~/.ssh/id_rsa.pub | clip
	
Add the SSH key to GitHub:

	Go to GitHub's SSH and GPG keys settings.
	Click on "New SSH key".
	Paste your key into the "Key" field.
	Add a descriptive title (e.g., "My Laptop Key").
	Click "Add SSH key".
	
## Step 5: Test Your SSH Connection
Run the command:

	ssh -T git@github.com
	
You should see a message like: 

	Hi username! You've successfully authenticated, but GitHub does not provide shell access.

## Step 6: Test by Pulling or Pushing a repo.

These two properly test if you've done these steps correctly since git clone works fine as long as you have git installed on your machine.

    git push -u origin main
    
    OR
    
    git pull (repo SSH/HTTP)

If the SSH is set up correctly, you should see something similar to this if you used pull:

    remote: Enumerating objects: 12, done.
	remote: Counting objects: 100% (12/12), done.
	remote: Compressing objects: 100% (10/10), done.
	remote: Total 12 (delta 2), reused 11 (delta 1), pack-reused 0 (from 0)
	Unpacking objects: 100% (12/12), 3.59 KiB | 1.79 MiB/s, done.
	From github.com:username/repo
	* branch            HEAD       -> FETCH_HEAD

## Summary
Generate a key if you don't have one. Add it to your agent and upload it to GitHub. Pull and pull a repo using SSH URL.


