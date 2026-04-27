---
title: "Basic DevOps Project"
author: "Fong"
date: 2026-04-25
---

# This is a place where Fong starts his DevOps journey
### Part 1: Setup Gitlocal - Github:
- This is an easy part so nothing to say here.
### Part 2: Setup Jenkins - Docker:
- This is a "not so easy part", I have a hard time fixing a lot of errors here.

#### Build a Jenkins image in Docker on my mac:

	docker run -d \
  	-u 0 \
  	-p 8080:8080 -p 50000:50000 \
  	-v jenkins_home:/var/jenkins_home \
  	-v /var/run/docker.sock:/var/run/docker.sock \
  	--name jenkins-server \
  	jenkins/jenkins:lts

- Some of the bugs i must give credits to Gemini for helping me through the tough time.
	
### Part 3: Use Ngrok to make an auto pipeline:
- Set up a Webhook using Ngrok. 
- An easy way to explain this is whenever i fixxed and push my index file Jenkins will automatically build the Web. 
