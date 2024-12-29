
# Minimal TexLive installation on Arch
- tags: `#git`
- updated: 2024-12-29
- editor: "@nhanthatsu"
---

## 1\. Prerequisite
- `openssh` to key generate.
- `git` to interactive with git, github.

### 1\.1 Git config
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### 1\.2 Install openssh
```bash
sudo pacman -S openssh
```

## 2\. Generate ssh key

### 2\.1 Gen new ssh key
- Check if existed.
```bash
ls -al ~/.ssh
```
- Generate new key
```bash
ssh-keygen -t ed25519 -C "your.email@example.com" # Recommended: Ed25519
# or
ssh-keygen -t rsa -b 4096 -C "your.email@example.com" # RSA (if Ed25519 is not supported)
```

### 2\.2 Add the SSH key to ssh-agent
- start the agent
```bash
eval "$(ssh-agent -s)"
```
- Add your SSH key to the agent
```bash
ssh-add ~/.ssh/id_ed25519 # Or ~/.ssh/id_rsa if you used RSA
```

Copy the public key
Copy the entire output, starting with `ssh-ed25519` or `ssh-rsa` and ending with your email address.
```bash
cat ~/.ssh/id_ed25519.pub # Or ~/.ssh/id_rsa.pub
```

### 3\. Add the SSH key to Github/GitLab/Bitbucket account

With github key type is authentication

```bash
ssh -T git@github.com # For GitHub
ssh -T git@gitlab.com # For GitLab
ssh -T git@bitbucket.org # For Bitbucket
```
> You should see a message like "Hi username! You've successfully authenticated, but GitHub does not provide shell access."

## 4\. Using SSH URLs

```bash
git clone git@github.com:username/repository.git
```









