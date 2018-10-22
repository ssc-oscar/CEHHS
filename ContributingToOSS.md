# Guide (contributed by Xin Tan tanxin16@pku.edu.cn)

## How to Contribute to the Open Source Community

As online activities become de-facto resume for oftware developers and importance of open source projects becomes critical for *ALL* commercial, governmental, 
and non-governmental organizations, it is essential to understand and practice open source contributions.

This guide provides various approaches and suggestions on how to ensure that the actual contribution will suceed and, that you have 
are good experience while doing it.

A. How to choose an appropriate open source project to contribute?

1) Start by thinking about the projects you have already used, or want to use. 
The projects you’ll actively contribute to are the ones you find yourself coming back to.

2) Choose the project you are very interested in. 

For example, if you are interested in search engine and want to know how it works. First of all, you should study technical literature 
to learn the basic technical points. After that, you can choose Lucene, Sphinx to learn through practice.

3) Choose the project you are familiar with. 

If you are familiar with the programing language and the technology that the project uses, it will be much easier for you to 
contribute. 

4) Choose the project that can be run stand-alone. 

There are many kinds of open source projects. Although many of them represent stand-alone software, most projects, e.g. the 
plugins of other projects, libraries, that would require you first to understand the underlying frameworks. 
Some of the projects may require very complex installation 
and configure in order to test the software. You may want to avoid them unless the time investmet would be worth-while.

5) Choose an active project. 

The activeness of the project usually contains two parts. The frequency of the commits, and the enthusiasm of the discussion in 
the community. The higher frequency of the commits, the more active it is. Higher enthusiasm can help you find the answer 
easier when you have problems.

When you’ve found a project you’d like to contribute to, do a quick scan to make sure that the project is accepting contributions. 
Otherwise, your hard work may never get a response.

Here’s a handy checklist to evaluate whether a project is suitable for new contributors [1].
```
Meets the definition of open source
  Does it have a license? Usually, this is a file called LICENSE in the root of the repository.
Project actively accepts contributions
  Look at the commit activity on the master branch. On GitHub, you can see this information on a repository’s homepage.
  When was the latest commit?
  How many contributors does the project have?
    How often do people commit? (On GitHub, you can find this by clicking "Commits" in the top bar.)
  Next, look at the project’s issues.
    How many open issues are there?
  Do maintainers respond quickly to issues when they are opened?
  Is there active discussion on the issues?
  Are the issues recent?
  Are issues getting closed? (On GitHub, click the "closed" tab on the Issues page to see closed issues.)
  Now do the same for the project’s pull requests.
    How many open pull requests are there?
    Do maintainers respond quickly to pull requests when they are opened?
    Is there active discussion on the pull requests?
    Are the pull requests recent?
    How recently were any pull requests merged? (On GitHub, click the "closed" tab on the Pull Requests page to see closed PRs.)

Project is welcoming
  A project that is friendly and welcoming signals that they will be receptive to new contributors.  
  Do the maintainers respond helpfully to questions in issues?
  Are people friendly in the issues, discussion forum, and chat (for example, IRC or Slack)?
  Do pull requests get reviewed?
  Do maintainers thank people for their contributions?
```

B. Learn how the open source community work.

When you decide which project you want to contribute, now you should understand how it works.
Documents: Be sure to remember that reading documents is much more important than reading code at first. These files are usually listed in the top level of a repository, 
including license, readme, contributing, tutorials and so on. Reading these documents can give you much valuable information of the 
project in a short time. For example, readme is the instruction manual that welcomes new community members to the project. 
It explains why the project is useful and how to get started. 

Most of large Open Source projects have a series of documents which tell the important details that new contributors need to pay 
attention to, e.g., In Linux Kernel community, How to do Linux Kernel development not only contains some rules of the community but 
also tells contributors what they should pay attention to in the software development process. Make sure to make good use of these 
valuable resources.

You should understanding the way that contributors collaborate. Open source projects use the following tools to organize discussion. 
    - Issue tracker: Where people discuss issues related to the project. Maybe you could find the bug there you want to deal with. 
    - Pull requests: Where people discuss and review changes that are in progress. 
    - Discussion forums or mailing lists: Some projects may use these channels for conversational topics. Others use the issue tracker for all conversations. 
    Many contributors’ first interactions with the Open Source community usually happen there. Please subscribe the project’s mailing list,
    thus you can receive interesting discussions and sharing your idea.

If the project is on GitHub, check out Make a Pull Request, which @kentcdodds created as a walkthrough video tutorial. You 
can also practice making a pull request in the First Contributions repository, created by @Roshanjossey.

C. How to make your first contribution?

There are many types of things you could do in your first contribution.

1. Send an email
The first contribution usually is not writing code. Researchers found that often a significant period of observation (lurking), 
ranging from a couple of weeks to several months, was needed before a joiner became a developer [2]. However, the standard deviation 
was quite high, due to the variance of technical skills and the time that the contributors devote. 

Therefore, please choose the project that matches with your specialized knowledge and try to spend a little more time. 
During this time, new contributors usually participate in discussion via email. If you want to join an open-source project, 
the first thing that you should do is getting on the mailing list. The following list gives the types of activities you could 
try in your email [2]. Maybe your email will receive no response, don’t give up.

1) Ask question 
2) General technical discussion
3) Usage feedback (no bug report) 
4) Request for help 
5) Point to technical resources/ refer to other projects 
6) Express interest to contribute 
7) Suggestion for improvements 
8) Propose/outline bugfix (no code) 
9) Coordination and organization discussion 
10) User support 
11) Answer (technical) question
12) Self introduction 
13) Announcing “external” contribution 
14) Give Feedback on others contribution 

2. Activities in issue tracker system

1) Report an issue
Before reporting an issue, you need make sure this issue has not been reported by others (You could check it in the 
issue tracker system). Then, you need to describe what the issue is, the context and how to reproduce it.
2) Comment on an issue 
These comments might be an interpretation for a confusing report, or suggesting a possible solution. Researchers [3] 
found that starting from a comment instead of reporting an issue also reflects such an attitude — it means she is 
intentionally getting involved, perhaps by first finding a similar issue and commenting on it instead of simply reporting 
an issue she encounters as a user.
3) Commit code
It is much difficult for new contributors to contribute code. If you want to challenge yourself at beginning, the first thing you 
should do is choosing the appropriate component. The following three items may help you [4].
a) Choose the component which is easy to modify and coding. 
For example, some components perform simple tasks, such as documentation. On the contrary, in a product, some domains are always 
considered to be more difficult than others, e.g., some critical modules. For new contributors, try to avoid these kind of components.
b) Choose the component with easier computer language. 
Some languages are complex and difficult to learn, while others, i.e. simple script languages can be mastered fairly easily.
c) Choose the component which has less dependent on others. 
This allows contributors to use existing functionalities without having to understand the rest of the specific functionalities used 
by other components. And such components can be added or removed at any point, often without having to recompile the whole source 
code.

### References:

[1] How to contribute to Open Source? https://opensource.guide/how-to-contribute/#orienting-yourself-to-a-new-project
[2] Krogh G V, Spaeth S, Lakhani K R. Community, joining, and specialization in open source software innovation: a case study[J]. Social Science Electronic Publishing, 2003, 32(7):1217-1241.
[3] Zhou M, Mockus A. What make long term contributors: willingness and opportunity in OSS community[C]// International Conference on Software Engineering. IEEE, 2012:518-528.
[4] Xin Tan, Hanmin Qin, Minghui Zhou: Understanding the Variation of Software Development Tasks: a Qualitative Study. Internetware 2017: 15:1-15:6
