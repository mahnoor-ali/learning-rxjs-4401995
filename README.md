# Learning RxJS
This is the repository for the LinkedIn Learning course Learning RxJS. 


Imagine that you’re working on an Angular application and need to call an API for a to-do list, shopping cart, or weather app data. Whatever the number of APIs you’re using, you need a way to manage them. RxJS can help. When you learn RxJS, you’ll be working with an industry standard library that seamlessly works with any Angular application to manage APIs and data. In this course, front-end software engineer Alex Nguyen gives you an introduction to RxJS that will get you started on building Angular applications that scale to handle data from anywhere. Learn key RxJS concepts, including exactly what an observable is. Find out how to use RxJS to create and subscribe to observables and leverage subjects—a specialized type of observable—for fine-grained control. Plus, explore ways to use RxJS with multiple observables.

# CONTENTS:
- Synx, Async, Reactive programming
- Behaviour Subjects
- Subjects
- Replaying Subjects
- Data transformation using -- pipe, map function
- Filtering data from observables
- Taking data and then unsubscribe on component destroy..
- Subsciption with first, last, skipWhile
- Listening multiple observables with combineLatest
- Preventing multiple calls using exhaustMap
- Switching to latest request using SwitchMap
- MergeMap

# Behaviour Subjects
BehaviorSubjects are a type of observable that allow you to get a current value from a subject.

# Qualities of BehaviorSubjects:
- the initial value is passed to our subscription function when we subscribe to them.

# POINTS
- A good rule of thumb is that: transforming your data should be done in pipes, and interacting with your angular component should be done in the subscription function.

- last(): will take the last value from an observable and pass it into a subscription
- from(): will take an array and convert that into a subject/observable for us.

- When we are making our weather app we have a button to admit an event to the observable to be passed to the subscribers. It can be pretty tempting to click this button multiple times. Sometimes our code handles the user input. Other times it can be expensive API calls we need to be careful of clicking too often. A way to fix this is to wait until the previous in progress event has been fired before creating a new one. We do this with exhaustMap, an RxJS operator that waits for the previous event to finish before starting another one. In our marble diagram, we can see how often a user wants to query the weather. While they can click the button multiple times, only the first request will be made and completed. All the other ones will be ignored until the request finishes. This ensures we're not overloading our APIs and subscribers with too many unfinished events.
- Use the exhaustMap operator to prevent making multiple requests until the most recent one has completed. 
