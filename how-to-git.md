# GIT 
If you already have an RSA id for SSH - great, otherwise generate one.

## Gitlab setup
Register our public RSA id with Gitlab:
```cat ~/.ssh/id_rsa.pub```
1 .Copy the output (ssh-rsa AAAA......== my@user) 
1. Go to https://gitlab.....at/profile/keys/new  
1. Add a title and paste the RSA key from before

## RSA key test
Open a terminal, select an empty directory where you want to put the repository and type:
```git clone git@gitlab..../my-repos.git```
If you get asked 
* The authenticity of host 'gitlab.... (...)' can't be established.  **yes**
* For a password **Problem**

## User setup
Since the authentication via RSA works, let's make the access easier.

    #Open config file
    vi .ssh/config
    #add the configuration (not to forget the git user)
    Host hgit
      Hostname gitlab....
      User git

And GIT global variables:

    git config --global user.name "Your name"
    git config --global user.email "$USER@my-great-url.at"

Now the command changes to 
```git clone hgit:ngs.git```
