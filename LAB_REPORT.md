# Lab Report, Code Quality and Design Quality

Repository URL: https://github.com/Yumon-lab/itcs382-lab/tree/main

## Tools

| Item | Version or name |
| --- | --- |
| JDK | openjdk version "25.0.4.1" 2026-08-18 LTS | 
| Maven | ache Maven 3.10.0|
| IDE | 1.143.1 |
| SonarQube for IDE | 6.2.0 |
| AI tool and exact model | |

## Task 1. SonarQube on the starter code

Commit of the starter, before any change:865e04c

Table 1. SonarQube issues in the starter code

| No. | Rule | File:line | Message |
| --- | --- | --- | --- |
|1| S2143| ParcelService.java: Ln 1, Col 0| Use the "java.time" API for date and time|
|2| S1128| ParcelService.java: Ln 6, Col 7| Remove this unused import 'java.util.Date'|
|3| S1068| ParcelService.java: Ln 12, Col 16| Remove this unused "maxParcels" private field.|
|4| S4973| ParcelService.java: Ln 42, Col 51| Strings and Boxed types should be compared using "equals()"|
|5| S2095| ParcelService.java: Ln 76, Col 32| Use try-with-resoruces or close this "FileWriter" in a "finally" clause.|
|6| S108| ParcelService.java: Ln 80, Col 32| Remove this block of code, fill it in, or add a comment explaining why it is empty.| 

## Task 2. AI review of the starter code

| Item | Value |
| --- | --- |
| Date | 25th October 2026 |
| AI tool and exact model | ChatGPT, GPT-6 model|
| Commit reviewed | I mostly test on how to successfully commit file to redirectory in Github|
| How the AI read the files (attached the files, opened the folder, or pasted the files) | Pasted the files as text |
| Output file in the reviews folder | parcelpoint-review.md|

Table 2. All findings on the starter code

| No. | File:line | Finding | Found by (SonarQube, AI or both) | SonarQube rule or course term | Correct? (yes or no, and why) |
| --- | --- | --- | --- | --- | --- |
| 1 | ParcelService.java: line 42 | string compare should be equals() | Found by SonarQube and ChatGPT | S4973 | Correct because == is used for comparing value and not locations in memory|
|2| Main.java: line 10| Input is split on a single space | Found by chatGPT | Code quality| yes, the danger is a case where there are multiple space in string leading to incorrect parsing|
|3| ParcelService.java: line 76| Resources should be close | Found by SonarQube | S2095| yes, due to danger of result leak from improper closing|
|4| ParcelService.java: line 1| Java.time API for date and time| Found by SonarQube | S2143| yes, it is much more suitable for dates and times|
|5| Parcel.java:9| status is a non-private field, contrary to the expected encapsulation of object state.| Found by ChatGPT| Encapsulation| No, this status variable is used locally, making it private will make other class unable to use it

2.1 Name two problems that only the AI review found.
Problem 2,5
2.2 Name one problem that only SonarQube found, or write none.
Problem 3,4
2.3 Name one AI finding that was wrong or too vague, and explain why. If every finding was right, explain how you checked them.
Problem 5, as said before, the variable status must be public so other can use it

## Task 3. Fix and check

Table 3. What you did with each SonarQube issue in Table 1

| No. in Table 1 | Fixed or kept | Commit, or the reason for keeping it |
| --- | --- | --- |
| 1 | Fixed| I remove it as it wans't used at all|
| 2 | Fixed| it was removed because it doesn't do much|
| 3 | Fixed| it was removed as maxparcel barely do anything|
| 4 | Fixed| == is replace with .equals() for string comparison|
| 5 | Fixed| it is replace with try and catch error to successfully close this type writer with no more complexity
| 6 | kept| it suddenly disappear while fixing the code|

Number of SonarQube issues that remain after your fixes: 0

The two design problems that you fixed

| Design problem (course term) | What you changed | Commit |
| --- | --- | --- |
| Interface Segregation |  | commit |
| | | |

Output of the program after your fixes, for the commands `store P1 6501 2`, `pickup P1 5` and `staff`, and the content of parcels.csv:

```text
P1,PICKED_UP
```

## Task 4. AI-generated poor and good designs

| Item | bikeshare-poor | bikeshare-good |
| --- | --- | --- |
| Date | | |
| AI tool and exact model | | |
| Prompt (B or C as given, or your changed prompt in full) | | |
| Builds with mvn package (yes or no) | | |
| Number of classes, interfaces, enums and records | | |
| SonarQube issues, total | | |
| SonarQube issues, by rule | | |
| AI review findings in Check 1 | | |
| AI review findings in Check 2 | | |
| Review output file in the reviews folder | | |

4.1 Did SonarQube report any cohesion or coupling problem in bikeshare-poor? Quote the rule and the message if it did.

4.2 Did the AI review tell the two versions apart? Give one finding for bikeshare-poor that does not appear for bikeshare-good.

4.3 Which version would you rather extend with a new member type, such as a visitor who pays 4 baht per minute, and why?

## Task 5. Reflection

5.1 What does SonarQube check, and what does it not check? Answer with examples from this lab.
It checks the quality of code but it does not alway check the problem that can come when implementing such as using java.time and it leads to more problem that it must be deleted.
5.2 When should you not trust the AI review? Give an example from this lab.
When you actually do what it said and it failed in practice as seen in changing status variable to private in parcel.java 
5.3 What will you do differently in Project Phase 2 after this lab?
I will say I will trust SonarQube as code checker and I will consult AI as quality assurance to have the best outcome for my project phase 2.
## AI usage declaration

| AI tool and exact model | Purpose | Files or parts that it produced or changed | How you checked its output |
| --- | --- | --- | --- |
|ChatGPT GPT-6|Code check in according to Part D and E| ParcelService.java| by follow the instruction of Part E task 3|
