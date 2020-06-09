# Profile-less pepr
No need to know to which profile (ap-dev, ap-test, ap-prod) a stack belongs. Simply type all or part of the stack name and pepr will manage.
## Future syntax
| Command | Parameter(s) | Function |
| ------- | ------------ | -------- |
| pepr    | -h / --help  | Display help |
| pepr    | -v / --version | Display version |
| pepr    |              | Called without parameters, pepr will list the AWS profiles configured in your `$HOME/.aws/credentials` file. |
| pepr    | <profile\>   | List the stacks         |
| pepr    | <stack\> | List the instances of a stack (stack name can be partial, no need for a joker) |
| pepr    | <stack\> <option\> | Option can be \! (SSH to all instances) or \~ (SSH to any instance) |
| pepr    | <stack\> <ID1\> ... <IDn\> | SSH to several instances from the same stack | 
