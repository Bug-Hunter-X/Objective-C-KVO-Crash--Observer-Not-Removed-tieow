# Objective-C KVO Crash: Observer Not Removed
This repository demonstrates a common yet subtle error in Objective-C related to Key-Value Observing (KVO) and object lifecycles.  Failure to remove observers before the observed object is deallocated can result in crashes or unpredictable program behavior.  The `bug.m` file showcases the problematic code, while `bugSolution.m` provides the corrected implementation.

**Problem:**
When an object observes another object using KVO and the observed object is deallocated without removing the observer, the observer attempts to access the memory of the deallocated object, potentially causing a crash or undefined behavior. 

**Solution:**
Ensure that observers are always removed using `removeObserver:forKeyPath:` in the appropriate lifecycle method of the observer, such as `dealloc` or when the observation is no longer needed.