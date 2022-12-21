Consequently, the style guide defers to improved readability and comprehension over space conservation.

# SQL Keywords
Capitalizing SQL keywords allows for easier comprehension by the reader by differentiating it from other SQL that often will be in CamelCase.  Additionally, code editors will often offer SQL syntax highlighting which further assists in comprehension by coloring SQL keywords.
## <span style="color: green">A. Good</span>
* SQL Keywords such as `SELECT`, `FROM`, `WHERE`, `INNER JOIN`, `LEFT JOIN`, `ON`, etc. should always be in all caps
<pre>
<mark>SELECT</mark>
    CU.Name
<mark>FROM</mark> AlohaCo.Retail.Customer <mark>AS</mark> CU
<mark>WHERE</mark>
    CU.StartDate >= '1/1/2000'
</pre>
## <span style="color: red">B. Not so Good</span>
* Keywords not in all caps
<pre>
<mark>select</mark>
    CU.Name
<mark>From</mark> AlohaCo.Retail.Customer <mark>as</mark> CU
<mark>WhErE</mark>
    CU.StartDate >= '1/1/2000'
</pre>


# Identation and Tabs/Spaces
Indenting is common practice across all programming languages.  In SQL, it assists the comprehension of the code by the reader by using indentation to associate portions of code to SQL keywords.  While there is debate between indenting using tabs or spaces, spaces are chosen because the width of the indentation will be uniform regardless of the environment, whereas tabs can vary across environments.  Furthermore, many modern code editors can automatically insert spaces when pressing the TAB key.
## <span style="color: green">A. Good</span>
* Indentation should identify that the code relates to the section it is indented from, e.g. the indented lines from a `SELECT` keyword indicate that the code relates to a `SELECT` statement
* Each indentation should consist of four (4) space characters
* _Note: The bullet/arrow characters in the examples below are used to illustrate the use of spaces/tabs and should not be included in the SQL_

<pre>
SELECT
<mark>∙∙∙∙</mark>  CU.Name
<mark>∙∙∙∙</mark>, CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Retail.Customer AS CU

WHERE
   CU.StartDate >= '1/1/2000'
</pre>
## <span style="color: red">B. Not so Good</span>
* Indentation logic is not used for fieldnames in the `SELECT`
* Indentation logic is not used in the `WHERE` clause
<pre>
SELECT
<mark>CU</mark>.Name
<mark>,</mark>CU.StartDate
<mark>,</mark>CU.PhoneNumber
,CU.EmailAddress
FROM AlohaCo.Retail.Customer AS CU
WHERE
<mark>CU</mark>.StartDate >= '1/1/2000'
</pre>

## <span style="color: red">C. Not so Good</span>
* Two (2) spaces are used instead of four (4) spaces
* Tab characters are used instead of spaces
<pre>
SELECT
<mark>∙∙</mark>  CU.Name
<mark>∙∙</mark>, CU.StartDate
<mark> →</mark>, CU.PhoneNumber
<mark> →</mark>, CU.EmailAddress

FROM AlohaCo.Retail.Customer AS CU

WHERE
<mark> →</mark>CU.StartDate >= '1/1/2000'
</pre>

# Spaces
Eliminating trailing spaces is good practice to maintain clean code.  Spaces preceding and following logical operations allows for a clear understanding of what is being compared to the left and the right of the operator.
## <span style="color: green">A. Good</span>
* Each section of SQL code should NOT have trailing spaces (trailing spaces are normally not visible unless you highlight multiple rows of text or your text editor settings are set to show spaces/tabs)
* Logical operators in equations/conditions should have spaces before and after them

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

## <span style="color: red">B. Not so Good</span>
* Trailing spaces
* No space before and after the "=" operator
* _Note: The bullet characters in the example below are used to illustrate the use of spaces and should not be included in the SQL_
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress<mark>∙∙∙∙∙</mark>

FROM AlohaCo.Retail.Customer AS CU<mark>∙∙</mark>

WHERE
    CU.StartDate<mark>>=</mark>'1/1/2000'
</pre>


# Fully Qualified Table/View Names
## <span style="color: green">A. Good</span>
* Use fully qualified names for tables and views: Database.Schema.TableOrViewName.
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM <mark>AlohaCo.Retail.Customer</mark> AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>
## <span style="color: red">B. Not so Good</span>
* Employs the `USE` keyword to define the database context instead of using the fully qualified name
<pre>
<mark>USE AlohaCo;</mark>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM <mark>Retail.Customer</mark> AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>


# Comparison Operators
## <span style="color: green">A. Good</span>
* While other operators may function in a similar manner, only use the six comparison operators listed below.
<pre>
=    Equal to
<>   Not equal to
<    Less than
<=   Less than or equal to
>    Greater than
>=   Greater than or equal to
</pre>

## <span style="color: red">B. Not so Good</span>
<pre>
!=   Not equal to
!<   Not less than
!>   Not greater than
</pre>

# Comments
Comments can help the reader to understand background information or particular portions of complicated SQL.  Comments can also serve as a way to document changes that have occurred over time by documenting changes done on a specific date.
## <span style="color: green">A. Good</span>
* Do not insert comments that are not useful
* Use block style comments with `/*` and `*/` for 3 or more lines of comments.  For block comments, the beginning and ending comment clauses should be on separate lines with the text comments set to one indentation between the clauses
* Use `--` for 1 to 2 lines of comments. A space character should immediately follow the beginning of either a single line or block comment declaration
<pre>
<mark>/*</mark>
   Comments that span three or more lines should use block comments
   rather than single-line comments.  Using block comments makes
   reading long comments easier to read than using single-line
   comments.
<mark>*/</mark>

SELECT
      SA.StoreId
    , SA.CategoryId
    , SA.SubCategoryId

    <mark>--</mark> This is an example of usign single-line comments to provide
    <mark>--</mark> further information about the SUM aggregation below
    , SUM(SA.SaleAmount) AS SaleAmountTotal

FROM AlohaCo.Retail.Sale AS SA

WHERE
     SA.SaleDate >= '1/1/2000'
     AND SA.CategoryId IN (
           1 <mark>-- </mark>Shirts
         , 2 <mark>-- </mark>Shorts
         , 3 <mark>-- </mark>Hats
     )

GROUP BY
      SA.StoreId
    , SA.CategoryId
    , SA.SubCategoryId
</pre>

## <span style="color: red">B. Not so Good</span>
* No usage of block comments for comments that span three or more lines
* No space following single line comments

<pre>
<mark>--</mark> Comments that span three or more lines should use block comments
<mark>--</mark> rather than single-line comments.  Using block comments makes
<mark>--</mark> reading long comments easier to read than using single-line
SELECT
      SA.StoreId
    , SA.CategoryId
    , SA.SubCategoryId <mark>-- This is SubCategoryId</mark>

    <mark>--T</mark>his is an example of using single-line comments to provide
    <mar>--f</mark>urther information about the SUM aggregation below
    , SUM(SA.SaleAmount) AS SaleAmountTotal

FROM AlohaCo.Retail.Sale AS SA

WHERE
     SA.SaleDate >= '1/1/2000'
     AND SA.CategoryId IN (
           1 <mark>--S</mark>hirts
         , 2 <mark>--S</mark>horts
         , 3 <mark>--H</mark>ats
     )

GROUP BY
      SA.StoreId
    , SA.CategoryId
    , SA.SubCategoryId
</pre>
# Comment Headers (Optional)
Sometimes it is useful to stylize your comments to indicate different sections of code.  This helps the reader find specific areas of code faster and have a high-level understanding of the different parts of your code.  These stylized comment headers are optional and are provided as a template.

## <span style="color: green">A. Good</span>
* Use the asterisk (`*`) character for headers
    * A 100 character width is used in the example to better fit this document
    * 150 characters is a better real-world width
* Use the hyphen (`-`) character for sub-headers
    * A 50 character width is used in the example to better fit this document
    * 100 characters is a better real-world width
* Use two indents (8 spaces) for SQL beneath a header or sub-header for improved readability

<pre><mark>/*</mark>**************************************************************************************************
<mark>**</mark>  Retail Sales
<mark>**</mark>*************************************************************************************************/

        <mark>--</mark>------------------------------------------------
        <mark>--</mark>  Customer Information
        <mark>--</mark>------------------------------------------------
                SELECT
                      CU.Name
                    , CU.StartDate
                    , CU.PhoneNumber
                    , CU.EmailAddress

                FROM AlohaCo.Retail.Customer AS CU

                WHERE
                    CU.StartDate >= '1/1/2000';

        <mark>--</mark>------------------------------------------------
        <mark>--</mark>  Shirts, Shorts, and Hats
        <mark>--</mark>------------------------------------------------
                SELECT
                      SA.StoreId
                    , SA.CategoryId
                    , SA.SubCategoryId

                    -- This is an example of using single-line comments to provide
                    -- further information about the SUM aggregation below
                    , SUM(SA.SaleAmount) AS SaleAmountTotal

                FROM AlohaCo.Retail.Sale AS SA

                WHERE
                    SA.SaleDate >= '1/1/2000'
                    AND SA.CategoryId IN (
                          1 -- Shirts
                        , 2 -- Shorts
                        , 3 -- Hats
                    )

                GROUP BY
                      SA.StoreId
                    , SA.CategoryId
                    , SA.SubCategoryId;
</pre>

## <span style="color: red">B. Not so Good</span>
* Inconsistent width of header characters
* Width is too short in the sub-header
* Lack of indentation beneath header.
</span>
<pre><mark>/*</mark>**********************
<mark>**</mark>  Retail Sales
<mark>**</mark>********************<mark>*******</mark>**/

        ----------<mark>  </mark>
        --  Customer Information
        ----------<mark>  </mark>
                SELECT
                    CU.Name
                    , CU.StartDate
                    , CU.PhoneNumber
                    , CU.EmailAddress

                FROM AlohaCo.Retail.Customer AS CU

                WHERE
                    CU.StartDate >= '1/1/2000';

<mark>--</mark>------------------------------------------------
<mark>--</mark>  Shirts, Shorts, and Hats
<mark>--</mark>------------------------------------------------
<mark>SE</mark>LECT
        SA.StoreId
    , SA.CategoryId
    , SA.SubCategoryId

    -- This is an example of using single-line comments to provide
    -- further information about the SUM aggregation below
    , SUM(SA.SaleAmount) AS SaleAmountTotal

<mark>FR</mark>OM AlohaCo.Retail.Sale AS SA

<mark>WH</mark>ERE
    SA.SaleDate >= '1/1/2000'
    AND SA.CategoryId IN (
            1 -- Shirts
        , 2 -- Shorts
        , 3 -- Hats
    )

<mark>GR</mark>OUP BY
      SA.StoreId
    , SA.CategoryId
    , SA.SubCategoryId;
</pre>
# Parentheses
Similar to evaluating mathematical equations where the order of operations is applied to determine the equation's evaluation order, when using multiple, different logical operators, it is important to use parentheses to define the order in which the SQL engine evaluates logical operator comparisons.
## <span style="color: green">A. Good</span>
* Parentheses must be used when using `OR` logic
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
    AND CU.State = 'HI'
    <mark>OR (</mark>
        CU.State IS NULL
        AND CU.PhoneNumber LIKE '808-%'
    <mark>)</mark>
</pre>
## <span style="color: red">B. Not so Good</span>
* No parentheses around 1OR1 logic makes the logic ambiguous
</span>
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
    AND CU.State = 'HI'
    <mark>OR</mark> CU.State IS NULL
    AND CU.PhoneNumber LIKE '808-%'
</pre>

# Brackets
Including brackets when they are not needed adds additional visual clutter that decreases readability.
## <span style="color: green">A. Good</span>
* Do not use square brackets unless there are spaces in the database object names or syntax dependent
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress
    , CU.<mark>[</mark>Birth Date<mark>]</mark>

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
    AND CU.State = 'HI'
</pre>

## <span style="color: red">B. Not so Good</span>
* Using brackets when not required
</span>
<pre>
SELECT
      CU.<mark>[</mark>Name<mark>]</mark>
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM <mark>[</mark>AlohaCo<mark>]</mark>.<mark>[</mark>Retail<mark>]</mark>.<mark>[</mark>Customer<mark>]</mark> AS CU

WHERE
    CU.StartDate >= '1/1/2000'
    AND CU.State = 'HI'
</pre>


# New Lines
This is a debatable style requirement, especially for simple queries with only a few fields or tables.  However, the majority of queries will not be simple.  Consequently, by inserting new lines in-between SQL keyword sections, it assists readability by using white space to distinguish different sections of code.
## <span style="color: green">A. Good</span>
* Insert blank lines in-between SQL keyword sections such as `FROM`, `JOIN`, `WHERE`, `GROUP BY`, `ORDER BY`, etc.
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress
    , SUM(SA.SaleAmount) AS SaleAmountTotal
<mark>  </mark>
FROM AlohaCo.Retail.Sale AS SA
<mark>  </mark>
LEFT JOIN AlohaCo.Retail.Customer AS CU
    ON SA.CustomerId = CU.CustomerId
<mark>  </mark>
WHERE
    CU.StartDate >= '1/1/2000'
<mark>  </mark>
GROUP BY
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress
</pre>

## <span style="color: red">B. Not so Good</span>
* No new line between SQL Keyword sections
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress
    , SUM(SA.SaleAmount) AS SaleAmountTotal
<mark>FROM</mark> AlohaCo.Retail.Sale AS SA
<mark>LEFT JOIN</mark> AlohaCo.Retail.Customer AS CU
    ON SA.CustomerId = CU.CustomerId
<mark>WHERE</mark>
    CU.StartDate >= '1/1/2000'
<mark>GROUP BY</mark>
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress
</pre>


# SELECT
Placing the `SELECT` keyword on its own line helps highlight the beginning of a `SELECT` statement which helps readability.
## <span style="color: green">A. Good</span>
* The `SELECT` keyword is always on a separate line
<pre>
<mark>SELECT</mark>
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>

## <span style="color: red">B. Not so Good</span>
* `SELECT` and fieldname are on the same line
<pre>
SELECT <mark>CU.Name</mark>
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>


# DISTINCT
Similar to the reasoning for the `SELECT` keyword to exist on its own line, the `DISTINCT` keyword affects the behavior of the `SELECT`, so including it on the same line as its related `SELECT` keep related keywords together.
| ★ WARNING ★         |
|:---------------------------|
| The use of the `DISTINCT` keyword should be used sparingly as it can often be an expensive query.|
## <span style="color: green">A. Good</span>
* The `DISTINCT` keyword should immediately follow and be placed on the same line as the `SELECT` keyword
* A line break should immediately follow the `DISTINCT` keyword
<pre>
SELECT <mark>DISTINCT</mark>
        CU.State
      , CU.ZipCode

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>

## <span style="color: red">B. Not so Good</span>
* Fieldnames should begin on a separate line
<pre>
SELECT DISTINCT <mark>CU.State</mark>
      , CU.ZipCode

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>

## <span style="color: red">C. Not so Good</span>
* DISTINCT is on its own line
<pre>
SELECT
<mark>DISTINCT</mark>
      CU.State
    , CU.ZipCode

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>


# Multiple Field Listing
There is varying opinion regarding leading or trailing commas.  Leading commas are recommended for this style because it is easier to identify missing commas while adding new fields because they line up vertically.  Similarly, opinion on first-field alignment also differs, however, the style guide opts for first field alignment as it makes easier to read the list of fields.
## <span style="color: green">A. Good</span>
* Each field should be on its own line with one indent to the right of the clause it is relating to (`SELECT`, `WHERE`, `GROUP BY`, etc.)
* Each subsequent field should utilize leading commas
* One (1) space should immediately follow the comma followed by the field name
* _Note: The bullets in the examples below are used to illustrate the use of spaces and should not be included in the SQL_
<pre>
SELECT
    <mark>∙∙</mark>CU.Name
    <mark>, </mark>CU.StartDate
    <mark>, </mark>CU.PhoneNumber
    <mark>, </mark>CU.EmailAddress

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>

## <span style="color: red">B. Not so Good</span>
* Field names not on separate lines
<pre>
SELECT
    CU.Name<mark>, </mark>CU.StartDate<mark>, </mark>CU.PhoneNumber<mark>,</mark> CU.EmailAddress

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>

## <span style="color: red">C. Not so Good</span>
* Trailing commas instead of leading commas
<pre>
SELECT
    CU.Name
    CU.StartDate<mark>,</mark>
    CU.PhoneNumber<mark>,</mark>
    CU.EmailAddress<mark>,</mark>

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>

## <span style="color: red">D. Not so Good</span>
* No space following each comma
* No first-field alignment
<pre>
SELECT
    <mark>CU.Name</mark>
    <mark>,C</mark>U.StartDate
    <mark>,C</mark>U.PhoneNumber
    <mark>,C</mark>U.EmailAddress

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>

## <span style="color: red">E. Not so Good</span>
* Columns not indented
<pre>
SELECT
<mark>  </mark>CU.Name
<mark>, </mark>CU.StartDate
<mark>, </mark>CU.PhoneNumber
<mark>, </mark>CU.EmailAddress

FROM AlohaCo.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>


# FROM
Because there is only ever one table/view that follows the `FROM` keyword, the table/view is placed on the same line rather than on a separate line.
## <span style="color: green">A. Good</span>
* The `FROM` keyword should include the table name on the same line.  It should NOT be placed on its own line.
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

<mark>FROM Aloha</mark>Co.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>

## <span style="color: red">B. Not so Good</span>
* The `FROM` keyword and the table/view are on separate lines
<pre>
SELECT CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

<mark>FROM
    Aloha</mark>Co.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
</pre>


# WHERE
The `WHERE` clause can include one or many predicates.  While it may make sense when there is only one predicate that it exist on the same line as the `WHERE` keyword, because many predicates can also exist, the style guide opts for a consistent rule for all cases and requires the separate lines approach.  First-field alignment should not be used due to the varying indentation that would be required because of the different lengths of `AND` and `OR` keywords.
## <span style="color: green">A. Good</span>
* The `WHERE` clause should exist on its own line
* Each logical condition in the `WHERE` clause should be placed on its own line with appropriate indentation
* Do not apply first-field alignment
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE
<mark>    </mark>CU.StartDate >= '1/1/2000'
<mark>    </mark>AND CU.State = 'HI'
<mark>    </mark>OR (
<mark>    </mark>    CU.State IS NULL
<mark>    </mark>    AND CU.PhoneNumber LIKE '808-%'
<mark>    </mark>)
</pre>

## <span style="color: red">B. Not so Good</span>
* Predicate should be on a separate line from the `WHERE` keyword
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE<mark> </mark>CU.StartDate >= '1/1/2000'
</pre>

## <span style="color: red">C. Not so Good</span>
* Predicates are not on separate lines
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000' <mark>AND</mark> CU.State = 'HI'
    OR (
        CU.State IS NULL
        AND CU.PhoneNumber LIKE '808-%'
    )
</pre>

## <span style="color: red">D. Not so Good</span>
* Do not apply first-field alignment
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE
    <mark>    </mark>CU.StartDate >= '1/1/2000'
    AND CU.State = 'HI'
    OR (
        CU.State IS NULL
        AND CU.PhoneNumber LIKE '808-%'
    )
</pre>

## <span style="color: red">E. Not so Good</span>
* No indentation of predicates in relation to the WHERE keyword
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE
<mark>C</mark>U.StartDate >= '1/1/2000'
<mark>A</mark>ND CU.State = 'HI'
<mark>O</mark>R (
<mark> </mark>   CU.State IS NULL
<mark> </mark>   AND CU.PhoneNumber LIKE '808-%'
<mark>)</mark>
</pre>


# IN
Values in an `IN` statement should be treated similarly to the Multiple Field Listing style with the addition of adding the name equivalent for values that represent an ID or code.  Including the "name" equivalent helps the reader understand what the list represents without having to write another query to determine the "names" of the listed values.
## <span style="color: green">A. Good</span>
* Each field should be on its own line with one indent to the right of the opening parentheses
* Each subsequent field should utilize leading commas
* One (1) space should immediately follow the comma followed by the field name
* For values representing IDs or codes, the "name" equivalent should be included
* The name equivalent should be aligned for all values and begin one space after the longest listed value
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
    AND CU.CustomerLoyaltyCardLevel IN (
    <mark>    </mark>  1  <mark> </mark>-- Bronze
    <mark>    </mark>, 2  <mark> </mark>-- Silver
    <mark>    </mark>, 3  <mark> </mark>-- Gold
    <mark>    </mark>, 202<mark> </mark>-- Platinum
    )
</pre>

## <span style="color: red">B. Not so Good</span>
* Individual values are not on separate lines
* No "name" equivalents included
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
    AND CU.CustomerLoyaltyCardLevel IN (
        <mark>1, 2, 3, 202</mark>
    )
</pre>

## <span style="color: red">C. Not so Good</span>
* List of values does not start on a separate line
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
    AND CU.CustomerLoyaltyCardLevel IN (<mark>1</mark>, 2, 3, 202)
</pre>

## <span style="color: red">D. Not so Good</span>
* "Name" equivalents are not aligned to one space after the right-most value
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
    AND CU.CustomerLoyaltyCardLevel IN (
          1<mark> </mark>-- Bronze
        , 2<mark> </mark>-- Silver
        , 3<mark> </mark>-- Gold
        , 202 -- Platinum
    )
</pre>

## <span style="color: red">E. Not so Good</span>
* List of values are not indented from its parent clause
* Commas should precede each value followed by a space and not after each value
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Database.Retail.Customer AS CU

WHERE
    CU.StartDate >= '1/1/2000'
    AND CU.CustomerLoyaltyCardLevel IN (
<mark>    </mark>1<mark>,</mark>   -- Bronze
<mark>    </mark>2<mark>,</mark>   -- Silver
<mark>    </mark>3<mark>,</mark>   -- Gold
<mark>    </mark>202 -- Platinum
    )
</pre>




# OVER (Window Function)
Window functions can add additional complexity to the `SELECT` statement.  The window function style focuses on improving readability of the window function code and visually separating the window block from surrounding `SELECT` objects.
## <span style="color: green">A. Good</span>
* The `PARTITION BY` keyword immediately follows the OVER clause on its own line and indented
* Field names in the `PARTITION BY` or `ORDER BY` clause should be indented an additional time from the Window function
* Field names in the `PARTITION BY` or `ORDER BY` clause should be on separate line with first-field alignment applied
* The closing parentheses should be on a separate line along with an alias
* The closing parentheses should be indented two spaces to align with the Window Function
* Due to the complexity of window functions, blank lines should both precede and follow each window function

<pre>
SELECT
      SA.StoreId
    , SA.SaleDate
    , SA.CustomerId
    , SA.TransactionId
    , SA.SaleAmount

    , ROW_NUMBER() OVER <mark>(</mark>
    <mark>∙∙∙∙</mark>PARTITION BY
            <mark>∙∙</mark>SA.CustomerId
            , SA.StoreId
            , HA.FinancialClassDSC
    <mark>∙∙∙∙</mark>ORDER BY
              SA.SaleDate ASC
            , SA.TransactionId ASC
    <mark>∙∙</mark>) AS SaleRowNumber

FROM AlohaCo.Retail.Sale AS SA

WHERE
    SA.SaleDate >= '1/1/2000'
    AND SA.SaleDate < '1/1/2001'
</pre>

## <span style="color: red">B. Not so Good</span>
* No carriage returns before and after the window function code
* `PARTITION BY` not on a separate line
* `PARTITION BY` field names not on separate lines line
* Opening parenthesis not on same line as the OVER keyword
* First-field alignment not applied
* `PARTITION BY` and `ORDER BY` not indented
* Closing parenthesis not on its own line
<pre>
SELECT
      SA.StoreId
    , SA.SaleDate
    , SA.CustomerId
    , SA.TransactionId
    , SA.SaleAmount
    , ROW_NUMBER() OVER
    <mark>(</mark>
    <mark>P</mark>ARTITION BY<mark> </mark>SA.CustomerId<mark>, </mark>SA.StoreId<mark>, </mark>HA.FinancialClassDSC
    <mark>O</mark>RDER BY
        <mark>S</mark>A.SaleDate ASC
        , SA.TransactionId ASC<mark>)</mark> AS SaleRowNumber
FROM AlohaCo.Retail.Sale AS SA

WHERE
    SA.SaleDate >= '1/1/2000'
    AND SA.SaleDate < '1/1/2001'
</pre>




# Aliases
## <span style="color: green">A. Good</span>
* Aliases should be applied to fields, `CASE` statements, multiple tables, and sub-queries
* All aliases should use the AS keyword. Do not use the "=" sign in place of the `AS` keyword
* Do not use an alias with a space in it
* Do not use the table alias convention of A, B, C, etc. or some other ordinal structure

| ★ P-SQL Exception ★         |
|:---------------------------|
| In P-SQL you cannot use the AS keyword on tables.  In such cases, simply do not use the AS keyword, but still utilize the `AS` keyword for fieldnames.|

<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress <mark>AS</mark> Email
    , CASE
          WHEN
              SA.CategoryId IN (
                    1 -- Shirts
                  , 4 -- Long-Sleeve Shirts
                  , 4 -- Tank Tops
              )
              THEN 1
          ELSE
              0
      END <mark>AS</mark> ShirtFlag

FROM AlohaCo.Retail.Sale <mark>AS</mark> SA

LEFT JOIN AlohaCo.Retail.Customer <mark>AS</mark> CU
    ON SA.CustomerId = CU.CustomerId

WHERE
    CU.StartDate >= '1/1/2000'

GROUP BY
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress
</pre>
## <span style="color: red">B. Not so Good</span>
* Uses the equal (=) sign to assingn an alias, use `AS`
* Spaces included in the alias name
* `AS` does not precede table/view alias
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , Email <mark>=</mark> CU.EmailAddress
    , ShirtFlag <mark>=</mark>
          CASE
              WHEN
                  "S T".CategoryId IN (
                        1 -- Shirts
                      , 4 -- Long-Sleeve Shirts
                      , 4 -- Tank Tops
                  )
                  THEN 1
              ELSE
                  0
          END

FROM AlohaCo.Retail.Sale AS <mark>"S T"</mark>

LEFT JOIN AlohaCo.Retail.Customer<mark> </mark>CU
    ON "S T".CustomerId = CU.CustomerId

WHERE
    CU.StartDate >= '1/1/2000'

GROUP BY
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress
</pre>

## <span style="color: red">C. Not so Good</span>
* Uses ordinal table aliasing
<pre>
SELECT
      A.Name
    , A.StartDate
    , A.PhoneNumber
    , A.EmailAddress AS Email
    , CASE
          WHEN
              B.CategoryId IN (
                    1 -- Shirts
                  , 4 -- Long-Sleeve Shirts
                  , 4 -- Tank Tops
              )
              THEN 1
          ELSE
              0
      END AS ShirtFlag

FROM AlohaCo.Retail.Sale <mark>AS A</mark>

LEFT JOIN AlohaCo.Retail.Customer <mark>AS B</mark>
    ON A.CustomerId = B.CustomerId

WHERE
    A.StartDate >= '1/1/2000'

GROUP BY
      A.Name
    , A.StartDate
    , A.PhoneNumber
    , A.EmailAddress
</pre>



# Joins
## <span style="color: green">A. Good</span>
* Do not use `OUTER` in the `JOIN` keywords (e.g. `LEFT OUTER JOIN`)
* Do not use the "old" style of joining tables where all tables are listed in the `FROM` statement and then joined in the WHERE statement.
* The join condition (`ON` keyword) should be on a separate line from the table with one indentation.
* If the join has more than one condition to join on, each subsequent condition should align with the `ON`.
* The ordering of the table in the join condition should be: table you are joining from &lt;operator&gt; table you are joining to

<pre>
SELECT
      ST.Name as StoreName
    , IT.Name AS ItemName
    , SA.SaleDate
    , CU.Name AS CustomerName

FROM AlohaCo.Retail.Sale AS SA

LEFT JOIN AlohaCo.Retail.Customer AS CU
    ON SA.CustomerId = CU.CustomerId

LEFT JOIN AlohaCo.Retail.Item AS IT
    ON SA.ItemId = IT.ItemId

LEFT JOIN AlohaCo.Retail.Store AS ST
    ON SA.StoreId = ST.StoreId
    AND Sale.SaleDate >= ST.EffectiveStartDate
    AND Sale.SaleDate <= ST.EffectiveEndDate

WHERE
    CU.StartDate >= '1/1/2000'
</pre>
## <span style="color: red">B. Not so Good</span>
* Including `OUTER` in the `JOIN` statement
* Misaligned join condition
<pre>
SELECT
      ST.Name as StoreName
    , IT.Name AS ItemName
    , SA.SaleDate
    , CU.Name AS CustomerName

FROM AlohaCo.Retail.Sale AS SA

LEFT <mark>OUTER</mark> JOIN AlohaCo.Retail.Customer AS CU
    ON SA.CustomerId = CU.CustomerId

LEFT JOIN AlohaCo.Retail.Item AS IT
    ON SA.ItemId = IT.ItemId

LEFT <mark>OUTER</mark> JOIN AlohaCo.Retail.Store AS ST
<mark>    </mark>ON SA.StoreId = ST.StoreId
<mark>        </mark>AND Sale.SaleDate >= ST.EffectiveStartDate
<mark>        </mark>AND Sale.SaleDate <= ST.EffectiveEndDate

WHERE
    CU.StartDate >= '1/1/2000'
</pre>

## <span style="color: red">C. Not so Good</span>
* Misaligned `JOIN` conditions
* Table ordering in join condition is not table you are joining from <operator> table you are joining to
* First Join condition should immediately follow the `ON` keyword on the same line
<pre>
SELECT
      ST.Name as StoreName
    , IT.Name AS ItemName
    , SA.SaleDate
    , CU.Name AS CustomerName

FROM AlohaCo.Retail.Sale AS SA

LEFT JOIN AlohaCo.Retail.Customer AS CU
    ON <mark>CU</mark>.CustomerId = <mark>SA</mark>.CustomerId

LEFT JOIN AlohaCo.Retail.Item AS IT
    <mark>ON</mark>
        SA.ItemId = IT.ItemId

LEFT JOIN AlohaCo.Retail.Store AS ST
    ON <mark>     </mark>SA.StoreId = ST.StoreId
    <mark>    </mark>AND Sale.SaleDate >= ST.EffectiveStartDate
    <mark>    </mark>AND Sale.SaleDate <= ST.EffectiveEndDate

WHERE
    CU.StartDate >= '1/1/2000'
</pre>
## <span style="color: red">D. Not so Good</span>
* `ON` keyword not indented
* `ON` keyword not on its own line
* Join condition not on its own line
<pre>
SELECT
      ST.Name as StoreName
    , IT.Name AS ItemName
    , SA.SaleDate
    , CU.Name AS CustomerName

FROM AlohaCo.Retail.Sale AS SA

LEFT JOIN AlohaCo.Retail.Customer AS CU
<mark>ON</mark> SA.CustomerId = CU.CustomerId

LEFT JOIN AlohaCo.Retail.Item AS IT <mark>ON</mark> SA.ItemId = IT.ItemId

LEFT JOIN AlohaCo.Retail.Store AS ST
    ON SA.StoreId = ST.StoreId <mark>AND</mark> Sale.SaleDate >= ST.EffectiveStartDate <mark>AND</mark> Sale.SaleDate <= ST.EffectiveEndDate

WHERE
    CU.StartDate >= '1/1/2000'
</pre>

# CTEs and Sub-Queries
## <span style="color: green">A. Good</span>
* The opening parentheses for each CTE should be preceded by a space and immediately follow the name of the CTE, e.g. `WITH CTEName AS (`
* Place the ensuing `SELECT` statement on a new line with one indentation
* Apply all other styles within the CTE as would for any other `SELECT` statement
* Closing parentheses should be on a separate line and align with the CTE’s declaration
* Add comments describing the contents of the CTE immediately preceding each CTE declaration
* Insert a blank line after the end of each CTE, including the last CTE and the beginning of the SELECT statement
<pre>
<mark>-- Determine the first shirt sale for every customer</mark>
WITH FirstShirtSale AS (
    SELECT
          SA.CustomerId
        , MIN(SA.SaleDate) AS FirstSaleDate

    FROM AlohaCo.Retail.Sale AS SA

    WHERE
        SA.CategoryId = 1 -- Shirts

    GROUP BY
        SA.CustomerId
<mark>)</mark>

-- Determine the first sale for every customer (regardless of the item category)
<mark>, </mark>FirstAnySale AS (
    SELECT
          SA.CustomerId
        , MIN(SA.SaleDate) AS FirstSaleDate

    FROM AlohaCo.Retail.Sale AS SA

    GROUP BY
        SA.CustomerId
)

SELECT
      CU.Name AS CustomerName
    , FSS.FirstSaleDate AS FirstShirtSaleDate
    , FAS.FirstSaleDate AS FirstAnySaleDate

FROM AlohaCo.Retail.Customer AS CU

LEFT JOIN FirstShirtSale AS FSS
    ON SA.CustomerId = FSS.CustomerId

LEFT JOIN FirstAnySale AS FAS
    ON SA.CustomerId = FAS.CustomerId

WHERE
    CU.StartDate >= '1/1/2000'
</pre>
## <span style="color: green">B. Good</span>
* Sub-query joins should begin with a space and then a left-parentheses
* Sub-queries should begin on its own line and standard styles applied
<pre>

SELECT
      CU.Name AS CustomerName
    , FSS.FirstSaleDate AS FirstShirtSaleDate

FROM AlohaCo.Retail.Customer AS CU

<mark>-- Determine the first shirts sale for every customer</mark>
LEFT JOIN<mark> (</mark>
    SELECT
          SA.CustomerId
        , MIN(SA.SaleDate) AS FirstSaleDate

    FROM AlohaCo.Retail.Sale AS SA

    WHERE
        SA.CategoryId = 1 -- Shirts

    GROUP BY
        SA.CustomerId
<mark>)</mark> AS FSS
    ON SA.CustomerId = FSS.CustomerId

WHERE
    CU.StartDate >= '1/1/2000'
</pre>
## <span style="color: red">C. Not So Good</span>
* `AS` is on a separate line from the CTE name
* , follows the end of the CTE rather than preceding the next CTE declaration
* No comments explaining the content of each CTE
* Closing parentheses of the CTE is not on its own line
<pre>
<mark> </mark>
WITH FirstShirtSale
<mark>AS (</mark>
    SELECT
          SA.CustomerId
        , MIN(SA.SaleDate) AS FirstSaleDate

    FROM AlohaCo.Retail.Sale AS SA

    WHERE
        SA.CategoryId = 1 -- Shirts

    GROUP BY
        SA.CustomerId
)<mark>,</mark>
<mark> </mark>
FirstAnySale AS (
    SELECT
          SA.CustomerId
        , MIN(SA.SaleDate) AS FirstSaleDate

    FROM AlohaCo.Retail.Sale AS SA

    GROUP BY
        SA.CustomerId<mark>)</mark>

SELECT
      CU.Name AS CustomerName
    , FSS.FirstSaleDate AS FirstShirtSaleDate
    , FAS.FirstSaleDate AS FirstAnySaleDate

FROM AlohaCo.Retail.Customer AS CU

LEFT JOIN FirstShirtSale AS FSS
    ON SA.CustomerId = FSS.CustomerId

LEFT JOIN FirstAnySale AS FAS
    ON SA.CustomerId = FAS.CustomerId

WHERE
    CU.StartDate >= '1/1/2000'
</pre>
## <span style="color: red">B. Not So Good</span>
* Styles not applied to contents of sub-query
<pre>

SELECT
      CU.Name AS CustomerName
    , FSS.FirstSaleDate AS FirstShirtSaleDate

FROM AlohaCo.Retail.Customer AS CU

LEFT JOIN (<mark>SELECT SA.CustomerId, MIN(SA.SaleDate) AS FirstSaleDate FROM AlohaCo.Retail.Sale AS SA WHERE SA.CategoryId = 1 GROUP BY SA.CustomerId</mark>) AS FSS
    ON SA.CustomerId = FSS.CustomerId

WHERE
    CU.StartDate >= '1/1/2000'
</pre>