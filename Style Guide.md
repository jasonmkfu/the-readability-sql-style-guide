# SQL Keywords
SQL Keywords such as SELECT, FROM, WHERE, INNER JOIN, LEFT JOIN, ON, etc. should always be in all caps.
<br/>
<span style="color: green"><strong>A. Good</strong></span>
<pre>
<mark>SELECT</mark>
    CU.Name
<mark>FROM</mark> AlohaCo.Retail.Customer <mark>AS</mark> CU
<mark>WHERE</mark>
    CU.StartDate >= '1/1/2000'
</pre>

<span style="color: red"><strong>B. Not so good</strong></span>
<br/>
<span style="color: red">Keywords not in all caps</span>
<br/>
<pre>
<mark>select</mark>
    CU.Name
<mark>From</mark> AlohaCo.Retail.Customer <mark>as</mark> CU
<mark>WhErE</mark>
    CU.StartDate >= '1/1/2000'
</pre>

# Identation
* Indentation should identify that the code relates to the section it is indented from: for example, the indented lines from a SELECT keyword indicates that the code relates to a SELECT statement.

<span style="color: green"><strong>A. Good</strong></span>
<pre>
SELECT
<mark>    </mark>  CU.Name
<mark>    </mark>, CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress

FROM AlohaCo.Retail.Customer AS CU

WHERE
   CU.StartDate >= '1/1/2000'
</pre>
<span style="color: red"><strong>B. Not so good</strong></span>
<br/>
<span style="color: red">Indentation logic is not used making code harder to read</span>
<pre>
<mark>SE</mark>LECT
<mark>CU</mark>.Name
<mark>,</mark>CU.StartDate
<mark>,</mark>CU.PhoneNumber
,CU.EmailAddress
FROM AlohaCo.Retail.Customer AS CU
WHERE
<mark>CU</mark>.StartDate >= '1/1/2000'
</pre>

# Spaces
* Each section of SQL code should NOT have trailing spaces (trailing spaces are normally not visible unless you highlight multiple rows of text or your text editor settings are set to show spaces/tabs)
* Operators in equations/conditions should have spaces before and after them

<span style="color: green"><strong>A. Good</strong></span>
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

<span style="color: red"><strong>B. Not so good</strong></span>
<br/>
<span style="color: red">Trailing spaces and no space before and after the “>=” operator</span>
<pre>
SELECT
      CU.Name
    , CU.StartDate
    , CU.PhoneNumber
    , CU.EmailAddress<mark>    </mark>

FROM AlohaCo.Retail.Customer AS CU<mark> </mark>

WHERE
    CU.StartDate<mark>>=</mark>'1/1/2000'
</pre>

# Fully Qualified Table/View Names
* Use fully qualified names for tables and views: Database.Schema.TableOrViewName.

<span style="color: green"><strong>A. Good</strong></span>
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

<span style="color: red"><strong>B. Not so good</strong></span>
<pre>
USE AlohaCo;

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
* While other operators may function in a similar manner, only use the six comparison operators listed below.

<span style="color: green"><strong>A. Good</strong></span>
<pre>
=    Equal to
<>   Not equal to
<    Less than
<=   Less than or equal to
>    Greater than
>=   Greater than or equal to
</pre>

<span style="color: red"><strong>B. Not so good</strong></span>
<pre>
!=   Not equal to
!<   Not less than
!>   Not greater than
</pre>

# Comments
Comments can help the reader to understand background information or particular portions of complicated SQL.

* Do not insert comments that are not useful.
* Comments can serve as a way to document changes that have occurred over time.  Use block style comments with "/*" and "*/" for 3 or more lines of comments.  For block comments, the beginning and ending comment clauses should be on separate lines with the text comments set to one indentation between the clauses.

* Use "--" for 1 to 2 lines of comments. A space character should immediately follow the beginning of either a single line or block comment declaration.

<span style="color: green"><strong>A. Good</strong></span>
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

<span style="color: red"><strong>B. Not so good</strong></span>
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
* Use the *** header as a header
    * A 100 character width is used in the example to better fit this document
    * 150 characters is a better real-world width
* Use the --- header as a sub-header
    * A 50 character width is used in the example to better fit this document
    * 100 characters is a better real-world width
* Use two indents (8 spaces) for SQL beneath a header or sub-header for improved legibility

<span style="color: green"><strong>A. Good</strong></span>
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

<span style="color: red"><strong>B. Bad</strong>
<br/>Inconsistent width of header characters, width is too short in the sub-header, and lack of indentation beneath header.
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
* Parentheses must be used when using OR logic

<span style="color: green"><strong>A. Good</strong></span>
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
<span style="color: red"><strong>B. Not so good</strong>
<br/>
No parentheses around OR logic makes the logic ambiguous.
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
* Do not use square brackets unless there are spaces in the database object names or syntax dependent

<span style="color: green"><strong>A. Good</strong></span>
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

<span style="color: red"><strong>B. Not so good</strong>
<br/>
Using brackets when not required.
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


