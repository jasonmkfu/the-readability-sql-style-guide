Consequently, the style guide defers to improved legibility and comprehension over space conservation.

# SQL Keywords
Capitalizing SQL keywords allows for easier comprehension by the reader by differentiating it from other SQL that often will be in CamelCase.  Additionally, code editors will often offer SQL syntax highlighting which further assists in comprehension by coloring SQL keywords.
## <span style="color: green">A. Good</span>
* SQL Keywords such as SELECT, FROM, WHERE, INNER JOIN, LEFT JOIN, ON, etc. should always be in all caps
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
Indenting is common practice across all programming languages.  In SQL, it assists the comprehension of the code by the reader by using indentation to associate portions of code to SQL keywords.  While there is debate between indenting using tabs or spaces, spaces are chosen because the width of the indentation will be uniform no matter the environment whereas tabs can vary across environments.  Furthermore, many modern code editors can automatically insert spaces when pressing the TAB key.
## <span style="color: green">A. Good</span>
* Indentation should identify that the code relates to the section it is indented from: for example, the indented lines from a SELECT keyword indicates that the code relates to a SELECT statement
* Each indentation should consist of four (4) space characters
* <em>Note: The bullets in the examples below are used to illustrate the use of spaces and should not be included in the SQL</em>
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
* Indentation logic is not used for fieldnames in the SELECT
* Indentation logic is not used in the WHERE clause
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
* Logical perators in equations/conditions should have spaces before and after them

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
* No space before and after the “>=” operator
* <em>Note: The bullets in the examples below are used to illustrate the use of spaces and should not be included in the SQL</em>
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
Comments can help the reader to understand background information or particular portions of complicated SQL.  Comments can also serve as a way to document changes that have occurred over time by documenting changes occurring on a specific date.
## <span style="color: green">A. Good</span>
* Do not insert comments that are not useful.
* Use block style comments with "/*" and "*/" for 3 or more lines of comments.  For block comments, the beginning and ending comment clauses should be on separate lines with the text comments set to one indentation between the clauses.

* Use "--" for 1 to 2 lines of comments. A space character should immediately follow the beginning of either a single line or block comment declaration.
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
<pre>
<mark>--</mark> Comments that span three or more lines should use block comments
<mark>--</mark> rather than single-line comments.  Using block comments makes
<mark>--</mark> reading long comments easier to read than using single-line
SELECT
      SA.StoreId
    , SA.CategoryId
    , SA.SubCategoryId <mark>-- This is SubCategoryId</mark>

    <mark>--T</mark>his is an example of using single-line comments to provide
    -- further information about the SUM aggregation below
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
* Use the *** header as a header
    * A 100 character width is used in the example to better fit this document
    * 150 characters is a better real-world width
* Use the --- header as a sub-header
    * A 50 character width is used in the example to better fit this document
    * 100 characters is a better real-world width
* Use two indents (8 spaces) for SQL beneath a header or sub-header for improved legibility

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
Similar to evaluating mathematical equations where the order of operations is applied to determine the order to evaluate different portions of the equation, when using multiple, different logical operators, it is important to use parentheses to define the order in which the SQL engine evaluates logical operator comparisons.
## <span style="color: green">A. Good</span>
* Parentheses must be used when using OR logic
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
* No parentheses around OR logic makes the logic ambiguous.
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
Included brackets when they are not needed adds additional visual clutter that decreases legibility.
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
    OR (
        CU.State IS NULL
        AND CU.PhoneNumber LIKE '808-%'
    )
</pre>

## <span style="color: red">B. Not so Good</span>
* Using brackets when not required.
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
    OR (
        CU.State IS NULL
        AND CU.PhoneNumber LIKE '808-%'
    )
</pre>


# New Lines
This is a debatable style requirement, especially for simple queries with only a few fields or tables.  However, the majority of queries will not be simple.  By inserting new lines in-between SQL keyword sections, it assists legibility by using white space to distinguish different sections with the SQL code.
## <span style="color: green">A. Good</span>
* Insert blank lines in-between SQL keyword sections such as FROM, JOINs, WHERE, GROUP BY, ORDER BY, etc.
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
<mark>FROM</mark> AlohaCo.Retail.Customer AS CU
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
Placing the SELECT keyword on its own line helps highlight the beginning of a SELECT statement which helps legibility.
## <span style="color: green">A. Good</span>
* The SELECT keyword is always on a separate line
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
* SELECT and fieldname are on the same line
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
Similar to the reasoning for the SELECT keyword to exist on its own line, the DISTINCT keyword affects the behavior of the SELECT, so including it on the same line as its related SELECT keep related keywords together.
| :warning: WARNING          |
|:---------------------------|
| The use of the DISTINCT keyword should be used sparingly as it can often be an expensive query.|
## <span style="color: green">A. Good</span>
* The DISTINCT keyword should immediately follow and be placed on the same line as the SELECT keyword
* A line break should immediately follow the DISTINCT keyword
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
There is varying opinion regarding leading or trailing commas.  Leading commas are recommended because it is easier to see when adding new fields that you are missing a comma because they are all lined up.  Similarly, opinion on first-field alignment also differs, however, the style guide opts for first field alignment as it makes easier to read the list fields.
## <span style="color: green">A. Good</span>
* Each field should be on its own line with one indent to the right of the clause it is relating to (SELECT, WHERE, GROUP BY, etc.)
* Each subsequent field should utilize leading commas
* One (1) space should immediately follow the comma followed by the field name
* <em>Note: The bullets in the examples below are used to illustrate the use of spaces and should not be included in the SQL</em>
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
Because there is only ever one table/view that follows the FROM keyword, the table/view is placed on the same line rather than on a separate line.
## <span style="color: green">A. Good</span>
* The FROM keyword should include the table name on the same line.  It should NOT be placed on its own line.
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
* The FROM keyword and the table/view are on separate lines
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
The WHERE clause can include one or many predicates.  While it may make sense for instance of one predicate to exist on the same line as the WHERE keyword, because many predicates also can exist, the style guide opts for a consistent rule in the separate line approach.  First-field alignment should not be used because of the varying amounts of indentation that would be needed depending on the use of AND/OR.
## <span style="color: green">A. Good</span>
* The WHERE clause should exist on its own line
* Each logical condition in the WHERE clause should be placed on its own line with appropriate indentation
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
* Predicate should be on a separate line from the WHERE keyword
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
Values in an IN statement should be treated similar to the Multiple Field Listing style with the addition of adding the name equivalent for values that represent an ID or code.  Including the "name" equivalent helps the reader understand what the list represents without having to write another query to determine the "names" of the listed values.
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
