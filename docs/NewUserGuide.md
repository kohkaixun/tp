
## **Features**

### Listing all Internships : `list`
Shows the list of all internship entries that you have stored in InternBuddy.

Format: `list`


### Adding an Internship : `add`

Do you have a new internship to track? Add it to InternBuddy using the `add` command.

Format: `add n/COMPANY_NAME r/ROLE s/STATUS d/DATE [c/COMMENT] [t/TAG]...`

* The optional `COMMENT` parameter has a default value of `NA`. This means that if you do not specify any value for it,
  the comment for the newly added internship will be `NA`.
* The optional `TAG` parameter will be empty by default. This means that if you do not specify any value for it, there
  will be no tags associated with the newly added internship.

Examples:
* `add n/Deliveroo r/Software Engineer s/Assessment d/2023-02-01` Adds a new internship entry with
  company name `Deliveroo`, role `Software Engineer`, status `Assessment` and date of technical assessment
  `2023-02-01`.
* `add n/Food Panda r/Web Developer s/New d/2023-02-01 c/I love Food Panda! t/React t/Front-end` Adds a new internship entry
  with company name `Food Panda`, role `Web Developer`, status `New`, deadline of application `2023-02-01`,
  comment `I love Food Panda` and tags `React` and `Front-End`.
* `add n/Food Panda s/new d/2023-02-01` Displays an error because the `ROLE` parameter is missing.


![Add Command](images/ug-add-example.png)
   <p style="text-align: center;">Figure XX: Example of the add command in action</p>

<br/>


### Editing an Internship : `edit`

Made a mistake, or wish to update your internship entry? The `edit` command allows you to make modifications.

Format: `edit INDEX [n/COMPANY_NAME] [r/ROLE] [s/STATUS] [d/DATE] [c/COMMENT] [t/TAG]...`

* Edits the internship whose index number is `INDEX`.
* You have to provide at least one of the optional parameters.
* You can reset the comment of an internship to the default value of `NA` by typing `c/` without specifying any comments after it.
* You can remove all of an internship’s tags by typing `t/` without specifying any other tags after it.


<div markdown="span" class="alert alert-danger">

:warning: **Warning:**  When editing tags, the existing tags of the internship will be removed. For example, if the
internship with index 1 currently has the tags `iOS` and `Swift`, editing the internship via `edit 1 t/macOS` will lead
to the internship only having the tag `macOS`. To have all 3 tags, you need to type `edit 1 t/iOS t/Swift t/macOS`.

</div>

Examples:
* `edit 2 s/Asessment r/Software Developer` Sets the status and role of the second internship entry as `Assessment` and `Software Developer` respectively.
* `edit 2` Displays an error because the command does not satisfy the criteria of having at least one optional parameter.
* `edit 2 t/Java t/Go` Sets the tags of the second internship entry as Java and Go (existing tags will be removed).
* `edit 2 c/` Sets the comment of the second internship entry to be `NA`.
* `edit 2 t/` Removes all the tags of the second internship entry.


![Edit Command](images/ug-edit-example.png)
   <p style="text-align: center;">Figure XX: Example of the edit command in action</p>

<br/>



### Viewing an Internship : `view`
Want to view the details of a specific internship entry? You can do so using the `view` command.

Format: `view INDEX`
* Views the details of the internship entry with index number `INDEX` as indicated in
  the [List Panel](#exploring-the-graphical-user-interface).
* The details will be shown in the [View Panel](#exploring-the-graphical-user-interface).
* Apart from the internship details, a custom tips box is also included in the
  [View Panel](#exploring-the-graphical-user-interface), where the tips change according to the status of the
  internship entry.

Examples:
* `view 1` Assuming that you have at least three internships displayed in the
  [List Panel](#exploring-the-graphical-user-interface), this displays the details of the third internship in the
  [View Panel](#exploring-the-graphical-user-interface).
* `view -1` Displays an error because `INDEX` must be a positive integer.
* `view 8` Assuming that you have 7 internships displayed in the
  [List Panel](#exploring-the-graphical-user-interface), this displays an error because `INDEX` cannot be greater
  than the maximum index shown in the [List Panel](#exploring-the-graphical-user-interface), which is 7 in this case.



![View Command](images/ug-view-example.png)
   <p style="text-align: center;">Figure XX: Example of the view command in action</p>

<br/>

### Copying an Internship to Clipboard : `copy`
[TODO by Chuhao]

### Finding Internships : `find`
Want to locate selected internship entries? Use the `find` command to filter through
your entries and narrow down your search.


Format: `find [n/COMPANY_NAME]... [r/ROLE]... [s/STATUS]... [d/DATE]... [t/TAG]...`

* You have to provide at least one of the optional parameters.
* The `find` command is case-insensitive, and it returns exact matches only. For example,
  `find n/Google Ltd` will not return an entry with company name `Google` because `Google`
  does not exactly match with `Google Ltd`.

There are 2 possible ways for you to use the `find` command.

**Method 1: Use a single parameter type**

e.g., `find s/Applied`, `find s/Applied s/New`, `find n/Google n/Apple n/Meta`

* The `find` command returns all internship entries that match with **any** of the search terms.
* For example, `find s/Applied s/New` returns all internship entries that have a status of **either**
  `Applied` **or** `New`.

  

**Method 2: Use 2 or more different parameter types**

e.g., `find n/Google n/Apple s/New`, `find n/Google n/Apple s/Applied s/New`, `find n/Google r/Engineer t/Python t/Java`

* The `find` command returns all internship entries that matches with **at least one** search term for
  **every** parameter type that is specified.
* For example, `find n/Google n/Apple s/new` returns internship entries that have a status `New` and have
  a company name of `Google` **or** `Apple`.
* Another example is that `find n/Google n/Apple s/Applied s/New` returns internship entries that have company names
  of `Google` **or** `Apple` **and** roles of `Applied` **or** `New`.



![Find Command](images/ug-find-example.png)
   <p style="text-align: center;">Figure XX: Example of the find command in action</p>

### Getting Upcoming Events and Deadlines : `upcoming`
Want to view your upcoming events and deadlines? You can do so using the `upcoming` command.

Format: `upcoming`
* The `upcoming` command provides the list of internships that have events (interviews/assessments) or deadlines (application deadline/offer acceptance deadline) within the upcoming week
* In other words, it gives you the list of internships that have a `STATUS` of `NEW/OFFERED/ASSESSMENT/INTERVIEW`, and the `DATE`  falls within the upcoming week.
* Upcoming week is defined as the current day and the 6 days that follow it.


Examples:
* `upcoming` If today's date is 5 January 2023, it will list all internships that have a `STATUS`of `NEW/OFFERED/ASSESSMENT/INTERVIEW` and `DATE` is from 5 January 2023 to 11 January 2023 inclusive.



### Deleting Internships by Index : `delete-index`
Having multiple internships that you wish to quickly delete using their indices? You can achieve this
via the `delete-index` command.

Format: `delete-index INDEX..`

* Deletes the internship whose index number is `INDEX`.
* If multiple `INDEX` are provided, multiple internships can be deleted.



Examples:
* `delete-index 1` Assuming that you have at least one internship displayed in the
  [List Panel](#exploring-the-graphical-user-interface), this deletes the first
  internship in the [List Panel](#exploring-the-graphical-user-interface).
* `delete-index 1 3` Assuming that you have at least three internships displayed in the
  [List Panel](#exploring-the-graphical-user-interface), this deletes the first and third
  internship in the [List Panel](#exploring-the-graphical-user-interface).
* `delete-index` Displays an error because at least one `INDEX` must be specified.

![Delete Command](images/ug-delete-example.png)
   <p style="text-align: center;">Figure XX: Example of the delete-index command in action</p>



### Deleting Internships by Parameters : `delete-parameter`
Wishing that you could delete internships using parameters instead of indices? You can
certainly do so using `delete-parameter`.

Format: `delete-parameter [n/COMPANY_NAME]... [r/ROLE]... [s/STATUS]... [d/DATE]... [t/TAG]...`

* You have to provide at least one of the optional parameters.
* The `delete` command is case-insensitive, and it deletes entries with exact matches only.
  For example, `delete n/Google Ltd` will not delete an entry with company name `Google` because
  `Google` does not exactly match with `Google Ltd`.

There are 2 possible ways for you to use the `delete` command.

**Method 1: Use a single parameter type**

e.g., `delete-parameter s/Applied`, `delete-parameter s/Applied s/New`,
`delete-parameter n/Google n/Apple n/Meta`

* The `delete-parameter` command deletes all internship entries that match with **any** of the keywords.
* For example, `delete-parameter s/Applied s/New` deletes all internship entries that have a status of **either**
  `Applied` **or** `New`.

  
**Method 2: Use 2 or more different parameter types**

e.g., `delete-parameter n/Google n/Apple s/New`, `delete-parameter n/Google n/Apple s/Applied s/New`,
`delete-parameter n/Google r/Engineer t/Python t/Java`

* The `delete-parameter` command deletes all internship entries that matches with **at least one** keyword for
  **every** parameter type that is specified.
* For example, `delete-parameter n/Google n/Apple s/new` delete internship entries that have a status `New` and have
  a company name of `Google` **or** `Apple`.
* Another example is that `delete-parameter n/Google n/Apple s/Applied s/New` deletes internship entries that have company names
  of `Google` **or** `Apple` **and** roles of `Applied` **or** `New`.




  
### Clearing all Internships : `clear`
The `clear` command deletes all entries permanently from InternBuddy.

Format: `clear`

Example:
![Clear Command](images/ug-clear-example.png)
   <p style="text-align: center;">Figure XX: Example of the clear command in action</p>


### Getting Help : `help`
Forgot the commands for InternBuddy? Fret not! You can easily view the list of supported commands and their formats
using the `help` command.

Format: `help`
* Opens a new window which displays the list of supported commands in InternBuddy, and provides a link to InternBuddy's
  user guide where you can view more detailed information about each command.
* You can click on the <button>Copy URL</button> button to copy the link to your clipboard.


![Help Command](images/ug-help-window.png)
   <p style="text-align: center;">Figure XX: Help Window</p>

<br/>

<div markdown="span" class="alert alert-primary">

:information_source: **Info:** Clicking on the hyperlink in the help window may not work on some Linux
devices as the functionality is dependent on Gnome libraries. If you are using a Linux device and
the hyperlink does not work, you can click on the <Button>Copy URL</Button> button instead.
</div>

### Exiting InternBuddy : `exit`

Done with tracking your internships for the day? Exit InternBuddy using the `exit` command.

Format: `exit`

### Saving your Internship Data

Your internship data for InternBuddy are saved automatically after any command that changes the data. The data are saved
in a file `internbuddy.json` which is located in a subfolder `data` in the [home folder](#quick-start)
where you placed `internbuddy.json`. There is no need to save manually.

<div markdown="span" class="alert alert-primary">

:information_source: **Info:** The file location of `internbuddy.json` is stated in the
<a href="#exploring-the-graphical-user-interface">Location Bar</a> of the GUI.
</div>


### Loading the Data

InternBuddy data is loaded from `internbuddy.json` automatically at the beginning of each run. There is no need to load
manually.
* If `internbuddy.json` is missing, InternBuddy will start with a new data file containing the sample internship
  entries.
* If the content in `internbuddy.json` was altered and as a result has invalid format, InternBuddy will start with an
  empty data file.

<div markdown="span" class="alert alert-danger">

:warning: **Warning:**  Starting with an empty data file means that all internship entries previously stored in
InternBuddy will no longer be present. This is equivalent to a data wipeout. Therefore, we advise against tampering
with the content in `internbuddy.json` unless you are confident in doing so. If you are interested, you can refer to
<a href="#appendix-b--customising-the-data-file">Appendix B</a> for instructions on how to do so.

</div>

<div style="page-break-after: always;"></div>

<br/>