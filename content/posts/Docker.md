---
title: "Containerizing your applications with Docker."
date: 2023-07-08T22:24:26+05:30
---

Hello guys.

 You probably would have heard about docker and containerization before. Just to give you a brief, Docker is a container runtime. What does that mean? What is a container? Why do I even containerize my application to start with? Let's address these problems one at a time.

 **What are containers?**
 
 Containers and containerization is a concept that allows us to isolate some kernel processes. In other words, it acts like a virtual machine, except virtual machines provides isolation on hardware level whereas Docker works on kernel level. It helps you run multiple isolated environments without taking much of system's resources.
 
 But what problems does it solve? Suppose a scenario in which you and your friends want to work on a project. But there's a major issue, everyone works on their own systems and have different operating system. So now changes made by one of them doesn't work on another. One way to solve this issue could be to install the same OS on everyone's pc. But that, for obvious reasons might not be the most efficient solution, it might not even be sufficient (there might be other dependencies that your application rely on which might not be present on everyone's system). Comes Docker. Docker provides a virtual environment (a container), which is same for everyone and works exactly same on every system. It deprecates the use of "works on my machine" as an excuse to enjoy your weekend. 

So be it a simple html webpage, or a complex web app with interrelated frontend and backend, Docker (along with some other tools) can help containerize your applications so that workflow remain consistent in a production grade environment. It's a tool worth adding in your tech stack.

**But wait there's more**

Containerized applications can be deployed and managed by tools such as docker-swarm, kubernetes etc. Using docker along with deployment tools can help you create a smooth CI/CD(Continuous Integration, Continuous Delivery) pipeline which can help automate lots of processes and build tests.   

--- 

For further in-depth reading and to get started with Docker, you can refer to this docs -> https://devopswithdocker.com/