# Exam Preparation & Taking the Exam

This page offers some advice as to some possibilities for preparing for the AP Computer Science A exam. This is largely based on personal opinion.

## Exam preparation in general – start here

Here are some things you may want to consider doing to prepare for the AP Exam:

* Do everything listed in ["Navigating this guide"](#navigating-this-guide) section.

* Read through the ["General exam tips"](#general-exam-tips-for-exam-day) section.

* [Practice. the. FRQs.](../resources.md#frq) A good way to do this would be to choose a past FRQ, complete it, compare your solution to the canonical solution in the Scoring Guidelines, and score it with the Scoring Guidelines.
  * You can also "check" your score by viewing one of the sample responses, scoring it yourself, and comparing your score to the official score.

* Review AP Classroom content and questions for topics you may need to review.

* Practice sample MCQs from the [Course and Exam Description](https://apcentral.collegeboard.org/pdf/ap-computer-science-a-course-and-exam-description.pdf?course=ap-computer-science-a), page 191.

* Watch the AP Daily: Live Review Sessions. These sessions review the most important course content in preparation for the AP Exam.
  * For the 2022 AP Exam, these are streamed daily on [YouTube](https://www.youtube.com/playlist?list=PLoGgviqq4845xKOY11PnkE7aqJC7-bYrd) from April 18-21 and April 25-28 at 7:00 pm EDT (UTC-4).
  * You can also watch the VODs after the fact for both 2021 and 2022. These are on the same YouTube playlist or on AP Classroom.

* Familiarize yourself with the [task verbs used on the exam](https://apstudents.collegeboard.org/courses/ap-computer-science-a/exam-tips) so you know what you're doing when writing FRQ responses. There are only three, and they are basically common sense.

* You may want to focus more of your preparation on the parts of the course that will appear most frequently on the AP Exam. This information is detailed in the [Course and Exam Description](https://apcentral.collegeboard.org/pdf/ap-computer-science-a-course-and-exam-description.pdf?course=ap-computer-science-a) (page 19). For example, Unit 4: Iteration composes the largest portion of the MCQs, while Unit 1: Primitive Types and Unit 10: Recursion, to name a few, have much less weight.
  * Note that these weights are specific to the MCQs. The FRQs have their own specific structure, detailed on the ["about the exam"](about_the_exam.md) page.

## Navigating this guide, in particular

General suggestions for anyone, regardless of level of comfort with the course content:

* Read through this page – to see what you might want to look over

* Read through the ["about the exam"](about_the_exam.md) page – to know what to expect

* Read through the [topic list](topic_list.md). This is a full list of pretty much every topic assessed on the AP Exam. By running through this list, you can see what individual topics you may need to review.

* Read the ["gotchas"](gotchas.md) page. Even if you are confident about the course content, you may have overlooked/forgotten some of the things listed here, which may trip you up on the exam.

* Check out the [resources](../resources.md) page and consider looking at anything that piques your interest or might be helpful.

If you are having trouble with a particular unit or units, you probably want to look back at any class resources for those topics or the unit pages in this guide, if they are complete.

## General exam tips for exam day

An assortment of pointers based on College Board publications, common sense, and other sources.

### Before the exam

The usual – start studying early, go to bed early, and eat breakfast.

### Multiple-Choice Questions

* The usual – skip over questions you are having issues with, watch your time, etc.

* Process of elimination may be helpful for some questions, especially when it is immediately clear that one or more answer choices are incorrect.

### Free-Response Questions

* Read through the full question and specification before writing anything. If you are well-prepared, you will have the time, and it will be much better than if you make a mistake and need to restart/reorganize your code.

* Don't use methods, constructs, or other material that is not covered in the CED or listed on the Java Quick Reference. It may hurt your score if you are not fully familiar with what you are doing.

* Leave space in between lines of code in your solution in case you need to add something later.

* **Do not** destroy persistent data! Remember that all method parameters of reference types are passed by reference, so if you change the object referenced by a reference parameter, the original object from the calling method will also be changed. For example:

  ```java
  public static void change(int[] a) {
    a[0] = (int) (Math.random() * 100);
    System.out.println(a[0]);
  }
  ```

  Changing the value of the array element at index `0` will also change the value of that element in the array stored by the calling method. This is because they are the same array!

  Destroying persistent data on an FRQ response unless explicitly directed to results in a penalty, per the Scoring Guidelines.

* If you're told that something is a precondition, don't check it in your code! By its nature, the existence of a precondition means that you can assume that it will be satisfied before the method is called. If you accidentally write an improper check, you will receive a score penalty, per the Scoring Guidelines.
