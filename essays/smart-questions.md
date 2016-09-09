---
layout: essay
type: essay
title: How Asking Smart Questions Makes Better Software Engineers
date: 2016-09-08
labels:
  - Software Engineering
  - Critical Thinking
---

I recently read ["How to Ask Questions the Smart Way"](http://www.catb.org/esr/faqs/smart-questions.html) as part of my software engineering class, an essay that's now a classic in the open source and hacker community...so much that it warranted a "do not contact us" disclaimer punctuated with some florid insults for would-be inquirers. Despite all its hackery cred, I actually found myself thinking about how "smart questions" in the hacker world were really just smart questions, no matter the context--and I've seen first-hand the impact and importance of smart questions, even outside the software world.

Eric Raymond alludes to how a smart question leaves the respondent better for having answered it. In my experience, a sharp, insightful question has the potential to completely shift a team's view of a problem, revealing angles and approaches that couldn't have even been considered prior to uncovering that line of inquiry. However, smart questions do require some level of insight about the problem being asked about; superficial knowledge results in superficial questions, after all. Though smart questions are sometimes posed innocently, more often they are the result of deep familiarity with the problem. Often, even the process of formulating a truly good question will make you more effective at whatever you are asking about. 

Though Raymond's essay is fairly lengthy, his requests are summarized pretty easily:
- Don't ask people for solutions so extensive that you should be paying for the work
- Communicate clearly, use descriptive titles, and explain what outcome you are trying to achieve
- Show you've made a real effort to research, understand, and solve your own problem
- Have a narrow scope of where you need help, and evidence of why you think that's the case
- Value the time of others by working to balance conciseness against providing enough information to diagnose a problem
- Show your appreciation to the people that helped you, and try to give back to the community they came from

##How to Ask an Interesting Question

As an example of a good question, I looked for the most upvoted question on Stack Overflow in the last 30 days as of this post, and found someone asking about an [unusual parseInt() behavior in JavaScript](http://stackoverflow.com/questions/39147108/why-is-it-that-parseint8-3-nan-and-parseint16-3-1).

The title of the post is descriptive and succinct: *Why is it that parseInt(8,3) == NaN and parseInt(16,3) == 1?* The post itself is also succinct, showing the behaviors of the function under various conditions in an easily-digestible way, and explaining why the behavior is unexpected. The strange nature of this error led to substantial upvotes, as it seemed to be a corner case that many people couldn't understand.

The expert response was that parseInt (and JavaScript in general) just takes in the argument up until the last valid character in an effort to provide resilience against errors. As the first condition only had one character, it returned NaN, but the second condition was not valid, so JavaScript resorted to using the first character, which was still valid.

The answer here is an example of how a good question elicits a good answer that ended up having to get down to the very structure of the language itself in order to explain what was going on. These are the kinds of problems software engineers should be solving.

##How to Ask a Bad Question

In the quest for a bad question, I searched for the most downvoted posts on Stack Overflow. A question deep into the negative is especially notable, because casting downvotes in Stack Overflow actually costs reputation points to do (and not everyone can do it), so it's not an action taken lightly. What I found was a question about [how to send 100,000 emails weekly](http://stackoverflow.com/questions/3905734/how-to-send-100-000-emails-weekly).

The question exhibits all the hallmarks of Raymond's pet peeves, from asking a question about a solved problem with no evidence of research, to requesting a solution that requires extensive involvement and would otherwise be paid for a post that is of blatantly commercial intent. In fact, the question was so bad, one of the Stack Overflow moderators locked the thread and left this comment about it:

> This question exists because it has historical significance, but **it is not considered a good, on-topic question for this site**, so please do not use it as evidence that you can ask similar questions here. 

In other words, this question is *historically* bad. It should be noted, however, that someone thought this question was enough for a rather [long and detailed response](http://stackoverflow.com/a/3905805/4957881) about the intricacies of mass mailing and ensuring delivery, so it seems that even asking historically bad questions will get you answers...it just probably won't make you a deeper thinker.

##Professional Communication Makes You a Better Developer

In conclusion, the rules of good communicaiton and etiquette that you've encountered all your life still apply to the hacker world. In using them, you will not only become more likely to get answers to your questions, you will also gain a deeper understanding of your problem topic and become more insightful as a result, all of which make you a better engineer and professional.
