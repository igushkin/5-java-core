# 5-java-core

This is part of the Java Developer course from Yandex. Module - standard Java library and its features.

The repository contains my solution that has been verified from the reviewer to the task described below.

Technical specification
===================

It's time to practice and improve the tracker code with the help of the acquired knowledge about lists and hash tables! In this sprint, you will have to work with the history of task views, namely, to get rid of repeated views in it and restrictions on the size of the history. Let's go!

### Please note

It is not enough to implement the code in such a way that the program runs through the entire browsing history and only then deletes the previous view. After all, then the running time of this program will linearly depend on the length of the story.

Your goal is to implement the functionality so that the viewing time of the task does not depend on the total number of tasks in the history.

### The `HistoryManager` interface

We already have an interface, it remains to add the `void remove(int id)` method to remove the task from the view. And implement it in the `InMemoryHistoryManager` class. Add its call when deleting tasks so that they are also deleted from the browsing history.

### Further development of the algorithm with `CustomLinkedList` and `HashMap'

The program must remember the order of calls to the `add` method, because it is in this order that the views will be lined up in the history. It is convenient to use a list to store the order of calls.

If a task has been viewed several times, only the last view should be displayed in the history. The previous view should be deleted immediately after the new one appears — for `O(1)`. From the topic about lists, you learned that a constant operation execution time can guarantee a connected list `CustomLinkedList'. However, its standard implementation will not work in this case. Therefore, you have to write your own.

`CustomLinkedList` allows you to delete an element from an arbitrary place for `O(1)` with one important condition — if the program has already reached this place in the list. To fulfill the condition, create a standard `HashMap'. Its key will be the id of the task that you want to delete, and its value will be the place where this task is viewed in the list, that is, the node of the linked list. Using the task number, you can get the corresponding node of the linked list and delete it.

![image](https://pictures.s3.yandex.net:443/resources/S4_25-2_1643365392.png)

The implementation of the `getHistory` method should shift tasks from a linked list to an 'ArrayList` to form an answer.

### Testing the operation of the program

After writing the history manager, check his work:

* create two tasks, an epic with three subtasks and an epic without subtasks;
* request the created tasks several times in different order;
* after each request, output the history and make sure that there are no repetitions in it;
* delete the task that is in the history and check that it will not be output when printing;
* delete the epic with three subtasks and make sure that both the epic itself and all its subtasks are removed from the history.

Have fun programming!
