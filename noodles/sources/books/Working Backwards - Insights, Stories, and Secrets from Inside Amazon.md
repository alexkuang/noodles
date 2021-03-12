[[Colin Bryar]] [[Bill Carr]]

Book on Amazon culture written by two ex-Amazonians.  Expands on the Amazon [leadership principles](https://www.amazon.jobs/en/principles), backed up by narrative non-fiction from company history.

### Operational Excellence
Operationalize anything that is important.  Higher level goals and principles are broken down into every day processes: "if a company's principles must be memorized, then it's a warning sign that they aren’t sufficiently woven into the fabric of that company."  Good intentions like "we'll try extra hard next time" are not enough to fix a broken process or a mistake, because people already had good intentions when the mistake was made.

Put another way: it's not a real principle or goal until it is backed by a process.  This focus on operational excellence shows up everywhere in the book, e.g. "customer obsession" => working backwards + PR/FAQ, "ownership" => single-threaded leaders + autonomous teams.

### Autonomous teams
Teams should be autonomous and free from external dependencies as much as possible.  The first order effect of being blocked by external dependencies is the slowdown of innovation.  The second order effect is the decrease of morale from disempowered teams.  In the earliest days of global prioritization, "getting NPI'd" ("New Project Initiative") was an internal pejorative for having your team's resources drafted into an initiative that provided no benefit to your team.

Autonomous teams are organized such that they are independently functioning and self-sustainable, e.g. Team A shdould not have to ask for developer time from Team B to build something.  The same team owns the business goal and the associated products + tech so interests are aligned.

In addition to the obvious benefit of independence, this also ends up cutting down on the amount of overhead from scale.  The book cites, "[I've heard Jeff] say many times that if we wanted Amazon to be a place where builders can build, we needed to eliminate communication, not encourage it."  By treating teams as the atomic unit instead of individuals, the organization reduces the amount of point-to-point communication necessary for everyday work.

#### Service oriented architecture
Systems are organized in a service oriented architecture, where the business logic and underlying data are treated as one unit and exposed only via APIs.  e.g. there is no direct database access across systems owned by separate teams.  Starting with the goal of "externally facing" services resulted in stronger and more reusable systems over time.  Amazon saw the benefits of this approach when building Prime:

> It’s also worth pointing out that other teams had created building blocks for other purposes that could be deployed for developing Prime — and without which we would not have been able to meet the aggressive schedule. [...] One building block that we took advantage of was the Fast Track program.  [...]  Fast Track took two years to complete, and had required a massive amount of software development as well as physical modifications to the fulfillment centers. So we didn’t have to reinvent the wheel when it came to the accuracy and success rates of the shipping promises.  A second building block, as noted, was the subscription platform for an upcoming DVD rental launch.

#### Single-threaded leaders
An autonomous team is organized around a business goal and headed by a single-threaded leader whose only focus is that goal.  Corollary: it's not a real goal until it has a single-threaded leader on it.  One example from Amazon history is Fulfilled by Amazon, which languished for over a year without progress until 2005 when a single-threaded leader was appointed and given the appropriate resources to staff an independent team.  "The best way to fail at inventing something is by making it somebody's part-time job."

### Six page narratives
Amazon's use of the [[Amazon six-pager|six page]] narrative is pretty legendary at this point.  It is referenced throughout the book, mostly in relation to the press release/FAQ (PR/FAQ) process.

### Working backwards
Start with the customer experience in mind figure out what to build from there.  This provides clarity on keeping things simple while providing the best results for the customer.

"Working backwards" asks "What is the best thing for our customers, and how can we build the competencies to get it done?"  Contrast with "skills-forward," which asks "What are our current resources, and how can best leverage them to serve our customers and business?"  The authors credit this philosophical difference as the reason for Amazon's ability to expand from retail to seemingly unrelated verticals like AWS, FBA, and Prime Video.

### Long-term thinking
The book repeatedly hits on the themes of long-term thinking and the willingness to be misunderstood.  "Many companies will give up on an initiative if it does not produce the kind of returns they are looking for within a handful of years.  Amazon will stick with it for five, six, seven years--all the while keeping the investment manageable, constantly learning and improving."

One striking anecdote is the development of AWS.  Though the book does not mention the time period, one of the authors has said [elsewhere](https://review.firstround.com/how-to-build-an-invention-machine-6-lessons-that-powered-amazons-success) that the initial PR/FAQ process took about 18 months before developers started writing code.  At one point, one of the engineers protested, "We’re software engineers, not pricing specialists with MBAs . We want to write software, not more Word documents."

On the surface, 18 months without coding directly contradicts the "bias for action" principle.  This seems to be reconciled in two ways:  1) "action" includes iteration on a PR/FAQ, and is not limited to shipping code; 2) AWS aimed to be foundational infrastructure, so there were more "type 1" decisions to be made up front.  "with AWS we were certainly under time pressure to launch this product before our competitors did. But Bias for Action does not obviate the need for the painstaking aspects of the Working Backwards process."