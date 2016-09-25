---
layout: post
title: "Yith: Private npm registry"
date: 2016-09-26 13:00:00
categories: open source serverless private npm registry yith
abstract: "Handle private npm packages in the enterprise. No servers required!"
author: Jon Sharratt
hero_image: blog_wework_office.png
hero_image_alt: "Panorama of WeWork office, Old St."
---

The Craftship team have been working on a new Open Source project
to help organizations that require keep intellectual property but still
wish to share modules across teams and use npm modules from the offical registry.

Having worked in many large organizations they use GitHub Enterprise
which helps give them the ability to have a standard joiners and leavers policy
across thousands of employees of which all third party systems need to have single
sign on (normally via LDAP) so that they can ensure access control is managed in one place.

One thing to note is that GitHub have recently announced at their GitHub Universe
conference they are rolling out SSO for SAML based authentication amongst a whole heap of
exciting [new features](https://github.com/blog/2256-a-whole-new-github-universe-announcing-new-tools-forums-and-features).
We are hoping this means that in the enterprise organizations  will look to use hosted GitHub rather than having the overhead of managing it internally.

![Serverless astract imge](/images/blog_yith_serverless.png)

### What is yith?
Yith is a private npm registry that uses the [Serverless framework](https://serverless.com/) to
reduce cost and overhead of any instances required in your cloud
provider (currently AWS) to host a private npm registry.

Every operation that is required for the registry is a Lambda function,
a bite size function that runs only on demand when required.  The up shot of
doing this is that in the case of Amazon you are only charged for the
time in which the function runs.  This makes hosting a private npm
registry using yith incredibly cost effective.

Each function when an `npm` command is executed makes a request to and
endpoint via Amazon AWS API Gateway which then invokes the function to
run and produce the relevant response required for the `npm` CLI.

We basically used [Charles](https://www.charlesproxy.com/) to sniff the `https`
requests being made by the npm CLI and replicated the endpoints (which are ultimately
is CouchDB) :D

![yith cloud diagram](/images/blog_yith_diagram.png)

### How does my team use it ?
Once deployed using the serverless framework each team member just sets
the relevant npm registry url (`npm set registry`) to the deployment url
specified.  It is built to be compatiable with the npm CLI you all know
and love!

### Authentication
For authentication yith overrides using `npm login` to authenticate and instead
uses github.com or your github enterprise instance to authenticate and
allow publishing of packages.  All you need is to setup a GitHub
developer application and update the relevant config file with the
client id and secret.

To support two factor auth we had to bei a bit cheeky and require your username
to end with a full stop then the one time authentication password, for
example `username.123456`.

### Publishing packages
Once logged in via GitHub publishing packages is the same as you have
done before using `npm publish`, simple!

### Installing packages
To install a package when you use `npm install` yith will first check
the S3 bucket to see if it exsists in your private registry.  If it does
not exist it will then go off to the real npm registry and download it
from there.

### Summary
Hopefully this gives you a nice introduction to what yith is and a high
level overview of how it works.  We have plenty of features we want to
add in the upcoming months and hope to get some contributions from the
wider community.

One thing to note is that we have found Serverless RC1 (expected as it is
very new!) to have a few minor issues.  You will notice until we get
some of our pull requests merged into Serverless we are running the yith
on our own fork / branch for now.

[Yith GitHub repository](https://github.com/craftship/yith)
