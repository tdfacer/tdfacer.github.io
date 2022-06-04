---
layout: post
title:  "AWS IAM"
date:   2022-06-04 13:07:21 -0600
categories: tech aws iam
tags: tech aws iam
author: Trevor Facer
---

## Terms

* `Principal` - The person or application making the request
* `Identity` - User, group, or role
* `Policy` - An object in AWS that, when associated with an identity or resource, defines their permissions 
* `Resource` - An object in AWS; an instance of a "thing" created in an AWS service
* `Role` - A tool for giving temporary access to AWS resources in your AWS account


## Resource vs. Identity Based Policies

[official docs](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_identity-vs-resource.html)

A policy is an object in AWS that, when associated with an identity or resource, defines their permissions.

### Identity

* Attached to an _IAM user, group or role_
* Specify what that identity can do
* Allow you to specify what actions can be done by a given user
  * Can have _resource-level permissions_, which say what a specified identity can do on a specific resource
* e.g. allow a user to perform EC2 `RunInstances` action

### Resource

* Attached to a _resource_
* Allow you to specify who can access a resource
* e.g. allow public access to an S3 bucket

### Cross-Account

* For an identity to perform actions on a resource in a separate account, the following conditions must be met:
  a. Identity has an _identity-based policy in `Account A`_ that grants permissions to make request to `Account B`
  b. Resource in `Account B` must have a `resource-based` policy allowing requestor from `Account A` to access the resource
