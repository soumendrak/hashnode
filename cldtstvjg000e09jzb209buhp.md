---
title: "A Guide to the Amazon Recruiting Process: What to Expect and How to Get Ready"
datePublished: Tue Feb 07 2023 05:25:58 GMT+0000 (Coordinated Universal Time)
cuid: cldtstvjg000e09jzb209buhp
slug: a-guide-to-the-amazon-recruiting-process-what-to-expect-and-how-to-get-ready
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1671973927760/029f8dc4-67a5-4fe5-82ce-f65016523404.png
tags: interview, amazon, python, interview-questions, faang

---

## TL;DR

A Guide to the Amazon Recruiting Process: What to Expect and How to Get Ready - This article outlines the Amazon recruiting process, what to expect, and how to prepare. It includes a breakdown of the interview rounds, the topics discussed, and the outcome. It also provides tips on preparing for the Amazon Leadership Principle rounds and a conclusion.

## How I landed up with an interview call?

One of my friends on the org referred me for this post. As always, I was not prepared to qualify for a FAANG interview when the recruiter called me.

She should be, and the people are mad about FAANG companies even after they kicked out thousands of employees like no one.

## Interview details

* Job Position: System Development Engineer (L5)
    
* Interview Process: There will be 1 round; if you qualify that there will be 3-4 more rounds, then the results will be announced by HR. It was not series-like crossing level after level, unlike my previous interviews.
    
* Years of experience at the time of applying: 9
    
* Total number of rounds: 7
    
* Outcome: Offered 🙂
    

## First round (Litmus test)

*June 2021,* Telephonic Chime (like Skype) call

My first round of discussion was with a system development engineer who has worked for amazon for over two years. She has asked me questions on the followings:

* We discussed my experiences in UI tools, Python, Network Automation script writing, Auditing, Infrastructure automation, and AWS Cloud.
    
* Context Manager and in which case will you be using a context manager and in which case a decorator; excellent question.
    
* Garbage collector behind the scenes.
    

Two short coding problems

* Write a timer decorator and write a unit test case for that.
    
* Write a class
    
    * that takes a first name, last name, and age as parameters
        
    * Auto-populate the creation date
        
    * and return the name and age of each object with the proper *\_\_str*\*\*\*\_\_\*\*\* method.
        

I cleared this round.

## Second round (ALP)

*After a week of the first round.*

In this round, we did behavioral discussions based on [Amazon leadership principles](https://amazon.jobs/content/en/our-workplace/leadership-principles)(ALP) and something along the line of:

* AWS components: ECS, Lambda, DynamoDB, Quickshift
    
* API gateway
    
* Agile methodologies
    

## Third round (ALP)

*One day after the second round.*

The interviewer joined the call 10 minutes late. In this round, we have discussed on few Amazon leadership principles:

* Tell me when you did XYZ leadership principle in your past and what went well, and what could have been done better.
    

Preparing stories for ALP rounds is essential. To optimize your account, including all relevant details of what you have done in the past. If needed, add a little extra information to shape the story better. As an interviewer, if the candidate is not strong, they may be caught bluffing if you probe the WHYs of the story.

## Fourth round (API Designing)

*One day after the third round.*

We discussed my skills on the following topics:

* Error Debugging
    
* ECS, Cloudwatch, Application maintenance
    
* Monolithic and distributed server; why and hows
    
* Designing an API that involved network devices, laptops, scanners, and IoTs.
    

It went well. We got our thought process aligned on many points.

## Fifth round (System Designing)

*One week after the fourth round.*

The interviewer was severe, and the first thing that came out of his mouth was a question like a bullet. We discussed the followings:

* Design a system with N hosts/servers at M number of sites/locations.
    
    You have to schedule a job on the host to pull camera footage from the server and save it locally for human export.
    
    The server count and the location count can be received from another service.
    
    You cannot schedule multiple jobs per host at any given time.
    
    The camera data currently lives locally on each server for the cameras it handles, and we have frequent adds and deletes.
    
* We discussed the above problem throughout:
    
    * Data Flow
        
    * Map of camera, host, and location
        
    * Website to server API payload
        
    * Deletion or Addition of Camera
        
    * Backend
        
    * DB
        
    * Queue
        
    * User roles in the system
        

His general advice:

* Do not settle and always aim for the sky
    
* Be open to feedback and **act upon them**
    

The discussion was ok. I did not excel with flares. On the other hand, it was not pathetic either.

## Sixth round (ALP)

*This round was rescheduled for three times, and finally, on the fourth, the force acted in my favor two weeks after the fifth round.*

ALP's theme was *Invent and Simplify.* Which has probable questions like this:

* Tell me about a time when you invented something.
    
* What improvements have you made at your current company?
    
* Tell me about a time when you gave a simple solution to a complex problem.
    
* Tell me about a time you had to think outside the box (think creatively) to close a sale or sell your product.
    
* What is the most innovative project you've worked on?
    

### Coding Question

After these questions, I got a follow-up problem to solve.

Q. Given a 100MB log file that looks like this:

charles=3918  
alice=0  
bob=100  
charles=3918  
django=77  
alice=0  
erik=0  
charles=4231

Write a program that removes the duplicate lines and sorts the pairs by value.  
\* value is the integer assigned; duplicate lines are defined by the full-text line, not the key.

I have written one with all logs, Exception handling, and Edge case handling. This interviewer was more empathetic and logical than the rest of the interviewees so far.

## Seventh round (HR)

* The HR explained RSU, ESOP, Shares, and Prorated concepts to me.
    
* I negotiated and requested to give me some time to decide.
    

## The Offer 🙂

* Finally, I got an offer from a FAANG company. (Do we care after the 2022 Layoffs?)
    

## Lessons Learnt

* Prepare the use cases well for the Leadership principles
    

## Conclusion

We have discussed my first interview experience, where I got an offer on this platform. We have discussed the different rounds and processes in Amazon. You can ask me any specific questions over [LinkedIn](https://www.linkedin.com/in/soumendrak/) or [Twitter](https://twitter.com/soumendrak_).