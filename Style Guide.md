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
<em>Indentation should identify that the code relates to the section it is indented from.</em>
<br/>
For example, the indented lines from a SELECT keyword indicates that the code relates to a SELECT statement.

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