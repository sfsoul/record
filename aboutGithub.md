### Checking for existing SSH keys
**检查是否存在公钥（public keys）**

- Open Terminal
- `ls -al ~/.ssh` to see if existing SSH keys are present
- Check the directory listing to see if you already have a public SSH key

**if you donot have an existing public and private key pair, or donot wish to use any that are available to connect to Github,
then generate a new SSH key.**

### Generating a new SSH key and adding it to the ssh-agent
**If you donot want to reenter your passphrase every time you use your SSH key,you can `add your key to the SSH agent`,
which manages your SSH keys and remembers your passphrase.**

#### Generating a new SSH key
- Open Terminal.
- `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"` This creates a new ssh key,using the provided email as a label.
- When you are prompted to "Enter a file in which to save the key", press Enter.This accepts the default file location.
- At the prompt, type a secure passphrase.

#### Adding your SSH key to the ssh-agent
 

### 参考文章
- [Checking for existing SSH keys](https://help.github.com/en/articles/checking-for-existing-ssh-keys)
- [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- [Working with SSH key passphrases](https://help.github.com/en/articles/working-with-ssh-key-passphrases)