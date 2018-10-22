# How to communicate? (contributed by Xin Tan)

In software development, efficiency and quality are the core goals pursued by developers. Researchers found that the total 
time of coding only accounts for half a day [1], and 37% of the rest of the time is spent communicating or writing emails [2]. 
In particular, in Open Source community, developers are distributed over the world and collaborate with each other through the 
Internet. The communication required in distributed development is often considered more challenging than communication for 
acolocated team due to the lack of face to face communication, different time zones, culture differences and so on [3]. 
Therefore, communicating efficiently is very important. And in many ways of communication, email becomes an indispensable way for 
developers to share information and discuss issues. Efficient communication can help you get useful information from experts as 
soon as possible. For the questions you have, through communication, people can get a deeper understanding. Besides, communication 
is one of the important ways to establish personal reputation in Open Source community.

Whether you’re a one-time contributor or trying to join a community, working with others is one of the most important skills you’ll 
develop in open source [4]. Here are important suggestions specially when submitting patch, which can help you achieve efficient 
communication. These suggestions mainly involve seven aspects: motivation, problem description, implementation, quality, language, 
basic requirement of the community and time.

The examples given below are from the Linux kernel community.
### Motivation
1. Try your best to describe your motivation, including why you did and what you did.

Whatever you do, please try your best to describe your motivation. A good motivation can make other people understand your 
intention more easily and assess the value of your work preliminarily. How to write a good motivation in your email, and here 
are some tips for you.

For patch submission, a good description of motivation is very important, which is beneficial to both reviewers and authors. 
For reviewers, it can save time, and for authors, it can be easier to get the patch accepted. The motivation of patch usually 
contains two parts: a brief description of what you did and why you did. Don’t just include what but lose why. You should provide 
convincing reasons to make reviewers find the value of your patch easier. For different types of patches, when expressing your 
motivation, there are different features need to be satisfied.

*If you want to add a new feature, you should provide sufficient reasons why this functionality is required.*

Generally, adding a new function involves a lot of code, which brings many problems and makes the code difficult to maintain. 
If it's not very necessary, reviewers are generally not willing to accept this kind of patch. Therefore, you must provide a 
good reason to explain why this patch is necessary. The reason can be very sufficient if you can give something similar to 
"what a bad effect there is without this patch" or "It can support/enable… ".

```
Additionally there is no install rule and this is needed for make -C tools vm_install to work properly. /patch/9516003/
```
```
Adds the updated PSS event table to enable Telemetry driver on Gemini Lake. /patch/9855065/
  Introducing NR_VMAP_STACK_CACHE /patch/9564015/
comment: This should really explain _why_ we want/need this.
```

Note: If the feature has been widely accepted previously, that is to say, reviewers can easily know the importance of this feature, you may could omit providing the reason. 
```
supports 3bit width iomux type. /patch/9566429/
```
For other types of patches, e.g., fix bug, clean code, make improvement, just express what you did which has already reflected the reasons. 
```
Fixed checkpatch.pl warnings of the form "function definition argument 'foo' should also have an identifier name" in header files. /patch/9793895/

### Problem description

2. When you fix a bug, please describe the scenario of the bug or how to reproduce it, or the issue report.

Providing this information can help reviewers to get a more comprehensive understanding of what you did and confirm whether you have 
solved it. If the bug is reported by other people, please include the issue id and title, which can help reviewer easier to locate the 
bug you fix. If the bug is reported by self, please include the scenario of the bug or how to reproduce it, which looks like an issue 
report. 
```
When CONFIG_PM_SLEEP is disabled, we get a couple of harmless warnings: drivers/net/ethernet/renesas/ravb_main.c:2117:12: error: 'ravb_resume' defined but not used [-Werror=unused-function] drivers/net/ethernet/renesas/ravb_main.c:2104:12: error: 'ravb_suspend' defined but not used [-Werror=unused-function] /patch/9301619/
```
```
Fixes: 41e94a851304 ("add devm_memremap_pages") /patch/9498129/
```

3. Including the seriousness of the bug can bring more attention from reviewers.

Besides describing the motivation, the scene of the bug (how to reproduce it) and how to fix it, you should take great effort to 
what serious consequences it can cause. For example, the reasons like it can lead system crash, or can't support to the core device, 
are very convincing. Otherwise, it is difficult to understand the importance of patch when the reviewers are inadequately aware of 
the scene you described, which will result in the patch rejected. 
The following words are usually used to describe the seriousness of the bug: *error, warning, block, crash, wrong, invalid, leak, 
can't support, interrupt**
```
When dev.of_node is not NULL, we also need to set IRQF_TRIGGER_FALLING flag, otherwise it may cause uncertain interrupts. /patch/9319317/
```
```
Depositing them in the collapse path resulting in a pgtable_t memory leak also giving errors like "[ 2362.021762] BUG: non-zero nr_ptes on freeing mm: 3" /patch/9470935/

### Implementation
```
4. Briefly describe the core technical details.

Providing technical details can make recipients know how you did much easier. Focus on the core technology you used in the patch. 
Don’t include too much details, because it is a waste of time and in fact all the details have been shown in the code.

For the patches which have large amount of code, please include the core technical details, it will be very helpful for reviewers 
to understand your code easily.
```
Check that location after HLC write operations if the ready bit is not set and return an appropriate error code instead of always 
returning -EAGAIN. /patch/9342883/ 
```
```
/patch/8947691/ : This patch has 104 SLOC, but has no explanation of the implementation details.
```
Note: For some patches that are quite easy, for example fixing misspelling or only contain a few SLOC, writing detail is meaningless. 

5. If you add a new feature, especially for which includes several functions, please list all of them or give a brief introduction.

For the reviewers, because the functions of patch are new, they will feel unfamiliar. In addition, considering the code is more 
complex and not perfect, it will take more effort to look at the code directly. Therefore, all the support functions need to be 
clearly enumerated in the description. The reviewers can assess the importance of patch intuitively.
ince all em_sti instances are created after time_init(), none of them should ever observe any clock rate changes.
   - Determine the ->rate value in em_sti_probe() at device probing rather than at first usage.
   - Set the clockevent device's rate at its registration.
   - Although not strictly necessary for the upcoming clockevent core changes, set the clocksource's rate at its registration for consistency. /patch/9558771/

6. Clearly describe the improvement after applying the patch.

Whether you are suggesting a new idea or refactor code or do clean-up, you need to provide the improvement after applying your idea. 
For different scenarios, the improvement can be different. Here are some common ways to describe improvement.

** Use numbers to describe the improvement of system performance **

For example, ‘reduce 30% memory consumption’, ‘the processing time reduce 3ms’. If you claim improvements in performance, memory consumption, stack footprint, 
or binary size, include numbers that back them up. But also describe non-obvious costs.
```
/patch/9567873/
Declare device_type structure as const as it is only stored in the
type field of a device structure. This field is of type const, so add
const to the declaration of device_type structure.
File size before: drivers/hid/intel-ish-hid/ishtp/bus.o
   text	   data	    bss	    dec	    hex	filename
   4260	    336	     16	   4612	   1204 hid/intel-ish-hid/ishtp/bus.o
File size after: drivers/hid/intel-ish-hid/ishtp/bus.o
   text	   data	    bss	    dec	    hex	filename
   4324	    272	     16	   4612	   1204 hid/intel-ish-hid/ishtp/bus.o
```
Make code more readable and easy to maintain. 
```
Use module_platform_driver() helper to simplify the code. /patch/9429633/
Provide support. 
Relocate get_ncq_tag_v2_hw() to a common location, as future hw versions will require it. /patch/9786465/
```

7. If there is cost after applying the patch, please provide trade-offs.

Optimizations usually aren’t free but trade-offs between CPU, memory, and readability; or, when it comes to heuristics, 
between different workloads. Describe the expected downsides of your optimization so that the reviewer can weigh costs 
against benefits. 
```
These are less efficient than using the extract and insert functions, but allow more precise debugging code. /patch/9678053/
```
8. If the patch refers other information, e.g., commits, email content, the view of the expert, or links of related information, 
please include it.

Including this information can help reviewers to get a more comprehensive understanding of what you did. And make your work more 
reliable. 
```
The reason is that idling is key for providing service guarantees to processes doing sync I/O [1].   [1] P. Valente, A. Avanzini, "Evolution of the BFQ Storage I/O Scheduler", Proceedings of the First Workshop on Mobile System  Technologies (MST-2015), May 2015. http://algogroup.unimore.it/people/paolo/disk_sched/mst-2015.pdf /patch/8184361/ 
```
It references the paper.
```
Also allow IRQ 9 to work (it aliases to IRQ 2 on the card), as per Ondrej Zary's patch. /patch/9460365/
  comment： can you please quote your emails?  I can't find any content in between all these quotes. /patch/9563819/
```

### Quality

9. If there are several ways to implement the same function or your solution has something unique, showing the superiority 
of your implementation will be much better.

On the one hand, it can show the superiority of your solution, and on the other hand, it can also show that you have made a lot of 
effort. 
```
Changing this as a side-effect of dumping core isn't a safe thing to do (a few test suites have already flagged this behavioral change). 
Instead, restore the RET_KILL semantics, but still dump core when a RET_KILL delivers SIGSYS to a single-threaded process. /patch/9587563/
```
```
There are two ways to solve that:
   1) Reserve a hotplug state for LTTNG 2) Add a dynamic range for the prepare states.
While #1 is the simplest solution, #2 is the proper one as we can convert in tree users, which do not care about ordering, to 
the dynamic range as well. /patch/9518571/
```

10. If your patch is a prototype or on-going, please include the limitation.

For some patches, the initial version submitted by developers is usually just a prototype. The code only involves the implementation 
of the core part. Maybe some small functions or details are not implemented, and even bug will appear. Therefore, you need to point 
out the limitations of the current patch, so that the patch will not be directly denied for these reasons. 
What is not working/to be added later:

* Display - waiting for "tiny DRM" to be mainlined
* Speaker - needs new PWM sound driver
* USB - waiting for OHCI and MUSB device tree support to be mainlined
* ADC - needs new iio driver
* GPIOs - broken because of recent changes to core gpio driver
* Bluetooth - needs new driver for sequencing power/enable/clock
* Input and output ports - need some sort of new phy or extcon driver
* Battery - needs new power supply driver (depends on ADC iio driver) /patch/9389859/

 “In some cases this is not possible because those seems to be broken and require GFP_NO{FS,IO} context which is not vmalloc compatible in general. Those need to be fixed separately.”

### Language

11. When describing what you did, please use imperative mood.

Describe your changes in imperative mood, e.g. “make xyzzy do frotz” instead of “[This patch] makes xyzzy do frotz” or 
“[I] changed xyzzy to do frotz”, as if you are giving orders to the codebase to change its behaviour. 
Corrects the WARN_ON statement for subsampling based on the JPEG Hardware version. /patch/9762891/
 This patch allows APEI generic error source table with external
IRQ to share a single IRQ.
Comment: "This patch" in a commit message is tautologically redundant. /patch/9855743/

### Basic requirement of the community

12.  Be sure to pay attention to the rules in the community, such as the formatting requirements.

This is the most basic requirement. 
```
Comment：Please don't put anything below the Signed-off-by: line, you will note that all other commits are written that way.
Also, your subject: needs a lot of work, again, look at other commit for the driver you are modifying to get it right. /patch/9838637/
```

### Time

13.  Start communication at the right time. 
For example, if you send a patch via email, be sure to leave enough time for review. You need consider the length of time for patch 
reviewing in the particular community as well as the size and difficulty of your patch. Besides you should also consider the 
community’s institutions for patch. For example, Linux kernel sets the first two weeks in the release cycle as the merge window. 
During this time, the patches which passed reviewing can be merged into main repository. After that only the patches related to 
bug fix can be merged. So if you want your patch applied in the new release, you’d better submit it in the previous version.

### References

[1] Perry D E, Staudenmayer N, Votta L G. People, Organizations, and Process Improvement[J]. Software IEEE, 1994, 11(4):36-45.
[2] Nakakoji K, Ye Y, Yamamoto Y. Supporting Expertise Communication in Developer-Centered Collaborative Software Development Environments[J]. 2010:219-236.
[3] Ben Linders, Making Distributed Development Work [EB/OL]. https://www.infoq.com/news/2017/03/distributed-development, 2017-05-02/2017-12-30
In software development, efficiency and quality are the core goals pursued by developers. Researchers found that the total time of coding only accounts for half a day [1], and 37% of the rest of the time is spent communicating or writing emails [2]. In particular, in Open Source community, developers are distributed over the world and collaborate with each other through the Internet. The communication required in distributed development is often considered more challenging than local team due to a lack of face to face communication, different time zones, culture differences and so on [3]. Therefore, communicating efficiently is very important. And in many ways of communication, email becomes an indispensable way for developers to share information and discuss with each other. Efficient communication can help you get useful information from experts as soon as possible. For the questions you have, through communication, people can get a deeper understanding. Besides, communication is one of the important ways to establish personal reputation in Open Source community.
Whether you’re a one-time contributor or trying to join a community, working with others is one of the most important skills you’ll develop in open source [4]. Here are important suggestions specially when submitting patch, which can help you achieve efficient communication. These suggestions mainly involve seven aspects: motivation, problem description, implementation, quality, language, basic requirement of the community and time.
The examples given below are from the Linux kernel community.
Motivation
1. Try your best to describe your motivation, including why you did and what you did.
Whatever you do, please try your best to describe your motivation. A good motivation can make other people understand your intention more easily and assess the value of your work preliminarily. How to write a good motivation in your email, and here are some tips for you.
For patch submission, a good description of motivation is very important, which is beneficial to both reviewers and authors. For reviewers, it can save time, and for authors, it can be easier to get the patch accepted. The motivation of patch usually contains two parts: a brief description of what you did and why you did. Don’t just include what but lose why. You should provide convincing reasons to make reviewers find the value of your patch easier. For different types of patches, when expressing your motivation, there are different features need to be satisfied.
If you want to add a new feature, you should provide sufficient reasons why this functionality is required.
Generally, adding a new function involves a lot of code, which brings many problems and makes the code difficult to maintain. If it's not very necessary, reviewers are generally not willing to accept this kind of patch. Therefore, you must provide a good reason to explain why this patch is necessary. The reason can be very sufficient if you can give something similar to "what a bad effect there is without this patch" or "It can support/enable… ".
Additionally there is no install rule and this is needed for make -C tools vm_install to work properly. /patch/9516003/
Adds the updated PSS event table to enable Telemetry driver on Gemini Lake. /patch/9855065/
  Introducing NR_VMAP_STACK_CACHE /patch/9564015/
comment: This should really explain _why_ we want/need this.
Note: If the feature has been widely accepted previously, that is to say, reviewers can easily know the importance of this feature, you may could omit providing the reason. 
supports 3bit width iomux type. /patch/9566429/
For other types of patches, e.g., fix bug, clean code, make improvement, just express what you did which has already reflected the reasons. 
Fixed checkpatch.pl warnings of the form "function definition argument 'foo' should also have an identifier name" in header files. /patch/9793895/
Problem description
2. When you fix a bug, please describe the scenario of the bug or how to reproduce it, or the issue report.
Providing this information can help reviewers to get a more comprehensive understanding of what you did and confirm whether you have solved it. If the bug is reported by other people, please include the issue id and title, which can help reviewer easier to locate the bug you fix. If the bug is reported by self, please include the scenario of the bug or how to reproduce it, which looks like an issue report. 
When CONFIG_PM_SLEEP is disabled, we get a couple of harmless warnings: drivers/net/ethernet/renesas/ravb_main.c:2117:12: error: 'ravb_resume' defined but not used [-Werror=unused-function] drivers/net/ethernet/renesas/ravb_main.c:2104:12: error: 'ravb_suspend' defined but not used [-Werror=unused-function] /patch/9301619/
 Fixes: 41e94a851304 ("add devm_memremap_pages") /patch/9498129/

3. Including the seriousness of the bug can bring more attention from reviewers.
Besides describing the motivation, the scene of the bug (how to reproduce it) and how to fix it, you should take great effort to what serious consequences it can cause. For example, the reasons like it can lead system crash, or can't support to the core device, are very convincing. Otherwise, it is difficult to understand the importance of patch when the reviewers are inadequately aware of the scene you described, which will result in the patch rejected. 
The following words are usually used to describe the seriousness of the bug: error, warning, block, crash, wrong, invalid, leak, can't support, interrupt…
When dev.of_node is not NULL, we also need to set IRQF_TRIGGER_FALLING flag, otherwise it may cause uncertain interrupts. /patch/9319317/
Depositing them in the collapse path resulting in a pgtable_t memory leak also giving errors like "[ 2362.021762] BUG: non-zero nr_ptes on freeing mm: 3" /patch/9470935/
Implementation
4. Briefly describe the core technical details.
Providing technical details can make recipients know how you did much easier. Focus on the core technology you used in the patch. Don’t include too much details, because it is a waste of time and in fact all the details have been shown in the code.
For the patches which have large amount of code, please include the core technical details, it will be very helpful for reviewers to understand your code easily.
Check that location after HLC write operations if the ready bit is not set and return an appropriate error code instead of always returning -EAGAIN. /patch/9342883/ 
  /patch/8947691/ : This patch has 104 SLOC, but has no explanation of the implementation details.
Note: For some patches that are quite easy, for example fixing misspelling or only contain a few SLOC, writing detail is meaningless. 
5. If you add a new feature, especially for which includes several functions, please list all of them or give a brief introduction.

For the reviewers, because the functions of patch are new, they will feel unfamiliar. In addition, considering the code is more complex and not perfect, it will take more effort to look at the code directly. Therefore, all the support functions need to be clearly enumerated in the description. The reviewers can assess the importance of patch intuitively.
ince all em_sti instances are created after time_init(), none of them should ever observe any clock rate changes.
- Determine the ->rate value in em_sti_probe() at device probing rather than at first usage.
- Set the clockevent device's rate at its registration.
- Although not strictly necessary for the upcoming clockevent core changes,
set the clocksource's rate at its registration for consistency. /patch/9558771/
6. Clearly describe the improvement after applying the patch.
Whether you are suggesting a new idea or refactor code or do clean-up, you need to provide the improvement after applying your idea. For different scenarios, the improvement can be different. Here are some common ways to describe improvement.
Use numbers to describe the improvement of system performance 
For example, ‘reduce 30% memory consumption’, ‘the processing time reduce 3ms’. If you claim improvements in performance, memory consumption, stack footprint, or binary size, include numbers that back them up. But also describe non-obvious costs.
/patch/9567873/
Declare device_type structure as const as it is only stored in the
type field of a device structure. This field is of type const, so add
const to the declaration of device_type structure.
File size before: drivers/hid/intel-ish-hid/ishtp/bus.o
   text	   data	    bss	    dec	    hex	filename
   4260	    336	     16	   4612	   1204 hid/intel-ish-hid/ishtp/bus.o
File size after: drivers/hid/intel-ish-hid/ishtp/bus.o
   text	   data	    bss	    dec	    hex	filename
   4324	    272	     16	   4612	   1204 hid/intel-ish-hid/ishtp/bus.o
Make code more readable and easy to maintain. 
Use module_platform_driver() helper to simplify the code. /patch/9429633/
Provide support. 
Relocate get_ncq_tag_v2_hw() to a common location, as future hw versions will require it. /patch/9786465/
7. If there is cost after applying the patch, please provide trade-offs.
Optimizations usually aren’t free but trade-offs between CPU, memory, and readability; or, when it comes to heuristics, between different workloads. Describe the expected downsides of your optimization so that the reviewer can weigh costs against benefits. 
These are less efficient than using the extract and insert functions, but allow more precise debugging code. /patch/9678053/
8. If the patch refers other information, e.g., commits, email content, the view of the expert, or links of related information, please include it.
Including this information can help reviewers to get a more comprehensive understanding of what you did. And make your work more reliable. 
The reason is that idling is key for providing service guarantees to processes doing sync I/O [1].   [1] P. Valente, A. Avanzini, "Evolution of the BFQ Storage I/O Scheduler", Proceedings of the First Workshop on Mobile System  Technologies (MST-2015), May 2015. http://algogroup.unimore.it/people/paolo/disk_sched/mst-2015.pdf /patch/8184361/ 
It references the paper.
Also allow IRQ 9 to work (it aliases to IRQ 2 on the card), as per Ondrej Zary's patch. /patch/9460365/
  comment： can you please quote your emails?  I can't find any content in between all these quotes. /patch/9563819/
Quality
9. If there are several ways to implement the same function or your solution has something unique, showing the superiority of your implementation will be much better.
On the one hand, it can show the superiority of your solution, and on the other hand, it can also show that you have made a lot of effort. 
Changing this as a side-effect of dumping core isn't a safe thing to do (a few test suites have already flagged this behavioral change). Instead, restore the RET_KILL semantics, but still dump core when a RET_KILL delivers SIGSYS to a single-threaded process. /patch/9587563/
There are two ways to solve that:
 1) Reserve a hotplug state for LTTNG 2) Add a dynamic range for the prepare states.
While #1 is the simplest solution, #2 is the proper one as we can convert in tree users, which do not care about ordering, to the dynamic range as well. /patch/9518571/

10. If your patch is a prototype or on-going, please include the limitation.
For some patches, the initial version submitted by developers is usually just a prototype. The code only involves the implementation of the core part. Maybe some small functions or details are not implemented, and even bug will appear. Therefore, you need to point out the limitations of the current patch, so that the patch will not be directly denied for these reasons. 
What is not working/to be added later:

* Display - waiting for "tiny DRM" to be mainlined
* Speaker - needs new PWM sound driver
* USB - waiting for OHCI and MUSB device tree support to be mainlined
* ADC - needs new iio driver
* GPIOs - broken because of recent changes to core gpio driver
* Bluetooth - needs new driver for sequencing power/enable/clock
* Input and output ports - need some sort of new phy or extcon driver
* Battery - needs new power supply driver (depends on ADC iio driver) /patch/9389859/

 “In some cases this is not possible because those seems to be broken and require GFP_NO{FS,IO} context which is not vmalloc compatible in general. Those need to be fixed separately.”
Language
11. When describing what you did, please use imperative mood.
Describe your changes in imperative mood, e.g. “make xyzzy do frotz” instead of “[This patch] makes xyzzy do frotz” or “[I] changed xyzzy to do frotz”, as if you are giving orders to the codebase to change its behaviour. 
Corrects the WARN_ON statement for subsampling based on the JPEG Hardware version. /patch/9762891/
 This patch allows APEI generic error source table with external
IRQ to share a single IRQ.
Comment: "This patch" in a commit message is tautologically redundant. /patch/9855743/
Basic requirement of the community
12.  Be sure to pay attention to the rules in the community, such as the formatting requirements.
This is the most basic requirement. 
  Comment：Please don't put anything below the Signed-off-by: line, you will note that all other commits are written that way.
Also, your subject: needs a lot of work, again, look at other commit for the driver you are modifying to get it right. /patch/9838637/
Time
13.  Start communication at the right time. 
For example, if you send a patch via email, be sure to leave enough time for review. You need consider the length of time for patch reviewing in the particular community as well as the size and difficulty of your patch. Besides you should also consider the community’s institutions for patch. For example, Linux kernel sets the first two weeks in the release cycle as the merge window. During this time, the patches which passed reviewing can be merged into main repository. After that only the patches related to bug fix can be merged. So if you want your patch applied in the new release, you’d better submit it in the previous version.
Reference:
[1] Perry D E, Staudenmayer N, Votta L G. People, Organizations, and Process Improvement[J]. Software IEEE, 1994, 11(4):36-45.
[2] Nakakoji K, Ye Y, Yamamoto Y. Supporting Expertise Communication in Developer-Centered Collaborative Software Development Environments[J]. 2010:219-236.
[3] Ben Linders, Making Distributed Development Work [EB/OL]. https://www.infoq.com/news/2017/03/distributed-development, 2017-05-02/2017-12-30
[3] How to Contribute to Open Source [EB/OL]. https://opensource.guide/how-to-contribute/#orienting-yourself-to-a-new-project, 2017-12-30.
