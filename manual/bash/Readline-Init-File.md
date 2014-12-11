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
<title>Bash Reference Manual: Readline Init File</title>

<meta name="description" content="Bash Reference Manual: Readline Init File">
<meta name="keywords" content="Bash Reference Manual: Readline Init File">
<meta name="resource-type" content="document">
<meta name="distribution" content="global">
<meta name="Generator" content="texi2any">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<link href="index.html#Top" rel="start" title="Top">
<link href="Indexes.html#Indexes" rel="index" title="Indexes">
<link href="index.html#SEC_Contents" rel="contents" title="Table of Contents">
<link href="Command-Line-Editing.html#Command-Line-Editing" rel="up" title="Command Line Editing">
<link href="Readline-Init-File-Syntax.html#Readline-Init-File-Syntax" rel="next" title="Readline Init File Syntax">
<link href="Searching.html#Searching" rel="previous" title="Searching">
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
<a name="Readline-Init-File"></a>
<div class="header">
<p>
Next: <a href="Bindable-Readline-Commands.html#Bindable-Readline-Commands" accesskey="n" rel="next">Bindable Readline Commands</a>, Previous: <a href="Readline-Interaction.html#Readline-Interaction" accesskey="p" rel="previous">Readline Interaction</a>, Up: <a href="Command-Line-Editing.html#Command-Line-Editing" accesskey="u" rel="up">Command Line Editing</a> &nbsp; [<a href="index.html#SEC_Contents" title="Table of contents" rel="contents">Contents</a>][<a href="Indexes.html#Indexes" title="Index" rel="index">Index</a>]</p>
</div>
<hr>
<a name="Readline-Init-File-1"></a>
<h3 class="section">8.3 Readline Init File</h3>
<a name="index-initialization-file_002c-readline"></a>

<p>Although the Readline library comes with a set of Emacs-like
keybindings installed by default, it is possible to use a different set
of keybindings.
Any user can customize programs that use Readline by putting
commands in an <em>inputrc</em> file, conventionally in his home directory.
The name of this
file is taken from the value of the shell variable <code>INPUTRC</code>.  If
that variable is unset, the default is <samp>~/.inputrc</samp>.  If that
file does not exist or cannot be read, the ultimate default is
<samp>/etc/inputrc</samp>.
</p>
<p>When a program which uses the Readline library starts up, the
init file is read, and the key bindings are set.
</p>
<p>In addition, the <code>C-x C-r</code> command re-reads this init file, thus
incorporating any changes that you might have made to it.
</p>
<table class="menu" border="0" cellspacing="0">
<tr><td align="left" valign="top">&bull; <a href="Readline-Init-File-Syntax.html#Readline-Init-File-Syntax" accesskey="1">Readline Init File Syntax</a>:</td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Syntax for the commands in the inputrc file.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
</pre></th></tr><tr><td align="left" valign="top">&bull; <a href="Conditional-Init-Constructs.html#Conditional-Init-Constructs" accesskey="2">Conditional Init Constructs</a>:</td><td>&nbsp;&nbsp;</td><td align="left" valign="top">Conditional key bindings in the inputrc file.
</td></tr>
<tr><th colspan="3" align="left" valign="top"><pre class="menu-comment">
</pre></th></tr><tr><td align="left" valign="top">&bull; <a href="Sample-Init-File.html#Sample-Init-File" accesskey="3">Sample Init File</a>:</td><td>&nbsp;&nbsp;</td><td align="left" valign="top">An example inputrc file.
</td></tr>
</table>




</body>
</html>