# Installing pepr
## Initial installation
### pepr itself
```
cd /tmp/
git clone https://terrets@bitbucket.cd.auspost.com.au/scm/st/pepr.git
sudo cp -v ./pepr /usr/local/bin/
sudo cp -v ./awssh /usr/local/bin/
cd
```
### bash completion
```
sudo cp -v ./bash_completion.pepr /etc/bash_completion.d/pepr
cd /etc/bash_completion.d/
complete -F _pepr pepr
```
## Update
```
cd /tmp/pepr/
git pull
rm -f /tmp/pepr-$(whoami)/pepr.ap-prod.stacks.list /tmp/pepr-$(whoami)/pepr.ap-test.stacks.list /tmp/pepr-$(whoami)/pepr.ap-dev.stacks.list
sudo cp -v ./pepr /usr/local/bin/
cd
```
