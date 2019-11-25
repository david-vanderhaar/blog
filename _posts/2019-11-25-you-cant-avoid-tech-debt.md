---
layout: post
title:  "You Can't Avoid Technical Debt"
date:   2019-11-25 01:26:30 -0400
categories: blog
---

## **What is Technical Debt?**
**Technical debt** refers to an accrued development cost caused by implementing limited, short-term solutions over more thorough, long-term solutions. It is often analogized to monetary debt because of its useful metaphor in dealing with interest and debt repayment -- debt, left unchecked, will compound and grow more costly ro resolve. This analogy is somewhat helpful, but does not capture all angles of dealing with technical debt because of the inherent negative connotations of monetary debt.

According to [Tom Edith et al](https://dlnext.acm.org/doi/abs/10.1016/j.jss.2012.12.052). this kind of debt can be accrued in different ways.  It can be **strategic**, **tactical**, **inadvertent**, or **incremental**. The authors summarize these four classifications as follows:


  **Strategic debt** — This type of debt is incurred knowingly for strategic gains (such as first to release in market) and intended for long-term.

  **Tactical debt** — Such debt instances are incurred knowingly for quick gains and are typically intended for short-term.

  **Inadvertent debt** — Inadvertent debt is incurred unknowingly usually due to lack of knowledge and awareness.

  **Incremental debt** — Periodic inadvertent debt results in incremental debt.

Development teams and clients should, together, strive towards well-crafted systems that implement strategic and/or tactical debt while avoiding their unintended counterparts.


## **Why is Debt Inevitable?**
Software engineers are often building systems on top of systems and interfacing with environments outside of their control. A few examples include the user’s browser choice, system dependency updates, market deadlines, and even budgetary limitations. Any of these unknown variables can become roadblocks to releasing or updating software. A common example of navigating this compromise involves browser support. The client and development team may forego full support for Internet Explorer 10 and below. This is would accrue some technical debt because, if the need arises later, developers will need time and money to add in support later. However it may be warranted based on the intended user demographic. At this point the team may consider accruing deliberate debt. This is, generally, a good decision trying to avoid over-engineering, release the minimum viable product (MVP) on time, or optimize the feature/budget ratio.


## **Sources of Debt**
Technical debt can be further classified into several categorical sources.


### **UI/UX Debt**
It often benefits the project to have mock-ups and wireframes before implementation begins. These types of documents provide a concise translation layer for communication between non-technical clients and the development team. If implementation begins before desired functionality is understood,  it can lead to refactoring later.  


### **Specification Debt**
Specification debt defines, generally, what features and user scenarios the application must incorporate. It can also refer to the list of technologies used to accomplish these goals. Clients often need to tack on or redefine features after development starts. If deadlines are tight, and corners must be cut, the development team can seek out opportunities for strategic / tactical debt. If it becomes necessary to cut corners, even strategically, it is important that all parties understand the technical implications of the changes being made. Otherwise rushed decisions become a major source of inadvertent and incremental debt.


### **Experience Debt**
Lack of development experience with the technologies involved can be a potent source of inadvertent / incremental debt due to ignorance of the codebase or disregard for common development standards.


### **Documentation Debt**
Lack of documentation for: the technology stack; build and deployment processes; or implementation of complex systems can cause head scratching and lead to poor design decisions.


## **Mitigating Debt**
There are several ways the client and development team can work together to mitigate the sources of debt above.


### **Estimate Rigorously**
Project managers should strive to involve developers in client estimates and budget-making. This often leads clients to notice the gaps in their specifications and initial design requests. Estimates are all about working with unknowns so the more a team can document their estimation process, the better. The client and development team should also allow for re-estimations. This will keep expectations fresh and in check. Finally, teams may consider pushing for an exploratory phase of development to minimize the estimation of substantial unknowns.


### **Account for Experience**
Including at least one highly experienced developer on the team can be a tremendous help in avoiding inadvertent technical debt because they will be well-versed in common signs of debt. An experienced developer is able to call out code smell. This occurs when a developer consistently implements repetitive logic or deviates from code standards agreed upon by most users of a specific toolset. An experienced developer can also strike a balance between re-paying past technical debts and leaving them in place. It is often difficult for the inexperienced to know where code-base is heading based on a client’s feature requests.


### **Document Debt Strategically**
Finally, though there is much more we can do to tackle debt, documentation of existing debt will aid decision-making down the road. Whenever a compromise must be made during design or implementation, the team should document the decision so that a budget and plan can be better laid in the future.


## **Conclusion**
We, as software developers, can’t avoid technical debt, but we can do our best to identify, document, and budget for it. This should be a continuous process from MVP to release and beyond. Identify common or potential sources of debt whether that be lack of UX planning, ill-defined specifications, lack of team experience or documentation. Document and classify which of these debt sources are **inadvertent** or **incremental **and which are **strategic **or** tactical**. This will give the team a better sense of hierarchy in tackling such debt. Finally, build a plan of attack with the help of any experienced developers at your disposal.


## **Sources**
[https://en.wikipedia.org/wiki/Technical_debt](https://en.wikipedia.org/wiki/Technical_debt)

[https://hackernoon.com/there-are-3-main-types-of-technical-debt-heres-how-to-manage-them-4a3328a4c50c](https://hackernoon.com/there-are-3-main-types-of-technical-debt-heres-how-to-manage-them-4a3328a4c50c)

[https://www.infoq.com/articles/pragmatic-technical-debt/](https://www.infoq.com/articles/pragmatic-technical-debt/)

[https://dlnext.acm.org/doi/abs/10.1016/j.jss.2012.12.052](https://dlnext.acm.org/doi/abs/10.1016/j.jss.2012.12.052)

[https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=312135](https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=312135)

### Until Next Time

## Take it Easy
