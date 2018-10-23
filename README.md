# Open source education related topics

Possible RQs

## How to prepare the OSS-fluent developers: developing curiculum


Open Source Project Assignment in CS340 taught in Spring 18

### Sprint 1: Submit OSS project selection criteria
Due Feb 14 in younetid.md in this folder

Please describe criteria you plan to use in selecting OSS project to contribute. Please go over the points in 
Section A and for each note if you plan to use it. Also not any additional criteria you plan to use.

Remaining steps are assigned as issues to you

please go to https://github.com/COSCS340/oss/issues?q=is%3Aopen+assignee%3Ayourghid to see issues assigned to you. Pay attention to due date for the sprint. Thats the date when the assignment is due.

### Sprint 2:  Select OSS project
Please specify OSS project you actually plan to contribute to at the end of the oss/yournetid.md. \nPlease note\n* the projects website,\n* issue tracker,\n* version control system\n* as well as materials it has on how to contribute (if any).\n\n Please set label Ready to review once done. Pay attention to the due date.

### Sprint 3: Describe OSS project
Please describe OSS project selected at the end of the oss/yournetid.md.\n Give a brief introduction of the project:\n  - what the project is about,\n   - the scale of the project (e.g., the number of contributors, LOC),\n    - the history of the project\nits activity (total commits, recent commits), responsiveness (median time until first response for the last 10 issues), and suitability for making contributions (is there a recent external contribution)?\n\nPlease list the reasons why you think the project is suitable for you.  Please set label Ready to review once done

### Sprint 4: Develop a plan of contribution
Describe a few features that have been recently implemented,\n a few features that will/may be implemented in the near future, and\n the most attractive area for you to contribute.\n\n Please  choose and explain the mode of contribution you plane to make. For example: \n Review the current implementation of ...\n Improve existing implementation of ....\n Implement feature ....\n Fix bug ... reported by others.\n Test the new implementation using ...\n Write unit/regression tests for ...\n Improve documentation of ...\n Find and report a bug in ... \n\n  Please set label Ready to review once done

### Sprint 5: Select the first task
Please consider options listed in (https://github.com/COSCS340/lectures/blob/master/ContributingToOSS.md) Section C: How to make your first contribution? Please describe how you plan to use one of the options from the list or describe your approach if it is not listed. Please provide reasoning for your choice.\n\n  Please set label Ready to review once done


### Sprint 6: Make and document your contribution 
"Please implement and submit your contribution. Also, in the md file,\n- provide a link to the pull request,\n-patch,\n- issue where the contribution was submitted.\n Explain how you addressed the various points in Section C (https://github.com/COSCS340/lectures/blob/master/ContributingToOSS.md)\n Please provide reasoning for your choice.\n\n  Please set label Ready to review once done



## How individuals transition from data science students to data scientists

For example, there are 850K projects with R files
```
zcat pJR.gz| wc
 850079  850079 21573889
```
with 184K apparently related to coursework:
```
zcat pJR.gz| grep -Ei 'assignm|course|homework|class' | wc
 184813  184813 5985100
```

Could their contributions to repositories for class and for other purposes (including contributing to other repositories) could serve as an indicator of this.

Perhaps variables such as:
 

    Who the individual is
    What language they’re using
    What libraries/packages they’re using
    What they did in the repository for class
    The type of class (i.e., MOOC or in a higher ed setting)

 

influenced their contributions to open source projects and these could be used to understand the transition from student to practitioner better. Perhaps as I’m thinking about it it’s not yet very theoretically interesting, but – perhaps like software engineering – education is an applied area, and so I think this could be of interest to folks.

 
Obviously, there are a lot of open questions, including (to me), how to select/operationalize the variables, and model to specify, though I know you already have a lot of infrastructure and experience with these topics and so I hoped I could put this idea out there to see if it may have any legs. Because of my familiarity with the tools of the trade, I’d love to carry out such a study in the context of R-related repositories, but am familiar enough with Python that I would be more than happy to think about a project using Python- (or both R and Python-)related repositories. 

# References

## Learning in software engineering

Minghui Zhou and Audris Mockus. Developer fluency: Achieving true mastery in software projects. In ACM SIGSOFT / FSE, pages 137-146, Santa Fe, New Mexico, November 7-11 2010

Audris Mockus. Succession: Measuring transfer of code and developer productivity. In 2009 International Conference on Software Engineering, Vancouver, CA, May 12-22 2009. ACM Press.

Audris Mockus. Organizational volatility and its effects on software defects. In ACM SIGSOFT / FSE, pages 117-126, Santa Fe, New Mexico, November 7-11 2010. 

Minghui Zhou and Audris Mockus. Who will stay in the floss community? modelling participant's initial behaviour. Transactions on Software Engineering, 41(1):82-99, Jan 2015.
