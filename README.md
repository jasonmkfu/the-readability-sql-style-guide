# The Readability SQL Style Guide

Want to get straight to the good stuff?  Jump to the [guide](https://github.com/jasonmkfu/the-readability-sql-style-guide/blob/main/Style%20Guide.md)!

## Overview
SQL styling varies greatly from person to person.  This style guide defines a single way for all styles and seeks to explain the reasoning behind that choice.  The style guide often chooses readability over efficiency or succinctness, but will sometimes sacrifices readability for the sake of practicality.

The initial intention of the style guide was to provide a standard for the authors' department of SQL writers.  The majority of the SQL writter by the authors centered around data analysis and day-to-day ad hoc SQL query writing.  As such, the aforementioned practicality aspect is pertinent in that the styles chosen must be usable on a day-to-day basis, i.e. stylingc cannot be overly time consuming.

## Acknowledgements
Many thanks to [Sung Yan Micah Chao](https://github.com/smc395) who co-wrote the initial version of this style guide when it lived in a Microsoft Word document.
# Using the Guide
## Consistency
While there are many ways to style SQL code, the number one rule, regardless of style choice, is to remain consistent.  Switching styles throughout a query decreases readability.
## Markdown Reader
The Readability Style Guide is perfectly usable from within Github, however, opening the markdown document in a markdown editor such as Visual Studio Code will allow you to see highlighted sections of SQL that further assists understanding the definition of each style.

_Example from Visual Studio Code:_

![Highlighted SQL Example](/images/HighlightingExample.png)

## Further Discussion Sections
In cases where the choice of the style is very debatable, an additional section is included to further explain the reasoning for the choice of the style.  Readers will most likely still disagree with the provided expplanations, they are included to explain the thought process about the stylechoice.  Finally, the explanations are placed in a drop down section as they are not essential to the style guide, but included for the curious reader.

<details open>
  <summary>Further Discussion</summary>

---

This is an example of a "Further Discussion" section that is already expanded.  In the style guide, these sections are collapsed by default.  Many times, this section will include code blocks to assist in the explanation like the one below.
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>

---
</details>