---
title: "My GSoC Win"
date: 2025-09-16
draft: false
summary: "A story-like recap of my GSoC journey, encouraging anyone to take on the experience (or retry it), without rehashing the application process details that are already covered elsewhere. I've gathered every source and tool that helped me, starting from the very basics of what GSoC is, focusing on the things I didn't find in other resources."
---
### A Win-Win Situation

I was a second-year CS student who spent most of my time on problem-solving, CS courses, and console projects. One day, a friend told me about GSoC and shared this golden article: [Why Google Summer of Code is a golden Opportunity](https://xuser5000.hashnode.dev/why-google-summer-of-code-is-a-golden-opportunity). A line in that article caught my eye: **`Win Win situation`**.

I asked myself, "Am I ready for this step?" The answer was **a `Win Win situation`**. As a beginner, I wanted to level up in topics I already knew, learn new subjects, improve my Git and GitHub skills, and discover what open source really is. I realized that even if I didn’t get accepted, I would still achieve all of that. And if I _did_ get accepted? The thought was incredible.

##### The Leap After Acceptance

Being accepted feels like a leap into the future. For about three months in the summer, you work on a real-world project with a mentor guiding you. The experience of seeing how a professional team and an organization’s workflow operate will push your software career to a new level. And when you **learn** about the stipend, your eyes will light up.
##### In Short, What Is GSoC
_**for more details, check the sources**_

Google Summer of Code is a program run by Google that helps bring new developers into the world of open-source software.

Think of it as a paid, remote internship for students. Open-source organizations, which are projects built by volunteers and freely available to everyone, propose a list of programming tasks they need help with. Students then apply for a specific task by writing a project proposal. A proposal is a document that explains how you will implement the project.

If a student is selected, they spend their summer (about three months) working on that project under the guidance of mentors from the organization. The mentors provide help and feedback, making it a great learning experience. In return for successfully completing their project, the student receives a stipend from Google. It's a way for students to gain real-world experience, get paid, and contribute to software that people all over the world use.

So, you find an organization and a project from the ones that want to participate in GSoC, and then you submit a proposal explaining how you will implement it.

### The Starting Point

At the beginning of my journey, I opened the [GSoC page](https://summerofcode.withgoogle.com/programs/2025/organizations) to explore projects, looking for one whose tools I had used or that simply caught my interest. But with my beginner's level of experience, a question haunted me: "With my current skills, am I actually capable of this?"

> "You are able to do **anything** if you want."

This is a quote I heard from someone who was accepted into a major GSoC organization. He said he didn't understand anything at first, but he did it anyway. Motivated by this, I kept going through moments of both excitement and disappointment, exploring organizations and searching for my first pull request.

### Your Unexpected Teacher

Spending hours searching for the right organization or a beginner-friendly issue can feel boring and disappointing. It's easy to feel like you're wasting time while others are learning new technologies. But you don't see your own progress.

During this time, many of my skills improved almost without me realizing it, simply through **persistent searching**. I developed the ability to read open-source code, revisited concepts I had studied before, and understood them more deeply by seeing how they are applied in real-world projects. I also gained a stronger grasp of Git and GitHub workflows on a deeper level. All of this naturally **enhanced** my programming skills. The key is to just keep going.

### Your Friends

Of course, a real friend sharing this journey with you is crucial. Even if you are at the same level, a strong partnership makes all the difference. With a shared goal and high motivation, you are unlikely to feel down at the same time, so you can pull each other up. Understanding something motivates the other, and a merged PR becomes a shared victory.

And AI tools can help you fly. They can help you understand complex code, search for information, and find what fits you. But be careful, as they can sometimes make you feel lost. Tools like [DeepWiki](https://deepwiki.com/), which lets you "talk" to GitHub repositories, and [Gitingest](https://gitingest.com/), which turns a repository into text for LLMs, can be very useful.

#### [ACU](https://discord.gg/RPrZatCy) (Active Course University)

ACU is a programming-focused Discord channel that became like a second home for me. It's not only for GSoC but for your entire software development journey. Here, you find answers to any question from people who have been there before and genuinely want to help, asking for nothing in return. ACU is an amazing place that truly makes a difference.

### How to Choose Your Organization

_**What no one will tell you about how to search**_

At the beginning, the real obstacle for many is not technical skill but research and exploration. No one can tell you exactly what to search for because your journey is unique. Most GSoC contributors find an organization through their own focused exploration.

The key is knowing _how_ to search effectively. Learn to use tools like:
- [gsocorganizations.dev](https://www.gsocorganizations.dev/).
- **GitHub** with its filters (by language, topic, "good-first-issue").

Your search should be guided by your personal goals. Understand the trade-offs of each approach, as your strategy will define your experience.

**1. The Technology-First Approach**

> "I'll only contribute to orgs using technologies I already know."
- **Pro:** You'll be a strong contributor from day one and understand the code faster.
- **Con:** You narrow your options and might miss projects with ideas you love because of a tech mismatch.
    
**2. The Project-First Approach**
> "I'll search for a project regardless of technology to increase options."
- **Pro:** You open yourself up to many more organizations and inspiring ideas.
- **Con:** The load of learning a new technology _while_ contributing is significant and challenging.

**3. The Prestige-First Approach**
> "I want to contribute to a famous organization like Chromium or Fedora."
- **Pro:** A big name looks great on your resume and offers a high-impact experience.
- **Con:** You will face intense competition from many other applicants.

**4. The GSoC-First Approach**
> "My primary goal is to get into GSoC, regardless of the organization."
- **Pro:** You cast the widest net and increase your chances of acceptance.
- **Con:** The organization's name might carry less weight on your CV later.

**5. The Career-First Approach**
> "I'm looking for organizations known to hire contributors after GSoC."
- **Note:** Your stipend comes from Google, not the organization. You are searching for orgs that offer strong career opportunities post-GSoC.

There are more paths than these. **Set a clear goal for what you want from GSoC.** Each part of your goal will shape your search, and only you can weigh the trade-offs that fit your situation.

### The Power of Documentation & Your First PR

_**Don't ask before you read the documentation**_

Your most valuable mentor for any organization is its **documentation**. The documentation will tell you everything: if the org is a good fit, how to get started, and where to find answers.

When you're new to an open-source project, even "beginner-friendly" issues can seem confusing. You might not know how to solve the issue or even how to submit a Pull Request (PR).

**This is where the power of documentation shines.** Before you ask a question in the chat, search the documentation. The answer is almost always there. This shows the community you are resourceful and respectful of their time.

### Announcing Your Arrival

_**Everyone who keeps going eventually reaches this point**_

A merged PR gives a great feeling of achievement: “Finally, I’m here!” After that, read the org’s GSoC project ideas and pick one to propose. 

From this moment on, your goal is to show the organization that you are a committed, valuable member. How?

- **Be Active:** Join their communication channels (Slack, Discord, etc.). Answer other newcomers' questions (you'll know the answers from your time with the docs!).
- **Be Present:** Attend community meetings and introduce yourself to potential mentors.
- **Be Consistent:** Continue contributing with more PRs and issue reports.

Act like you belong, and soon, everyone else will see it too. When the mentors review proposals, they will already know your name and trust your work.

### Helpful Resources

**Essential:**

- Start with the article that inspired me, [Why Google Summer of Code is a golden Opportunity](https://xuser5000.hashnode.dev/why-google-summer-of-code-is-a-golden-opportunity).
- For a step-by-step walkthrough of the entire process, this video [Let's apply to Google Summer of Code](https://www.youtube.com/watch?app=desktop&v=WKFAwImEo1c) is incredibly helpful.


**Optional Guides:**
-  [Git and GitHub | شخبط وانت متطمن](https://www.youtube.com/watch?v=Q6G-J54vgKc)
- [Git & GitHub Tutorial for Beginners](https://youtube.com/playlist?list=PL4cUxeGkcC9goXbgTDQ0n_4TBzOO0ocPR&si=lHd79iY3Op0Op1fV)
- [Contributing to an Open Source Project on GitHub](https://www.pluralsight.com/courses/contributing-open-source-project-github) ( use pluralsight's free trial).
- [Open Source and GSoC 2024 Informational Session](https://www.youtube.com/watch?v=Pw9Je4iMU0s)
- [Google Summer of Code | A COMPLETE GUIDE](https://www.youtube.com/watch?v=BcSp27-HcZk&t=982s)

