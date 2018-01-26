# AWS SSM


SSM

---
## Agenda

* SSM
* Parameter Store

---
What is it?

"AWS Systems Manager is a collection of capabilities that helps you automate management tasks such as collecting system inventory, applying operating system (OS) patches, automating the creation of Amazon Machine Images (AMIs), and configuring operating systems (OSs) and applications at scale. Systems Manager lets you remotely and securely manage the configuration of your managed instances. A managed instance is any Amazon EC2 instance or on-premises machine in your hybrid environment that has been configured for Systems Manager."

---
Why use it?

* improves security
* decreases cost
* controls access by IAM
* scripts can be controlled
* asynchronous

---

Things that are different
* (probably) must have aggregated logging/cloudwatch because no direct access
* cannot ssh
* must be comfortable with shell/cli access

---

Parameter Store
* KVPs
* global to the account
* IAM access controlled

