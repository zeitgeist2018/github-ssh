# github-ssh
Steps to add an ssh key to github on Mac OS.

# Steps
1. Generate ssh key in your computer: `ssh-keygen -t rsa -b 4096 -f ~/.ssh/github -q -N ""`
2. Start ssh agent in the background: `eval "$(ssh-agent -s)"`
3. Add key to ssh agent and MacOS keychain:
```
cat <<EOF >> ~/.ssh/config     
  Host *
    AddKeysToAgent yes
    UseKeychain yes
    IdentityFile ~/.ssh/github
EOF

```
`ssh-add -K ~/.ssh/id_rsa`
4. Copy generated key to clipboard: `pbcopy < ~/.ssh/github.pub`
5. Navigate to https://github.com/settings/ssh/new and add a title and the key itself.
