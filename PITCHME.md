## AWS SSM

AWS DC Meetup

6-Feb-2018

[github.com/dougtoppin/presentation-aws-ssm](https://github.com/dougtoppin/presentation-aws-ssm)

Doug Toppin

dougtoppin@gmail.com

@dougtoppin

---
### Agenda

* SSM (primarily Run Command)
* Parameter Store
* Demos
* Links

---

## SSM

---

"AWS Systems Manager is a collection of capabilities that helps you automate management tasks such as collecting system inventory, applying operating system (OS) patches, automating the creation of Amazon Machine Images (AMIs), and configuring operating systems (OSs) and applications at scale. Systems Manager lets you remotely and securely manage the configuration of your managed instances. A managed instance is any Amazon EC2 instance or on-premises machine in your hybrid environment that has been configured for Systems Manager."

---

### Why use it?

* improves security
* automation reduces mistakes
* decreases cost (no bastion host instance)
* access controlled by IAM
* fewer things are public (such as RDS access)

---

### Why use it?

* scripts ("documents") can be controlled and versioned
* can manage EC2 or local instances
* can automate many typical functions
* Linux and Windows supported
* ops and developers can use it (console or cli)

---

### How does it work?

* SSM agent running on host
* agent is pre-loaded on AMZN Linux instances
* policies/permissions for the instance must allow it
* instance must appear as a "Managed Instance"
* multiple hosts can be acted on asynchronously/simultaneously

---

### What is in it?

* Run Command
* State Manager
* Inventory Manager
* Automation
* Parameter Store
* Maintenance Windows

---

### Things that are different

* (probably) should have aggregated logging/CloudWatch because no direct access
* cannot directly ssh
* must be comfortable with shell/cli access or use stored documents
* asynchronous, results and potential output available after hosts complete execution

---

## Parameter Store

---

"AWS Systems Manager Parameter Store provides secure, hierarchical storage for configuration data management and secrets management. You can store data such as passwords, database strings, and license codes as parameter values. You can store values as plain text or encrypted data. You can then reference values by using the unique name that you specified when you created the parameter. Highly scalable, available, and durable, Parameter Store is backed by the AWS Cloud. Parameter Store is offered at no additional charge."

---

### What can you use it for?
* key value pairs (KVPs)
* global to the account
* IAM access controlled
* values can be encrypted

---
### Why use it?

* can be accessed from the aws cli, CloudFormation, others
* centralize the values of things
* reduce distribution/copies of things
* audited in CloudTrail, notifications (know when something changes)

---

### Examples - AWS CLI

```
aws ssm put-parameter --name /db/dev/password --value password1 \
    --type String --overwrite
aws ssm put-parameter --name /db/prod/password --value password2 \
    --type String --overwrite

aws ssm describe-parameters --filters "Key=Name,Values=/dev/db/password"
aws ssm describe-parameters --filters "Key=Name,Values=/dev"
```

---

### Examples - CloudFormation

```
"Parameters" : {
...
    "DBPassword": {
        "Type" : 'AWS::SSM::Parameter::Value<String>',
        "Default" : "/dev/db/password"
    }
...
}

```
---

### Demo - SSM Run Command

* ECS cluster
* execute on all instances
* execute on tagged instances

---

### Demo - Parameter Store

* cli set
* cli get
* supports hierarchy of keys (/db/password/dev, /db/password/prod)
* CloudFormation RDS password

---

### Links

* [github.com/dougtoppin/presentation-aws-ssm](https://github.com/dougtoppin/presentation-aws-ssm)
* [docs.aws.amazon.com/systems-manager/latest/APIReference/Welcome.html](https://docs.aws.amazon.com/systems-manager/latest/APIReference/Welcome.html)
* [docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-paramstore.html](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-paramstore.html)
* [github.com/awslabs/ecs-refarch-cloudformation](https://github.com/awslabs/ecs-refarch-cloudformation)
