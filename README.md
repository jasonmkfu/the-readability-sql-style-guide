# The Readability SQL Style Guide

Want to get straight to the good stuff?  Jump to the [guide](https://github.com/jasonmkfu/the-readability-sql-style-guide/blob/main/README.md)!

## Overview
SQL styling varies greatly from person to person.  This style guide defines a single way for all styles and seeks to explain the reasoning behind that choice.  The style guide often chooses readability over efficiency or succinctness.
## Acknowledgements

# Using the Guide
## Consistency
While there are many ways to style SQL code, the number one rule, regardless ofstyle choice, is to remain consistent.  Switching styles throughout a query decreases readability.
## Markdown Reader
The Readability Style Guide is perfectly usable from within Github, however, opening the markdown document in a markdown editor such as Visual Studio Code will allow you to see highlighted sections of SQL that further assists understanding the definition of each style.

_Example from Visual Studio Code:_

![Highlighted SQL Example](/images/HighlightingExample.png)

## Further Discussion Sections
In cases where the choice of the style is very debatable, an additional section is included to further explain the reasoning for the choice of the style.  Readers will most likely still disagree with the provided expplanations, they are included to explain the thought process about the stylechoice.  Finally, the explanations are placed in a drop down section as they are not essential to the style guide, but included for the curious reader.
## Approach
### One-to-Many New Line Rule
For lists of fields or conditions, where there can be one to many instances, the list is always started on a new line.  In the example below, the `IN` keyword has one-to-many values, thus the list starts on a new line.
<pre>
CU.CustomerLoyaltyCardLevel IN (
      1   -- Bronze
    , 2   -- Silver
    , 3   -- Gold
    , 202 -- Platinum
)
</pre>
Similarly, for `SELECT` statements, there can be one-to-many fields selected so the list of fields start on a new line.
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU
</pre>
So because the `SELECT` is a one-to-many situation, the default style is to always begin a new line, so you would not do the following example even if there is only one field selected.
<pre>
SELECT CU.Name

FROM AlohaCo.Database.Retail.Customer AS CU
</pre>
The `FROM` keyword on the other hand, is a one-and-only-one SQL keyword and thus the table/view following the `FROM` keyword can remain on the same line.
Note: While old-style joins would make `FROM` a one-to-many keyword, the style guide does not allow old-style joins so it remains a one-and-only-one keyword.
