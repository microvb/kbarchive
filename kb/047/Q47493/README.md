---
layout: page
title: "Q47493: Using the Linker /ALIGN Option"
permalink: /kb/047/Q47493/
---

## Q47493: Using the Linker /ALIGN Option

{% raw %}

	Article: Q47493
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 05-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discusses various considerations regarding the Microsoft Linker and
	its /ALIGN option when it is used to develop applications for the Microsoft
	Windows environment. This information also applies to the development of
	dynamic-link libraries (DLLs) for Windows.
	
	MORE INFORMATION
	================
	
	According to its definition, the Microsoft Linker /ALIGN option "directs the
	linker to align segment data in the executable file along the boundaries
	specified by 'size.'" The "size" parameter is in bytes and must be a power of 2.
	Specifying /ALIGN:16 on the LINK line aligns segments on 16-byte boundaries.
	Making an /ALIGN:16 specification is recommended for Windows-based applications
	and dynamic-link libraries (DLLs) because the default alignment is 512.
	
	When the linker creates an EXE file and /ALIGN:16 is specified, if a segment does
	not end on a 16-byte boundary, the segment is padded with extra bytes. The next
	segment always begins at a 16-byte boundary.
	
	If an application contains several small segments, and no /ALIGN option is
	specified on the Linker command line, each segment will contain a great deal of
	wasted space and the resulting EXE file will be unnecessarily large. The amount
	of wasted space is computed as follows:
	
	     waste = align - (segment modulo align)
	
	Therefore, for a 514-byte segment, an align size of 512 causes 510 bytes to be
	wasted. However, for the same segment, an alignment size of 2 bytes does not
	waste any space.
	
	Problems can arise when the Linker creates a very large EXE file using a small
	align value because the size of the EXE may exceed the range of values that can
	be represented by the EXE header segment table.
	
	To demonstrate the problems that can arise, consider a very large EXE file that
	is linked with an align size of 2. During the process of creating this EXE file,
	the Linker puts segment 42 at file offset 380,000 and records the position in
	the New EXE Segment Table. The format of this table is as follows:
	
	  Offset  Length  Contents
	  ------  ------  --------
	
	     0h      2    Offset of segment relative to beginning of file
	                  after shifting value left by alignment shift count.
	
	     2h      2    Length of segment (0h for segment of 65536 bytes).
	
	     4h      2    Segment flag word.
	
	     6h      2    Minimum allocation size for segment; that is,
	                  amount of space Windows reserves in memory for the
	                  segment (0h for minimum allocation size of 65536
	                  bytes).
	
	In this case, the offset of the segment to place in the table is (380,000
	>> 1) = 190,000, which is too large to store in a 16-bit word (the maximum
	value is 65,535). Therefore, 58,928 (the low-order 16 bits of 190,000) is
	stored. Unfortunately, the Linker does not provide any warning of the data loss
	involved with this step.
	
	When Windows loads segment 42 from the EXE file, it takes the value 58,928 and
	multiplies it by the align size (2), which results in an offset of 117,856 and
	does not lead to the desired segment in the file.
	
	For more information on the new .EXE (New Executable) file header format, see
	appendix K (pages 1488-1497) of the "MS-DOS Encyclopedia" (Microsoft Press).
	Also refer to the article "Liposuction Your Corpulent Executables and Remove
	Excess Fat" by Matt Pietrek in the Microsoft Systems Journal, vol. 8, no. 7,
	July 1993 which describes a sample tool called EXESIZE. Please call the
	publishers (Miller Freeman Inc.) at (800) 666-1084 for order information.
	
	Additional query words: 3.00 3.10
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : WINDOWS:3.0,3.1
	
	=============================================================================
	

{% endraw %}
