### About SSH
**Using the SSH protocal, you can connect and authenticate to remote servers and services. With SSH keys,
you can connect to Github without supplying your username or password at each visit.**
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
**解决每次push代码时都要输入`Enter passphrase for key '/Users/jing_zhang/.ssh/id_rsa':` 密码的问题。**

**When adding your SSH key to the agent, use the default macOS `ssh-add` command.**

- Start the ssh-agent in the background  `eval "$(ssh-agent -s)"` 
- If you are using macOS Sierra 10.12.2 or later, you will need to modify your `~/.ssh/config`（if donot have config file, just create） file to automatically load keys into the ssh-agent and store passphrase in your keychain.
```
Host *
  AddkeysToAgent yes 
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```
- `ssh-add -K ~/.ssh/id_rsa`  Add your SSH private key to the ssh-agent and store your passphrase in the keychain.

### Testing your SSH connection
- `ssh -T git@github.com`
- Verify that the fingerprint in the message you see matches one of the message in step 1,then type `yes`：
```
> Hi username! You have successfully authenticated, but Github does not provide shell access
```
### Working with SSH key passphrases
**You can secure your SSH keys and configure an authentication agent so that you won't have to reenter
your passphrase every time you use your SSH keys.**

With SSH keys, if someone gains access to your computer, they also gain access to every system that uses that key.
To add an extra layer of security, you can add a passphrase to your SSH key. You can use `ssh-agent` to securely
save your passphrase so you don't have to reenter it.

#### Adding or changing a passphrase
```
$ ssh-keygen -p
# Start the SSH key creation process
> Enter file in which the key is (/Users/you/.ssh/id_rsa): [Hit enter]
> Key has comment '/Users/you/.ssh/id_rsa'
> Enter new passphrase (empty for no passphrase): [Type new passphrase]
> Enter same passphrase again: [One more time for luck]
> Your identification has been saved with the new passphrase.
```
**If your key already has a passphrase, you will be prompted to enter it before you can change to a new passphrase.**

#### Saving your passphrase in the keychain
The first time you use your key, you will be prompted to enter your passphrase. If you choose to
save the passphrase with your keychain, you won't have to enter it again.
Otherwise, you can store your passphrase in the keychain when you add your key to the ssh-agent.
 

### 参考文章
- [Checking for existing SSH keys](https://help.github.com/en/articles/checking-for-existing-ssh-keys)
- [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- [Working with SSH key passphrases](https://help.github.com/en/articles/working-with-ssh-key-passphrases)
- [MAC终端 SSH登陆：Enter passphrase for key](https://www.jianshu.com/p/5a5f3867d425)
- [Adding a new SSH key to your Github account](https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account)
- [About SSH](https://help.github.com/en/articles/about-ssh)
- [Connecting to Github with SSH](https://help.github.com/en/articles/connecting-to-github-with-ssh)