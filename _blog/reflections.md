---
layout: default
title: Reflections on a coding bootcamp
description: "I recently completed a 9 week Full Stack Development bootcamp in Berlin and I have some thoughts on the whole process and hopefully I can help some people decide whether or not it is for them."
order: 0
---

I recently completed a 9 week Full Stack Development bootcamp in Berlin and I have some thoughts on the whole process and hopefully I can help some people decide whether or not it is for them. I self-studied coding, before the bootcamp, in my spare time. Coding was and continues to be one of my hobbies. It's satisfying, results can come quick especially with languages like Python and Ruby. I decided to elevate my hobby into a career after a few boring career ventures into Project Management and Legal Consultancy. My coding level before the bootcamp was not strong in any sense of the word. I was comfortable with datatypes in Python, I could iterate over an array and I was happy enough to copy code. I applied to this bootcamp after a friend of a friend had completed it.

For me attending a bootcamp was a big gamble. I knew I had the capacity to become a strong coder if I could dedicate a year or more to teaching myself however the prospect of being accelerated by a school convinced me to leave my Project Management position and try and enter the Tech World.

Applying
--------

The entry bar for coding camps is simply time and money. I applied to a number of bootcamps in Berlin before settling on one and each of the bootcamps had similar entry requirements. Generally consisting of 50 hours of work on one of the various online studying platforms (freecodecamp, codecademy, etc.) with a focus on the language of choice. My bootcamp focused on Ruby which is an incredibly simple language to use and then some closing thoughts on HTML, CSS and Javascript. Aside from being able to complete the pre-course work there is obviously the cost. This bootcamp in Berlin cost ~€6000. Luckily, for me, the German Government was able to fund my tuition however a large portion of the people on the bootcamp were self-funded and, surprisingly to me, there was very little difference in the attitude between the two groups of people. It was obvious, even from the start, that some people were attending the bootcamp to transition careers and others were there simply for "something to do" during the COVID situation where numerous companies in Berlin had let their staff go on Kurzarbeit.

The first week
--------------

The atmosphere at the coding bootcamp was very interesting. A large mix of ages and genders (but very ethnically homogeneous) getting together to learn. It had been over 5 years since I had left any form of educational establishment whereas some people were joining directly from university and others had full careers that they had been able to take a leave of absence from to code. The first day, in which we were setting up our laptops (to UNIX systems) was a foreshadow of some things to come. We were shown basic git commands that the students would repeat with little understanding if they had not seen them before. Problems often arose with git among the students, most of which had to be solved by teachers or those with experience in version management. From the second day onward we used Ruby. In the short-term Ruby seemed like the most sensible "native" language for new students. I had used Python prior to the bootcamp and I would rank Python as slightly more complex than Ruby in its syntax. For new coders Ruby is, I think, a good gateway into coding. However when more complicated syntax was introduced with JavaScript some of the students struggled as they had been used to the simplicity of Ruby. Each day during the first 7 weeks of the bootcamp we were given between 2 and 6 challenges to solve. If you have used Hackerrank or Codewars then you are familiar with the style of the challenges: you are told to create, more times than not, a function/method that takes an input and then outputs something as a result.

During our time completing these challenges we had access to the Teaching Assistants, contactable by raising a ticket, who would assist in the problem. The code was exponential in the fact that the previous days code would build the foundations of the next's. The challenge system was a very good way of building upon the knowledge we were given in our 2 hour morning lecture. The morning lecture would introduce the concepts of any given day (for example the first day would be a focus on strings, the second arrays) before letting us loose on the challenges. As we had completed the prep work prior to the bootcamp the first two weeks of the bootcamp felt, to me, slightly redundant. We were repeating code that we had studied not too long ago. In this regard I would not consider bootcamps to be any better than Hackerrank or FreeCodeCamp where you could simply read a tutorial and then continue coding on your own. Where my bootcamp, and I presume all coding bootcamps, excel is the environment that you are in.

Coding by committee
-------------------

Each morning the inbuilt system would assign you a buddy. Your role with your buddy that day would be to discuss the code, help troubleshoot each other's problems and to generally build up a friendly environment within the bootcamp which would become crucial in the later weeks. It was obvious from the first couple of weeks who the stand-out coders were in our batch. More often than not these coders were people who had prior experience coding. The buddy system, for these more experienced people, was a hindrance in terms of the actual coding but in terms of the social skills it proved invaluable. I know, personally, I could have completed the challenges each day in a fraction of the time if I was left on my own however, having now spoken to recruiters and engineers alike, it is equally as important to have strong teaching skills if you want to enter the tech world. By having to explain how or why code works helped my own understanding sometimes but more importantly it let me learn how to teach. The times that this group-think coding really had an impact was a lot more casual. Sitting with friends and complaining about the challenges, discussing workarounds to get the output to be correct or simply deleting the test spec file was where we built out network and where the real learning happened. Showing code to my contemporaries and having them laugh at my incorrect variable names or debugging together helped me learn how write readable code and how to write shorter code. This is not something you can teach in a lecture.

Copying and pasting
-------------------

Copying and pasting on day one:

      
```
Open a terminal and type this, replacing the email with yours (the same one you used to create your GitHub account). 
It will prompt for information. 
Just press enter until it asks for a passphrase.  
mkdir -p ~/.ssh && ssh-keygen -t ed25519 -o -a 100 -f ~/.ssh/id_ed25519 -C "TYPE_YOUR_EMAIL@HERE.com"
```

Copying and pasting on the final day:

      
```
Setup  
To setup a favicon, you can use Rails' favicon_link_tag helper.
Best practice:      
    Resize your logo image in 32x32
    Upload it in a favicon generator, this will generate a favicon.ico file
    Add it to your app/assets/images folder
    Place your favicon_link_tag in your layout's :  <%= favicon_link_tag %>
```

One of my main criticism with the bootcamp format, and maybe this is actually a criticism of coding in general, is that we learned just enough to code. From the first day we were almost blindly pasting things into the console without much real understanding of what we were doing. Even at the last day as we were deploying our final product that we were just copying and pasting things into the terminal to satisfy some tests. Obviously this is how you have to do it in a bootcamp environment because I can't imagine explaining how a compiler works to a group of students who only learned how an if/else statements works less than 8 weeks prior. My main criticism, however, was the lack of education on how to continue learning. For 9 weeks the students at the bootcamp followed a very structured set of lectures, challenges and tests however now that I am two weeks outside the bootcamp system it has been an interesting transition into learning how to make my own projects, learn new concepts and overall maintain the pace that the bootcamp had set up. I understand that this is how the majority of education goes, for example when I was studying my bachelors I wasn't exactly prepared to self study in the legal world however I think with tech there is some exception. The tech world is largely self-taught and reading things like documentation is a legitimate skill that you need to develop. The bootcamp felt like its end goal was to get students through the bootcamp and not necessarily produce self-reliant coders.

The stack
---------

I realise that I should maybe give some insight into what we were actually taught as this will allow me to accelerate this diary entry into the interesting final weeks of the bootcamp. The bootcamp's modules are as follows:

*   Ruby (2 and a half weeks ending with basic OOP)
*   Databases (1 week starting with SQL before ending on PostgreSQL)
*   Front end (1 and a half weeks covering HTML, JS and CSS)
*   Rails (2 weeks of building webapps ranging from simple websites to an AIRBNB clone)
*   Project weeks (2 weeks of building our own project)

Before we move onto the project week it is worth discussing how each of these modules went as I believe the pacing and order could be slightly improved. The pacing that the Ruby module was taught I largely can't argue with. I personally thought that the challenges were a bit simple however that is more of a reflection on myself than it is the course. Databases were the area I, personally, struggled with the most. This is where I got the most insight into how the TAs operate and the insight that they give. The teaching staff at the bootcamp, including the TAs, are stellar. TAs are assigned each day based on their strengths and very rarely did I have a call with someone where I felt that they hadn't contributed somehow. would like to see Javascript be the first language that we are taught in the bootcamp. The beauty of Ruby relies on its simplicity and it's easy to read nature but this isn't fully appreciated until you touch on other languages. What surprised me about the order of teaching is we started off with the simpler language. I think that having a week of Javascript learning how to iterate over arrays and all the unusual complexities that Javascript presents would be a shock to the system that the tonic of Ruby would be welcome. I personally think for a topic as complicated and wide-reaching as Rails, or any framework for that matter, this bootcamp did a surprisingly good job at teaching. My criticism in this area, which I think might be a critique of the whole construct of bootcamps is the reliance on copying and pasting that I spoke about before.

Project week
------------

This is the real meat and potatoes of the bootcamp. Project week is the last 2 weeks of the bootcamp and is the first real insight into the developer life. There is no real guidelines to follow and you just have to produce something with the knowledge that you gain during the previous 7 weeks. It is a stressful, chaotic time where a group of four students, with one student acting as the lead developer have to work together. In the previous 7 weeks we were simply satisfying tests and then you are let loose. You are forced to learn how to work as a team, to use code that you hadn't ever seen before and I should really write another piece on this. Generally it was a fantastic experience.

Wrap up
-------

Was a coding a good experience? Yes, it was incredible. I grew as a coder, I grew as a person and I have come away from it with an insight into a world that I wouldn't otherwise have. Is it for everyone? I'm not so sure. I think the people who got the most out of the bootcamp are the ones who have a clear mindset about what they want to get out of it. Some people were hoping to change industry, others wanted to be able to project manage in a group of coders. I feel like those who got the least out of the experience were the people who just signed up to learn something.
