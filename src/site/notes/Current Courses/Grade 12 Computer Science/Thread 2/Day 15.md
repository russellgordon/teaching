---
{"dg-publish":true,"permalink":"/current-courses/grade-12-computer-science/thread-2/day-15/","dgHomeLink":false}
---

### Thread 2, Day 15 - Friday, February 3, 2023
#### Agenda

1. Musicals @ LCS
	- Populating Relationships in the Musicals @ LCS database
		- We have already populated tables without foreign keys – tables whose data does not depend on other tables
		- Today we will establish relationships, for example:
			- **position-production**
				- For what *production* did a given *person* hold a given *position* and what *classification* was that?
				- For *Chicago*, the person *Kate Bemrose* was a *Lead* and she was a *Student*
			- **role**
				- Which person, holding a *position within a production*, had the role for a given *character*?
				- Kate Bemrose, a *Lead*, played the character *Velma Kelly*
			- **character-group**
				- Which *character* was part of which *group*?
				- The character *Liz* was a member of the *Ensemble*.
			- **musical_number-group**
				- What *musical number* did a given *group* sing?
				- The *Cell Block Girls* sang *Cell Block Tango*.
			- **musical_number-character**
				- What *musical number* did a given character sing?
				- *Velma Kelly* sang in *Cell Block Tango*
		- Teams and assignments are:
			- Logan + Jacobo
				- for Chicago, in order:
					- position-production
					- role
			- Judy + Madison
				- for [Anything Goes](https://docs.google.com/document/d/1u8DaKOsfQ7p33uNOc5KzbLBJOemzJSqxyXfEKpSkOZA/edit), in order:
					- position-production
					- role
			- Lillian + Joyce
				- for [Something's Rotten](https://docs.google.com/document/d/1GOwBHsEO3mGyfcJD1X8iXgf3BpwFYwaCRt484baJljA/edit?usp=drive_web&ouid=111450826756825169792), in order:
					- positon-production
					- role
			- Noah + Amy
				- for Chicago, in order:
					- musical_number-character
					- ==group==
					- <strike>character-group</strike>
					- musical_number-group
				- for [Something's Rotten](https://docs.google.com/document/d/1GOwBHsEO3mGyfcJD1X8iXgf3BpwFYwaCRt484baJljA/edit?usp=drive_web&ouid=111450826756825169792), in order:
					- musical_number-character
					- ==group==
					- <strike>character-group</strike>
					- musical_number-group
			- Jerry + Vincent
				- for [Anything Goes](https://docs.google.com/document/d/1u8DaKOsfQ7p33uNOc5KzbLBJOemzJSqxyXfEKpSkOZA/edit), in order:
					- musical_number-character
					- ==group==
					- <strike>character-group</strike>
					- musical_number-group
				- Additionally, roaming to check in and help with other groups.

#### To-do items

*Before our next class...*

- [ ] Make progress on your [assigned and open issues for our app](https://github.com/lcs-apps/Chicago-HSE-LCS/issues) and use the [[Current Courses/Grade 12 Computer Science/Topics/Source Control/Working on Issues in a Team| usual process of committing, pushing, and creating a pull request]].