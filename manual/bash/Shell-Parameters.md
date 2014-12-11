<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<!-- This text is a brief description of the features that are present in
the Bash shell (version 4.2, 28 December 2010).

This is Edition 4.2, last updated 28 December 2010,
of The GNU Bash Reference Manual,
for Bash, Version 4.2.

Copyright (C) 1988-2011 Free Software Foundation, Inc.

Permission is granted to make and distribute verbatim copies of
this manual provided the copyright notice and this permission notice
are preserved on all copies.

Permission is granted to copy, distribute and/or modify this document
under the terms of the GNU Free Documentation License, Version 1.3 or
any later version published by the Free Software Foundation; with no
Invariant Sections, with the Front-Cover texts being "A GNU Manual",
and with the Back-Cover Texts as in (a) below.  A copy of the license is
included in the section entitled "GNU Free Documentation License".

(a) The FSF's Back-Cover Text is: You are free to copy and modify
this GNU manual.  Buying copies from GNU Press supports the FSF in
developing GNU and promoting software freedom."
 -->
<!-- Created by Texinfo 4.13.90+dev, http://www.gnu.org/software/texinfo/ -->
<head>
<title>Bash Reference Manual: Shell Parameters</title>

<meta name="description" content="Bash Reference Manual: Shell Parameters">
<meta name="keywords" content="Bash Reference Manual: Shell Parameters">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">
<meta name="Generator" content="texi2any">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<link href="index.html#Top" rel="start" title="Top">
<link href="Indexes.html#Indexes" rel="index" title="Indexes">
<link href="index.html#SEC_Contents" rel="contents" title="Table of Contents">
<link href="Basic-Shell-Features.html#Basic-Shell-Features" rel="up" title="Basic Shell Features">
<link href="Positional-Parameters.html#Positional-Parameters" rel="next" title="Positional Parameters">
<link href="Shell-Functions.html#Shell-Functions" rel="previous" title="Shell Functions">
<style type="text/css">
<!--
a.summary-letter {text-decoration: none}
blockquote.smallquotation {font-size: smaller}
div.display {margin-left: 3.2em}
div.example {margin-left: 3.2em}
div.lisp {margin-left: 3.2em}
div.smalldisplay {margin-left: 3.2em}
div.smallexample {margin-left: 3.2em}
div.smalllisp {margin-left: 3.2em}
kbd {font-style:oblique}
pre.display {font-family: serif}
pre.format {font-family: serif}
pre.menu-comment {font-family: serif}
pre.menu-preformatted {font-family: serif}
pre.smalldisplay {font-family: serif; font-size: smaller}
pre.smallexample {font-size: smaller}
pre.smallformat {font-family: serif; font-size: smaller}
pre.smalllisp {font-size: smaller}
span.nocodebreak {white-space:nowrap}
span.nolinebreak {white-space:nowrap}
span.roman {font-family:serif; font-weight:normal}
span.sansserif {font-family:sans-serif; font-weight:normal}
ul.no-bullet {list-style: none}
-->
</style>


</head>

<body lang="en" bgcolor="#FFFFFF" text="#000000" link="#0000FF" vlink="#800080" alink="#FF0000">
<a name="Shell-Parameters"></a>
<div class="header">
<p>
Next: <a href="Shell-Expansions.html#Shell-Expansions" accesskey="n" rel="next">Shell Expansions</a>, Previous: <a href="Shell-Functions.html#Shell-Functions" accesskey="p" rel="previous">Shell Functions</a>, Up: <a href="Basic-Shell-Features.html#Basic-Shell-Features" accesskey="u" rel="up">Basic Shell Features</a> &nbsp; [<a href="index.html#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="Indexes.html#Indexes" title="Index" rel="index">Index</a>]</p>
</div>
<hr>
<a name="Shell-Parameters-1"></a>
<h3 class="section">3.4 Shell Parameters</h3>
<a name="index-parameters"></a>
<a name="index-variable_002c-shell"></a>
<a name="index-shell-variable"></a>

<table class="menu" border="0" cellspacing="0">
<tr><td align="left" valign="top">&bull; <a href="Positional-Parameters.html#Positional-Parameters" accesskey="1">Positional Parameters</a>:</td><td>&nbsp;&nbsp;</td><td align="left" valign="top">The shell&rsquo;s command-line arguments.
</td></tr>
<tr><td align="left" valign="top">&bull; <a href="Special-Parameters.html#Special-Parameters" accesskey="2">Special Parameters</a>:</td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Parameters denoted by special characters.
</td></tr>
</table>

<p>A <var>parameter</var> is an entity that stores values.
It can be a <code>name</code>, a number, or one of the special characters
listed below.
A <var>variable</var> is a parameter denoted by a <code>name</code>.
A variable has a <var>value</var> and zero or more <var>attributes</var>.
Attributes are assigned using the <code>declare</code> builtin command
(see the description of the <code>declare</code> builtin in <a href="Bash-Builtins.html#Bash-Builtins">Bash Builtins</a>).
</p>
<p>A parameter is set if it has been assigned a value.  The null string is
a valid value.  Once a variable is set, it may be unset only by using
the <code>unset</code> builtin command.
</p>
<p>A variable may be assigned to by a statement of the form
</p><div class="example">
<pre class="example"><var>name</var>=[<var>value</var>]
</pre></div>
<p>If <var>value</var>
is not given, the variable is assigned the null string.  All
<var>value</var>s undergo tilde expansion, parameter and variable expansion,
command substitution, arithmetic expansion, and quote
removal (detailed below).  If the variable has its <code>integer</code>
attribute set, then <var>value</var> 
is evaluated as an arithmetic expression even if the <code>$((&hellip;))</code>
expansion is not used (see <a href="Arithmetic-Expansion.html#Arithmetic-Expansion">Arithmetic Expansion</a>).
Word splitting is not performed, with the exception
of <code>&quot;$@&quot;</code> as explained below.
Filename expansion is not performed.
Assignment statements may also appear as arguments to the
<code>alias</code>, 
<code>declare</code>, <code>typeset</code>, <code>export</code>, <code>readonly</code>,
and <code>local</code> builtin commands.
</p>
<p>In the context where an assignment statement is assigning a value  
to a shell variable or array index (see <a href="Arrays.html#Arrays">Arrays</a>), the &lsquo;<samp>+=</samp>&rsquo;
operator can be used to   
append to or add to the variable&rsquo;s previous value.
When &lsquo;<samp>+=</samp>&rsquo; is applied to a variable for which the <var>integer</var> attribute
has been set, <var>value</var> is evaluated as an arithmetic expression and
added to the variable&rsquo;s current value, which is also evaluated.
When &lsquo;<samp>+=</samp>&rsquo; is applied to an array variable using compound assignment
(see <a href="Arrays.html#Arrays">Arrays</a>), the
variable&rsquo;s value is not unset (as it is when using &lsquo;<samp>=</samp>&rsquo;), and new
values are appended to the array beginning at one greater than the array&rsquo;s
maximum index (for indexed arrays),  or added as additional key-value pairs
in an associative array.
When applied to a string-valued variable, <var>value</var> is expanded and
appended to the variable&rsquo;s value.
</p>
<hr>
<div class="header">
<p>
Next: <a href="Shell-Expansions.html#Shell-Expansions" accesskey="n" rel="next">Shell Expansions</a>, Previous: <a href="Shell-Functions.html#Shell-Functions" accesskey="p" rel="previous">Shell Functions</a>, Up: <a href="Basic-Shell-Features.html#Basic-Shell-Features" accesskey="u" rel="up">Basic Shell Features</a> &nbsp; [<a href="index.html#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="Indexes.html#Indexes" title="Index" rel="index">Index</a>]</p>
</div>



</body>
</html>