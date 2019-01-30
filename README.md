## What is this?
This is :
* an example of how to use AWS IAM Permission boundaries in Cloudformation
* an example of how to enforce users to attach a boundary to IAM Users they create - the same can work for IAM Roles


## How does this work?
Within ```example.template.yaml``` you can see an AWS IAM managed policy ```ApprovedIAMActionsPolicy```.  This is an 
example white list of actions your users are allowed to perform.  The idea here is that this is your allowed actions for 
your users.

Within ```example.template.yaml``` you can see can also see an AWS IAM managed policy ```BindingUserPolicy```.  This 
is to be used as a boundary for an IAM Role or User - as specified in the IAM Role ```RoleWithBoundary```.  The 
noteworthy lines are within the Sid ```BoundActions```.  The ``` StringEquals:
iam:PermissionsBoundary: !Sub arn:aws:iam::${AWS::AccountId}:policy/ApprovedIAMActionsPolicy``` is where the magic 
happens.

## Credits
The example (and the know-how) were derived from [here](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html)  
