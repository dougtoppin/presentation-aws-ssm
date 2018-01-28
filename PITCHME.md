# AWS SSM


SSM

---
## Agenda

* SSM
* Parameter Store

---
What is SSM?

"AWS Systems Manager is a collection of capabilities that helps you automate management tasks such as collecting system inventory, applying operating system (OS) patches, automating the creation of Amazon Machine Images (AMIs), and configuring operating systems (OSs) and applications at scale. Systems Manager lets you remotely and securely manage the configuration of your managed instances. A managed instance is any Amazon EC2 instance or on-premises machine in your hybrid environment that has been configured for Systems Manager."

---
Why use it?

* improves security
* decreases cost (no bastion host instance)
* controls access by IAM
* scripts ("documents") can be controlled


---

Things that are different
* (probably) must have aggregated logging/CloudWatch because no direct access
* cannot directly ssh
* must be comfortable with shell/cli access or use stored documents
* asynchronous execution, results and potential available later

---

Parameter Store

---
What is the SSM Parameter Store

"AWS Systems Manager Parameter Store provides secure, hierarchical storage for configuration data management and secrets management. You can store data such as passwords, database strings, and license codes as parameter values. You can store values as plain text or encrypted data. You can then reference values by using the unique name that you specified when you created the parameter. Highly scalable, available, and durable, Parameter Store is backed by the AWS Cloud. Parameter Store is offered at no additional charge."

---

What can you use it for?
* KVPs
* global to the account
* IAM access controlled
* values can be encrypted

---
Why use it?

* can be accessed from the cli, CloudFormation
* reduce distribution/copies of things
* audited in CloudTrail (know when something changes)

---

Demo - SSM

* ECS cluster
* execute on all
* execute on tagged instances

---

Demo - Parameter Store

* cli set
* cli get
* hierarchy of keys
* CloudFormation RDS password

---

Links

* [https://docs.aws.amazon.com/systems-manager/latest/APIReference/Welcome.html](https://docs.aws.amazon.com/systems-manager/latest/APIReference/Welcome.html)
* [https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-paramstore.html](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-paramstore.html)
