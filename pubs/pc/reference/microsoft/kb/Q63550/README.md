---
layout: page
title: "Q63550: Forward Slashes Appear in Paths of Some Error Messages"
permalink: /pubs/pc/reference/microsoft/kb/Q63550/
---

## Q63550: Forward Slashes Appear in Paths of Some Error Messages

	Article: Q63550
	Version(s): 6.00   | 6.00
	Operating System: MS-DOS | OS/2
	Flags: ENDUSER | s_quickc
	Last Modified: 15-AUG-1990
	
	Some errors generated by the Microsoft C Optimizing Compiler version
	6.00, as well as the QuickC Compiler versions 2.50 and 2.51, are
	displayed with forward slashes in the place of backward slashes in the
	error messages.
	
	The following is an example of this type of error message:
	
	   e:/c600/include\malloc.h(79): error C2086: '_bcalloc':
	       redefinition
	
	Note the forward slashes in "/c600/" and the backward slash in
	"\malloc.h".
	
	The forward slashes in these error messages are normal and do not
	cause any problems with the compiler. This behavior is intended.
