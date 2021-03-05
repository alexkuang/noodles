Systems accrue tech debt when changes in requirements are bolted on after the fact.  Let's say we have an internal project management system which has a model for tasks:

```typescript
type Task = {
  id: number;
  name: string;
  due: Date;
  assigned: User;
  status: TaskStatus; // New, In Progress, or Closed
};
```

Now let's say we want to add reasons for tasks being closed, i.e. is the task closed because it is done, because it is a duplicate, because WONTFIX?  For reporting purposes, we need to provide a reason whenever closing a task.

Because we can't specify a closed reason for historical tasks with 100% accuracy, the temptation is to take the easy route.  We could add the closed reason as an optional field in our database / model, and just assert requirement when writing new tasks:

```typescript
type Task = {
  // ...
  closedReason: ClosedReason | undefined;
}

function saveTask(/** ... */) {
  assert(task.reason !== undefined);
  // rest of logic
}
```

However, this leaves the code in a weird state where everyone working with closed reasons will have to handle the legacy case by either 1) explicitly adding logic for it, or 2) doing `task.closedReason! // should be OK as this is a new task`  This logic will also leak out to any external interactions, e.g. if tasks are exposed via API or exported to an analytics system like Tableau / Looker.  Readability suffers, as readers now have to remember that "oh right, legacy tasks have empty closed reasons."

These points seem somewhat minor in isolation, but they start to create significant friction as instances of this "add-on" approach accumulate over time.

In contrast, if we pretend "the requirements always included mandatory closed reasons," then the column would just be non-empty in the database and model.  This requires more effort up front (what value should be used for backfills?), but results in a healthier system over time.