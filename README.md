# PEPR
## Features
- Explore our stacks directly from your computer,
- Connect to multiple EC2 instances in one go.
## Requirements
- The file `$HOME/.aws/config` must exist and contain the right AWS Access Key ID & AWS Secret Access Key depending on the accounts you need to get access to,
- Report to [this documentation](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html) to set it up if necessary.
## Usage
### Availability
*pepr* must be installed on your workstation or on your company's bastion/jump host.
Check the INSTALL file.
### Syntax
| Command | Parameter(s) | Function |
| ------- | ------------ | -------- |
| pepr    | -h / --help  | Display help |
| pepr    | -v / --version | Display version |
| pepr    |              | Called without parameters, *pepr* will list the AWS profiles configured in your `$HOME/.aws/config` file. |
| pepr    | <profile\>   | List the stacks         |
| pepr    | <profile\> <stack\> | List the instances of a stack (stack name can be partial, no need for a joker) |
| pepr    | <profile\> <id\> | SSH to instance     |
| pepr    | <profile\> <stack\> <ID1\> ... <IDn\> | SSH to several instances |
| pepr    | <profile\> <stack\> <tiers\> | SSH to instances from a tier |
| pepr    | <profile\> <stack\> \! | SSH to all instances from a stack |
| pepr    | <profile\> <stack\> \~ | SSH to one instance from a stack |
### About the usage of GNU/Screen
*pepr* uses [GNU/Screen](https://www.gnu.org/software/screen/) to open multiple SSH connections in multiple terminals while using only one screen. The [manual is available online](http://www.gnu.org/software/screen/manual/screen.html), but it is unlikely you will ever need to look at it; the few things you have to know are available below.
#### Shortcuts
| Shortcut | Effect |
| -------- | ------ |
| Ctrl + a " | Select a window / virtual terminal |
| Ctrl + a \\ | Quit Screen |
| Ctrl + a S | Horizontally split screen in half |
| Ctrl + a Tab | Switch from one half to another (switch from one region to another) |
## Troubleshooting
### Target platforms
As of now, pepr is running on GNU/Linux and Apple Mac OS X.
### Logfile location
*pepr* log its actions in `/var/log/messages`
### The number of stacks / instances doesn't match reality
This happens when the query made to AWS took more than 20 seconds to complete; *pepr* is programmed to react this way in order to avoid wasting your time.
### The instance ID doesn't exist
The full error message is:
```
A client error (InvalidInstanceID.NotFound) occurred when calling the DescribeInstances operation: The instance ID 'i-aabbccdd' does not exist
```
This error occurs when pepr is using outdated cached information. The fix is to delete the cache files:
```
cd /tmp/
rm -fr ./pepr-$(whoami)/
```
