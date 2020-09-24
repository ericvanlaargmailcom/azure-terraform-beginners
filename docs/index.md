Terraform and Azure for Beginners

Get up and running with Terraform on Azure

My name is Eric van Laar and I'm a Microsoft Certified Trainer with Aino Cloud Solutions. I like building things. In my past life I was a Ops engineer, now I teach and help users get started with Infrastructure as Code.

Welcome to the beginner's guide to Terraform on Azure. We'll have you provisioning your first application on Azure with Terraform in less than 15 minutes. If you're new to Terraform or Azure, this webinar is for YOU. And if you're a Terraform veteran, hang around, perhaps you'll learn a few new tricks.

Learning a new skill can be scary and weird. Maybe you are not a programmer. Don't let that stop you. Terraform is not like learning C or Java. You do not need to be a software developer to take advantage of Terraform.

Our goal today is to equip you with some basic skills and get you started on your journey with infrastructure as code. Once you've got some basic Terraform skills this gets a lot easier. It's like learning any new language. The key is to get started with the basics and practice.

What is Microsoft Azure?
Microsoft Azure is a cloud computing platform that you can use to run your infrastructure and applications. 

What Can I Build in Azure?
.contents[
* Linux Virtual Machines
* Windows Virtual Machines
* Containers
* Networks
* Databases
* Functions as a Service
* Much, much more...
]
What can I build in Azure? Just about anything! The beauty of the cloud is that it allows organizations and companies to rent their infrastructure. Traditionally if you wanted to run an application you'd either need to build your own data center or lease some space from a data center provider. You could then buy a bunch of servers, install your operating system and application on them and configure your application for use. Most companies do not want to be in the business of running data centers.  And guess what - Microsoft is really good at this. They have a ton of experience and huge teams of people to maintain the hardware and network connectivity that you need, and you can simply rent your resources by the hour (or even by the minute).  It's pay-as-you go computing that you use just like a utility. Imagine I have three faucets, labeled compute, network, and storage. I can turn on as much as I need, run it for as long as I want, and then shut it off when I'm done using it. Those resources I was using are returned back to the pool of compute, network and storage.

What is Terraform?
-------------------------
* Infrastructure as Code
* Executable Documentation
* Human and machine readable
* Easy to learn
* Test, share, re-use, automate
* Works on all major cloud providers
]

Terraform is the DNA of your infrastructure.

Live Demo
=========================
Let's do a live demo! I'm going to walk you through the process of building a very simple application in Azure. First we'll go through the Azure Portal and see how you might deploy a virtual machine manually. Next we'll take a peek at an Azure Resource Manager template. Then we'll deploy our application using Terraform.

First we'll log onto the Azure portal. If you don't have an account yet you can sign up for free. Microsoft will give you $200 USD in Azure credits to use in your first 30 days. Or you can sign up for the Visual Studio Dev Essentials subscription and get $25 a month to use:

https://azure.microsoft.com/en-us/pricing/member-offers/credit-for-visual-studio-subscribers/

Once you've signed in you'll see your landing page in the Portal. One of the things I like about Azure is the ability to have custom dashboards that show different resources. This is my Terraform dashboard. 

Over here on the left side is the main navigation menu where I can view or build different types of cloud resources. Let's say I wanted to build a new virtual machine. I can click this plus symbol and walk through the little quickstart wizard to get a virtual machine stood up. Easy right? So you might be thinking to yourself at this point, why would I need Terraform when I already have this handy GUI here? Let's talk about complexity a bit. The Azure UI has actually hidden away most of the pieces that are required to stand up my VM. 

While using the GUI to stand up one or a handful of machines is useful, what if I need to create dozens or hundreds of machines?  Or build a complex application stack that contains multiple different platforms and components?  Going through the UI over and over, hoping I won't make any mistakes is not an ideal way to do this.  Manual processes quickly become burdensome the more complex my infrastructure needs are.

Ok, so what about ARM templates?  You might have heard of Azure Resource Manager.  These ARM templates are preconfigured settings that allow you to define your Azure infrastructure. ARM templates are defined on JSON, or Javascript Object Notation.  JSON is the defacto standard language of APIs. When computers need to talk to one another across the network they often use JSON formatted data. JSON is great for computers but not so friendly to humans. Let me show you what I mean by that. We're going to play a little game called "Fun with JSON". This also works with AWS Cloudformation and GCP Deployment manager, by the way.

Here's an example of an ARM template that I pulled from the Azure Quickstart repo. JSON has lots of commas and curly braces. These are all required so that the computers reading this code know how to reconstruct the data you want to use to build your infrastructure. 

I took this template and dropped it into a JSON testing tool, and then I removed a few random commas and curly braces. Everybody makes mistakes, and when you have ten thousand commas and curly braces to look after, it's inevitable you will forget one here and there, or add an extra character where it shouldn't be.

Now I've gone and messed this file up to the point where I don't know what to fix anymore to repair it.  I once had a nightmare, i was in this jungle and all the vines were shaped like curly braces, and there were thorns on the vines, those thorns were all commas.  The JSON jungle.  It wasn't fun.  Let me show you a side-by-side comparision of JSON vs Terraform

This is not to bash on ARM templates. They are super reliable once you get them configured correctly. JSON is just not that fun to build and edit.

Which brings us back to Terraform. Terraform is easy to learn, and easy to edit. It's also built right into your Azure account! Let's get started using Terraform on Azure CloudShell. If you have an Azure account feel free to follow along!

First I will click on the CloudShell icon here to open up a CloudShell prompt. Azure CloudShell is like having a portable workstation with a bunch of tools you can use to build and work with your Azure workloads. The Azure command line is built in, and Terraform and Git are also included. 

Once i've opened a command prompt, I can use the `git clone` command to pull some code off of GitHub and into my cloudshell environment.

`git clone https://github.com/ericvanlaargmailcom/azure-terraform-beginners`

This is a really simple terraform config to stand up a single VM with a web page on it. Now I can change into the repo that I just downloaded:

The next step is to configure a couple of variables.  For that I can use the handy build in text editor with the `code` command. You're also welcome to use vi, nano, or emacs which are all installed in your cloudshell.

Everyone should pick a different name for their application.  You can also choose a region close to your location if you like.  I'm going to go with westus.  

Once we have our variables saved we're going to run `terraform init`

Then we run `terraform plan`

And finally we'll run `terraform apply`

Now watch here in the portal, we can actually see our resources being built in real-time.  Terraform is quickly and efficiently standing up all of the resources configured in our terraform code.  While that builds let's walk through this Terraform code step by step and explain what's going on.

Hey, look our application is up and running!  Let's click on the link here in the outputs and see what we built!

When I'm done here, cleanup is really easy.  All I have to do is run `terraform destroy` and all of my resources will be wiped out!

