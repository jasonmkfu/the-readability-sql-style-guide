# SQL Keywords
SQL Keywords such as SELECT, FROM, WHERE, INNER JOIN, LEFT JOIN, ON, etc. should always be in all caps.
<br/>
<span style="color: green"><strong>A. Good</strong></span>
<pre>
1    <mark>SELECT</mark>
2        TA.FieldOne
3    <mark>FROM</mark> Database.Schema.TableAlpha <mark>AS</mark> TA
4    <mark>WHERE</mark>
5        TA.DateColumn >= '1/1/2000'
</pre>

<span style="color: red"><strong>B. Not so good</strong></span>
<br/>
<span style="color: red">Keywords not in all caps</span>
<br/>
<pre>
6    <mark>select</mark>
7        TA.FieldOne
8    <mark>From</mark> Database.Schema.TableAlpha <mark>as</mark> TA
9    <mark>WhErE</mark>
10        TA.DateColumn >= '1/1/2000'
</pre>

# Identation
* Indentation should identify that the code relates to the section it is indented from: for example, the indented lines from a SELECT keyword indicates that the code relates to a SELECT statement.

<span style="color: green"><strong>A. Good</strong></span>
<pre>
1    SELECT
2    <mark>    </mark>  TA.FieldOne
3    <mark>    </mark>, TA.FieldTwo
4        , TA.FieldThree
5        , TA.FieldFour
6    FROM Database.Schema.TableAlpha AS TA
7    WHERE
8       TA.DateColumn >= '1/1/2000'
</pre>
<span style="color: red"><strong>B. Not so good</strong></span>
<br/>
<span style="color: red">Indentation logic is not used making code harder to read</span>
<pre>
8     <mark>SE</mark>LECT
9     <mark>TA</mark>.FieldOne
10    <mark>,</mark>TA.FieldTwo
11    <mark>,</mark>TA.FieldThree
12    ,TA.FieldFour
13    FROM Database.Schema.TableAlpha AS TA
14    WHERE
15    <mark>TA</mark>.DateColumn >= '1/1/2000'
</pre>

# Spaces
* Each section of SQL code should NOT have trailing spaces (trailing spaces are normally not visible unless you highlight multiple rows of text or your text editor settings are set to show spaces/tabs)
* Operators in equations/conditions should have spaces before and after them

<span style="color: green"><strong>A. Good</strong></span>
<pre>
1    SELECT
2          TA.FieldOne
3        , TA.FieldTwo
4        , TA.FieldThree
5        , TA.FieldFour
6
7    FROM Database.Schema.TableAlpha AS TA
8
9    WHERE
10        TA.DateColumn >= '1/1/2000'
</pre>

<span style="color: red"><strong>B. Not so good</strong></span>
<br/>
<span style="color: red">Trailing spaces and no space before and after the “>=” operator</span>
<pre>
1    SELECT
2          TA.FieldOne
3        , TA.FieldTwo
4        , TA.FieldThree
5        , TA.FieldFour<mark>    </mark>
6
7    FROM Database.Schema.TableAlpha AS TA<mark> </mark>
8
9    WHERE
10        TA.DateColumn<mark>>=</mark>'1/1/2000'
</pre>

# Fully Qualified Table/View Names
* Use fully qualified names for tables and views: Database.Schema.TableOrViewName.

<span style="color: green"><strong>A. Good</strong></span>
<pre>
1    SELECT
2          TA.FieldOne
3        , TA.FieldTwo
4        , TA.FieldThree
5        , TA.FieldFour
6
7    FROM <mark>Database.Schema.TableAlpha</mark> AS TA
8
9    WHERE
10        TA.DateColumn >= '1/1/2000'
</pre>

<span style="color: red"><strong>B. Not so good</strong></span>
<pre>
1    USE Database;
2
3    SELECT
4          TA.FieldOne
5        , TA.FieldTwo
6        , TA.FieldThree
7        , TA.FieldFour
8
9    FROM <mark>Schema.TableAlpha</mark> AS TA
10
11   WHERE
12       TA.DateColumn >= '1/1/2000'
</pre>


# Comparison Operators
* While other operators may function in a similar manner, only use the six comparison operators listed below.

<span style="color: green"><strong>A. Good</strong></span>
<pre>
1    =    Equal to
2    <>   Not equal to
3    <    Less than
4    <=   Less than or equal to
5    >    Greater than
6    >=   Greater than or equal to
</pre>

<span style="color: red"><strong>B. Not so good</strong></span>
<pre>
7    !=   Not equal to
8    !<   Not less than
9    !>   Not greater than
</pre>

# Comments
Comments can help the reader to understand background information or particular portions of complicated SQL.

* Do not insert comments that are not useful.
* Comments can serve as a way to document changes that have occurred over time.  Use block style comments with "/*" and "*/" for 3 or more lines of comments.  For block comments, the beginning and ending comment clauses should be on separate lines with the text comments set to one indentation between the clauses.

* Use "--" for 1 to 2 lines of comments. A space character should immediately follow the beginning of either a single line or block comment declaration.

<span style="color: green"><strong>A. Good</strong></span>
<pre>
1    <mark>/*</mark>
2       Comments that span three or more lines should use block comments
3       rather than single-line comments.  Using block comments makes
4       reading long comments easier to read than using single-line
5       comments.
6    <mark>*/</mark>
7
8    SELECT
9          TA.FieldOne
10       , TA.FieldTwo
11       , TA.FieldThree
12       , TA.FieldFour
13
14       <mark>--</mark> This is an example of usign single-line comments to provide
15       <mark>--</mark> further information about the SUM aggregation below
16       , SUM(TA.FieldFive) AS FieldFiveSum
17
18   FROM Database.Schema.TableAlpha AS TA
19
20   WHERE
21        TA.DateColumn >= '1/1/2000'
22        AND TA.FieldFour IN (
23              1 <mark>-- 1: Alpha</mark>
24            , 2 <mark>-- 2: Beta</mark>
25            , 3 <mark>-- 3: Charlie</mark>
26        )
27
28   GROUP BY
29         TA.FieldOne
30       , TA.FieldTwo
31       , TA.FieldThree
32       , TA.FieldFour
</pre>

<span style="color: red"><strong>B. Not so good</strong></span>
<pre>
1    <mark>--</mark> Comments that span three or more lines should use block comments
2    <mark>--</mark> rather than single-line comments.  Using block comments makes
3    <mark>--</mark> reading long comments easier to read than using single-line
4    <mark>--</mark> comments.
6
7    SELECT
8          TA.FieldOne
9        , TA.FieldTwo
10       , TA.FieldThree
11       , TA.FieldFour <mark>-- This is FieldFour</mark>
12
13       <mark>--T</mark>his is an example of usign single-line comments to provide
14       -- further information about the SUM aggregation below
15       , SUM(TA.FieldFive) AS FieldFiveSum
16
17   FROM Database.Schema.TableAlpha AS TA
18
19   WHERE
20        TA.DateColumn >= '1/1/2000'
21        AND TA.FieldFour IN (
22              1 <mark>--1</mark>: Alpha
23            , 2 <mark>--2</mark>: Beta
24            , 3 <mark>--3</mark>: Charlie
25        )
26
27   GROUP BY
28         TA.FieldOne
29       , TA.FieldTwo
30       , TA.FieldThree
31       , TA.FieldFour
</pre>