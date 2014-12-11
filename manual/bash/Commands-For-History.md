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
<title>Bash Reference Manual: Commands For History</title>

<meta name="description" content="Bash Reference Manual: Commands For History">
<meta name="keywords" content="Bash Reference Manual: Commands For History">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">
<meta name="Generator" content="texi2any">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<link href="index.html#Top" rel="start" title="Top">
<link href="Indexes.html#Indexes" rel="index" title="Indexes">
<link href="index.html#SEC_Contents" rel="contents" title="Table of Contents">
<link href="Bindable-Readline-Commands.html#Bindable-Readline-Commands" rel="up" title="Bindable Readline Commands">
<link href="Commands-For-Text.html#Commands-For-Text" rel="next" title="Commands For Text">
<link href="Commands-For-Moving.html#Commands-For-Moving" rel="previous" title="Commands For Moving">
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
<a name="Commands-For-History"></a>
<div class="header">
<p>
Next: <a href="Commands-For-Text.html#Commands-For-Text" accesskey="n" rel="next">Commands For Text</a>, Previous: <a href="Commands-For-Moving.html#Commands-For-Moving" accesskey="p" rel="previous">Commands For Moving</a>, Up: <a href="Bindable-Readline-Commands.html#Bindable-Readline-Commands" accesskey="u" rel="up">Bindable Readline Commands</a> &nbsp; [<a href="index.html#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="Indexes.html#Indexes" title="Index" rel="index">Index</a>]</p>
</div>
<hr>
<a name="Commands-For-Manipulating-The-History"></a>
<h4 class="subsection">8.4.2 Commands For Manipulating The History</h4>

<dl compact="compact">
<dt><code>accept-line (Newline or Return)</code>
<a name="index-accept_002dline-_0028Newline-or-Return_0029"></a>
</dt>
<dd><p>Accept the line regardless of where the cursor is.
If this line is
non-empty, add it to the history list according to the setting of
the <code>HISTCONTROL</code> and <code>HISTIGNORE</code> variables.
If this line is a modified history line, then restore the history line
to its original state.
</p>
</dd>
<dt><code>previous-history (C-p)</code>
<a name="index-previous_002dhistory-_0028C_002dp_0029"></a>
</dt>
<dd><p>Move &lsquo;back&rsquo; through the history list, fetching the previous command.
</p>
</dd>
<dt><code>next-history (C-n)</code>
<a name="index-next_002dhistory-_0028C_002dn_0029"></a>
</dt>
<dd><p>Move &lsquo;forward&rsquo; through the history list, fetching the next command.
</p>
</dd>
<dt><code>beginning-of-history (M-&lt;)</code>
<a name="index-beginning_002dof_002dhistory-_0028M_002d_003c_0029"></a>
</dt>
<dd><p>Move to the first line in the history.
</p>
</dd>
<dt><code>end-of-history (M-&gt;)</code>
<a name="index-end_002dof_002dhistory-_0028M_002d_003e_0029"></a>
</dt>
<dd><p>Move to the end of the input history, i.e., the line currently
being entered.
</p>
</dd>
<dt><code>reverse-search-history (C-r)</code>
<a name="index-reverse_002dsearch_002dhistory-_0028C_002dr_0029"></a>
</dt>
<dd><p>Search backward starting at the current line and moving &lsquo;up&rsquo; through
the history as necessary.  This is an incremental search.
</p>
</dd>
<dt><code>forward-search-history (C-s)</code>
<a name="index-forward_002dsearch_002dhistory-_0028C_002ds_0029"></a>
</dt>
<dd><p>Search forward starting at the current line and moving &lsquo;down&rsquo; through
the the history as necessary.  This is an incremental search.
</p>
</dd>
<dt><code>non-incremental-reverse-search-history (M-p)</code>
<a name="index-non_002dincremental_002dreverse_002dsearch_002dhistory-_0028M_002dp_0029"></a>
</dt>
<dd><p>Search backward starting at the current line and moving &lsquo;up&rsquo;
through the history as necessary using a non-incremental search
for a string supplied by the user.
</p>
</dd>
<dt><code>non-incremental-forward-search-history (M-n)</code>
<a name="index-non_002dincremental_002dforward_002dsearch_002dhistory-_0028M_002dn_0029"></a>
</dt>
<dd><p>Search forward starting at the current line and moving &lsquo;down&rsquo;
through the the history as necessary using a non-incremental search
for a string supplied by the user.
</p>
</dd>
<dt><code>history-search-forward ()</code>
<a name="index-history_002dsearch_002dforward-_0028_0029"></a>
</dt>
<dd><p>Search forward through the history for the string of characters
between the start of the current line and the point.
This is a non-incremental search.
By default, this command is unbound.
</p>
</dd>
<dt><code>history-search-backward ()</code>
<a name="index-history_002dsearch_002dbackward-_0028_0029"></a>
</dt>
<dd><p>Search backward through the history for the string of characters
between the start of the current line and the point.  This
is a non-incremental search.  By default, this command is unbound.
</p>
</dd>
<dt><code>yank-nth-arg (M-C-y)</code>
<a name="index-yank_002dnth_002darg-_0028M_002dC_002dy_0029"></a>
</dt>
<dd><p>Insert the first argument to the previous command (usually
the second word on the previous line) at point.
With an argument <var>n</var>,
insert the <var>n</var>th word from the previous command (the words
in the previous command begin with word 0).  A negative argument
inserts the <var>n</var>th word from the end of the previous command.
Once the argument <var>n</var> is computed, the argument is extracted
as if the &lsquo;<samp>!<var>n</var></samp>&rsquo; history expansion had been specified.
</p>
</dd>
<dt><code>yank-last-arg (M-. or M-_)</code>
<a name="index-yank_002dlast_002darg-_0028M_002d_002e-or-M_002d_005f_0029"></a>
</dt>
<dd><p>Insert last argument to the previous command (the last word of the
previous history entry).
With a numeric argument, behave exactly like <code>yank-nth-arg</code>.
Successive calls to <code>yank-last-arg</code> move back through the history
list, inserting the last word (or the word specified by the argument to
the first call) of each line in turn.
Any numeric argument supplied to these successive calls determines
the direction to move through the history.  A negative argument switches
the direction through the history (back or forward).
The history expansion facilities are used to extract the last argument,
as if the &lsquo;<samp>!$</samp>&rsquo; history expansion had been specified.
</p>
</dd>
</dl>

<hr>
<div class="header">
<p>
Next: <a href="Commands-For-Text.html#Commands-For-Text" accesskey="n" rel="next">Commands For Text</a>, Previous: <a href="Commands-For-Moving.html#Commands-For-Moving" accesskey="p" rel="previous">Commands For Moving</a>, Up: <a href="Bindable-Readline-Commands.html#Bindable-Readline-Commands" accesskey="u" rel="up">Bindable Readline Commands</a> &nbsp; [<a href="index.html#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="Indexes.html#Indexes" title="Index" rel="index">Index</a>]</p>
</div>



</body>
</html>