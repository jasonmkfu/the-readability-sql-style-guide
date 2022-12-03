# SQL Keywords
SQL Keywords such as SELECT, FROM, WHERE, INNER JOIN, LEFT JOIN, ON, etc. should always be in all caps.
<br/>
<span style="color: green"><strong>A. Good</strong></span>
<pre>
1	<mark>SELECT</mark>
2	    T.FieldOne
3	<mark>FROM</mark> Database.Schema.Table <mark>AS</mark> T
4	<mark>WHERE</mark>
5	    T.DateColumn >= '1/1/2000'
</pre>

<span style="color: red"><strong>B. Not So Good</strong></span>
<br/>
<span style="color: red">Keywords not in all caps</span>
<br/>
<pre>
6	<mark>select</mark>
7	    T.FieldOne
8	<mark>From</mark> Database.Schema.Table<mark>as</mark> T
9	<mark>WhErE</mark>
10	    T.DateColumn >= '1/1/2000'
</pre>