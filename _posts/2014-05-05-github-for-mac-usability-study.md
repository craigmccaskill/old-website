---
layout: default
title: GitHub for Mac - A usability study
author: Craig McCaskill
category: null
published: true
---
# GitHub for Mac - A usability study#

## Objective
Usability study on some basic interactions within GitHub for Mac. I love GitHub and decided to take a step back and see if I could find any areas of improvement to the UX of one of their products. 

## Test Parameters
* What: GitHub for Mac
* Who: People familiar with Git and GitHub (have used both at least a couple of times in the last month) who have not used GitHub for Mac before.
* Where: Denizens of various coffee shops in the SOMA district of San Francisco. 

### Test Tasks
It's important to set a base line of what you're actually testing for things like this, so all users were asked to complete the following actions within the product:

1. Clone a repository from a GitHub page.
2. View most recent set of commits
3. Break up changes into two partial commits
4. Update with server
5. Change branch
6. Merge current branch with master

These tasks were selected as (with the exception of number 3) they are all fundamental git interactions. 

## Data Synthesis
![Synthesis](http://imgur.com/zjoKR0W.jpg)

The big question when gathering results like this is always "what does this actually mean". Couple of things here.

1. Going through the transcriptions for each of the user tests, I noted everything that stood out and put it on a postit. I used a different color postit for each user (this helps as a sanity check if just so happen to get a user who struggles with *everything*).
2. With my newly forged postits, I then arranged them into columns based on the task, this lets me see if any of the tasks were especially problematic. 
3. I also placed color coded dots on each of the postits based on their task. This let me re-arrange the postits out of their task-coloums into other configurations and still have an immediately obvious correlation to the specific task. 

## Findings

Thoughout all the tests, none of the users had any trouble changing branch, so I'm going to rule that task out and focus on lower hanging fruit. This isn't to say there aren't some tweaks that could be made to improve this interaction, but by and large it's working as intended. 

If you look back at the task column view, you can see that *every* user had some issue with cloning a repository. Now, this is the very first step and a very likely action for a user to want to complete on their first run of the app. While there is a first run wizard that lets you add existing local repositories that I didn't include as part of this usability study, it's very possible (dare I say likely?) that a user completely skip this step or just isn't interested in adding a local repository and instead wants to add a remote repo.

### Issue #1

#### Cloning an existing repository
The majority of the test users when asked to clone a repository, thinking they knew how this worked, either copied the GitHub project URL or the clone URL typically used for ssh and tried to find somewhere to plug it into the application. This is fantastic -- as soon as you find something that *everyone* has some difficulty completing you know there are changes you can make. There's nothing worse than making some changes that help user group A that ends up making things worse for user group B. If everyone needs a little help, it's far easier to make improvements that don't negatively impact a subset of your users.

Nobody immediately found the corrent (and only) way of cloning a remote repo via the 'Clone in Desktop' button on GitHub.com and some users actually got to the point of giving up the process entirely and had to be guided through to task completion. 

![Clone in desktop button](http://i.imgur.com/Z3BtPAa.png)

There's a really strong [mental model](http://craigmccaskill.com/mental-models.html) in place here, a set of assumptions from users who have done this before. They think they know what to expect, and as designers, if we don't give them that we'll end up just causing confusion. 


Clone in Desktop is not the most prominantly displayed button on GitHub.com, but regardless I find it odd there isn't a way to add a repository by URL. It's a super simple fix to just add a clone button to the GitHub with a URL field and have the app reach out to GitHub.com and pull down the selected repository to the default . 

### Issue #2

#### Updating with the server
The other frequently encounterd issue was when going through these tasks was with the sync button. While promenantly displayed at the top right of the UI, it's not entirely clear what this button does. More importantly, it doesn't actually map to how people typically use git. Most of the users, when asked to update with the server immediately started looking around the UI for actions to push or pull, again, this is a [mental model](http://craigmccaskill.com/mental-models.html) that anyone with prior git experience will attempt to draw from to help them navigate the UI.

Furthermore, some users just flat out did not trust the sync button. A typical git workflow from the command line would be to run git status before pushing or pulling. With this in mind, a couple of users while they recognised that sync was probably what they were looking for, they didn't want to initiate the sync action for fear of screwing something up. There was no visability as to the current status of the git tree and what sync would actually do. One user specifically actually tried to right click sync to see the arrow on the UI indicated it was a dropdown. This actually initiated the sync, which prompted the user to panic and start mashing the escape key. 

![sync button image](http://imgur.com/ZyBcvai.jpg)

My recommendation here would be to add the capability to check the current status and a preview of changes to be made via sync. Better yet I'd update the terminology to more accurately map the push/pull mental model existing git users already have.


### Issue #3

#### Merge current branch with master
The third most common problem encountered was when asking users to merge their current branch with master. I attribute this entirely down to iconography. 

![merge ui view image](http://imgur.com/YOy1xEe.jpg)

See that button? Notice the icon. What do you think that button does? Does it show current state, is it inviting a click for further options or is it directing the users attention. It turns out, none of the above. 

![merge ui slide image](http://imgur.com/XhnqU0I.jpg)

Clicking this button causes an extra pane to slide out (so that's what the icon indicates!), allowing the user access to the merge view. This is a really confusing use of iconography which mirrors the experience 3/5 of the users tested found. Most believed this text was an indication that we were *already* in merge view and lead to them diving into menus and settings pages looking for something that was sitting directly infront of them *that they had already seen*. 

My recommendation here would be some slight UI tweaks to make merge view more obvious, likely by moving merge view to be always open at the bottom of the page.

[Here's a quick mockup of how that might look, if you're interested.](http://imgur.com/peTLSxZ.png)

## Conclusion
GitHub for Mac is a good product, but I feel it suffers from some confusion over who the target market is. While I appreciate GitHub for Mac might've been conceived as an application targetted at non or beginer developers, it doesn't do a good job of servicing either audience. On the other hand, it simplifies many of the things seasoned git users have come to expect, breaking their mental models or removing functionality they need to feel comfortable in the tool and on the other it doesn't *quite* do enough to introduce someone without any git knowledge into contributing to a repository.

There's a lot of value in having a client aimed at developers, offering insight into the more visual aspects of git such as deep dives into complicated branching, merging, history or diffs. 

There's also a lot of value in having a client aimed at people with little to no git experience, guiding them through checking out their friends or colleagues code and teaching them the fundamentals of a good git workflow. 

GitHub for Mac doesn't cater to either of these audiences. This is the difference between a good product and a great one. Double down on who matters to your product rather than trying to make do with opening your arms to everyone. 