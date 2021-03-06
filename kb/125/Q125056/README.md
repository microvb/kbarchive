---
layout: page
title: "Q125056: INFO: Precision and Accuracy in Floating-Point Calculations"
permalink: /kb/125/Q125056/
---

## Q125056: INFO: Precision and Accuracy in Floating-Point Calculations

{% raw %}

	Article: Q125056
	Product(s): Microsoft Fortran Compiler
	Version(s): 1.0,1.0a,1.5,1.51,2.0,4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbFortranPS kbLangC kbLangFortran kbVC kbVC100 kbVC150 kbVC151 kbVC200 kbVC400 k
	Last Modified: 11-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FORTRAN PowerStation for MS-DOS, versions 1.0, 1.0a 
	- Microsoft Fortran Powerstation 32 for Windows NT, version 1.0 
	- Microsoft Visual C++, versions 1.0, 1.5, 1.51, 2.0, 4.0 
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	There are many situations in which precision, rounding, and accuracy in
	floating-point calculations can work to generate results that are surprising to
	the programmer. There are four general rules that should be followed:
	
	1. In a calculation involving both single and double precision, the result will
	  not usually be any more accurate than single precision. If double precision
	  is required, be certain all terms in the calculation, including constants,
	  are specified in double precision.
	
	2. Never assume that a simple numeric value is accurately represented in the
	  computer. Most floating-point values can't be precisely represented as a
	  finite binary value. For example .1 is .0001100110011... in binary (it
	  repeats forever), so it can't be represented with complete accuracy on a
	  computer using binary arithmetic, which includes all PCs.
	
	3. Never assume that the result is accurate to the last decimal place. There are
	  always small differences between the "true" answer and what can be calculated
	  with the finite precision of any floating point processing unit.
	
	4. Never compare two floating-point values to see if they are equal or not-
	  equal. This is a corollary to rule 3. There are almost always going to be
	  small differences between numbers that "should" be equal. Instead, always
	  check to see if the numbers are nearly equal. In other words, check to see if
	  the difference between them is very small or insignificant.
	
	MORE INFORMATION
	================
	
	In general, the rules described above apply to all languages, including C, C++,
	and assembler. The samples below demonstrate some of the rules using FORTRAN
	PowerStation. All of the samples were compiled using FORTRAN PowerStation 32
	without any options, except for the last one, which is written in C.
	
	Please refer to the FORTRAN manual(s) supplied with Microsoft FORTRAN for a
	description of numeric constants, and article Q36068 for a description of the
	internal representation of floating-point values.
	
	SAMPLE 1
	--------
	
	The first sample demonstrates two things:
	
	- That FORTRAN constants are single precision by default (C constants are
	  double precision by default).
	
	- Calculations that contain any single precision terms are not much more
	  accurate than calculations in which all terms are single precision.
	
	After being initialized with 1.1 (a single precision constant), y is as
	inaccurate as a single precision variable.
	
	  x = 1.100000000000000  y = 1.100000023841858
	
	The result of multiplying a single precision value by an accurate double
	precision value is nearly as bad as multiplying two single precision values.
	Both calculations have thousands of times as much error as multiplying two
	double precision values.
	
	  true = 1.320000000000000 (multiplying 2 double precision values)
	  y    = 1.320000052452087 (multiplying a double and a single)
	  z    = 1.320000081062318 (multiplying 2 single precision values)
	
	Sample Code
	-----------
	
	  C Compile options: none
	
	         real*8 x,y,z
	         x = 1.1D0
	         y = 1.1
	         print *, 'x =',x, 'y =', y
	         y = 1.2 * x
	         z = 1.2 * 1.1
	         print *, x, y, z
	         end
	
	SAMPLE 2
	--------
	
	Sample 2 uses the quadratic equation. It demonstrates that even double precision
	calculations are not perfect, and that the result of a calculation should be
	tested before it is depended on if small errors can have drastic results. The
	input to the square root function in sample 2 is only very slightly negative,
	but it is still invalid. If the double precision calculations did not have
	slight errors, the result would be:
	
	  Root =   -1.1500000000
	
	Instead, it generates the following error:
	
	  run-time error M6201: MATH
	  - sqrt: DOMAIN error
	
	Sample Code
	-----------
	
	  C Compile options: none
	
	         real*8 a,b,c,x,y
	         a=1.0D0
	         b=2.3D0
	         c=1.322D0
	         x = b**2
	         y = 4*a*c
	         print *,x,y,x-y
	         print "(' Root =',F16.10)",(-b+dsqrt(x-y))/(2*a)
	         end
	
	SAMPLE 3
	--------
	
	Sample 3 demonstrates that due to optimizations that occur even if optimization
	is not turned on, values may temporarily retain a higher precision than
	expected, and that it is very unwise to test two floating- point values for
	equality.
	
	In this example, two values are both equal and not equal. At the first IF, the
	value of Z is still on the coprocessor's stack and has the same precision as Y.
	Therefore X does not equal Y and the first message is printed out. At the time
	of the second IF, Z had to be loaded from memory and therefore had the same
	precision and value as X, and the second message also is printed.
	
	Sample Code
	-----------
	
	  C Compile options: none
	
	         real*8 y
	         y=27.1024D0
	         x=27.1024
	         z=y
	         if (x.ne.z) then
	           print *,'X does not equal Z'
	         end if
	         if (x.eq.z) then
	           print *,'X equals Z'
	         end if
	         end
	
	SAMPLE 4
	--------
	
	The first part of sample code 4 calculates the smallest possible difference
	between two numbers close to 1.0. It does this by adding a single bit to the
	binary representation of 1.0.
	
	  x   = 1.00000000000000000  (one bit more than 1.0)
	  y   = 1.00000000000000000  (exactly 1.0)
	  x-y =  .00000000000000022  (smallest possible difference)
	
	Some versions of FORTRAN round the numbers when displaying them so that the
	inherent numerical imprecision is not so obvious. This is why x and y look the
	same when displayed.
	
	The second part of sample code 4 calculates the smallest possible difference
	between 2 numbers close to 10.0. Again, it does this by adding a single bit to
	the binary representation of 10.0. Notice that the difference between numbers
	near 10 is larger than the difference near 1. This demonstrates the general
	principle that the larger the absolute value of a number, the less precisely it
	can be stored in a given number of bits.
	
	  x   = 10.00000000000000000  (one bit more than 10.0)
	  y   = 10.00000000000000000  (exactly 10.0)
	  x-y =   .00000000000000178
	
	The binary representation of these numbers is also displayed to show that they do
	differ by only one bit.
	
	  x = 4024000000000001 Hex
	  y = 4024000000000000 Hex
	
	The last part of sample code 4 shows that simple nonrepeating decimal values
	often can be represented in binary only by a repeating fraction. In this case
	x=1.05, which requires a repeating factor CCCCCCCC....(Hex) in the mantissa. In
	FORTRAN, the last digit "C" is rounded up to "D" in order to maintain the
	highest possible accuracy:
	
	  x = 3FF0CCCCCCCCCCCD (Hex representation of 1.05D0)
	
	Even after rounding, the result is not perfectly accurate. There is some error
	after the least significant digit, which we can see by removing the first
	digit.
	
	  x-1 = .05000000000000004
	
	Sample Code
	-----------
	
	  C Compile options: none
	
	         IMPLICIT real*8 (A-Z)
	         integer*4 i(2)
	         real*8 x,y
	         equivalence (i(1),x)
	
	         x=1.
	         y=x
	         i(1)=i(1)+1
	         print "(1x,'x  =',F20.17,'  y=',f20.17)", x,y
	         print "(1x,'x-y=',F20.17)", x-y
	         print *
	
	         x=10.
	         y=x
	         i(1)=i(1)+1
	         print "(1x,'x  =',F20.17,'  y=',f20.17)", x,y
	         print "(1x,'x-y=',F20.17)", x-y
	         print *
	         print "(1x,'x  =',Z16,' Hex  y=',Z16,' Hex')", x,y
	         print *
	
	         x=1.05D0
	         print "(1x,'x  =',F20.17)", x
	         print "(1x,'x  =',Z16,' Hex')", x
	         x=x-1
	         print "(1x,'x-1=',F20.17)", x
	         print *
	
	         end
	
	SAMPLE 5
	--------
	
	In C, floating constants are doubles by default. Use an "f" to indicate a float
	value, as in "89.95f".
	
	     /* Compile options needed: none
	     */ 
	
	     #include <stdio.h>
	
	     void main()
	     {
	        float floatvar;
	        double doublevar;
	
	     /* Print double constant. */ 
	        printf("89.95 = %f\n", 89.95);      // 89.95 = 89.950000
	
	     /* Printf float constant */ 
	        printf("89.95 = %f\n", 89.95F);     // 89.95 = 89.949997
	
	     /*** Use double constant. ***/ 
	        floatvar = 89.95;
	        doublevar = 89.95;
	
	        printf("89.95 = %f\n", floatvar);   // 89.95 = 89.949997
	        printf("89.95 = %lf\n", doublevar); // 89.95 = 89.950000
	
	     /*** Use float constant. ***/ 
	        floatvar = 89.95f;
	        doublevar = 89.95f;
	
	        printf("89.95 = %f\n", floatvar);   // 89.95 = 89.949997
	        printf("89.95 = %lf\n", doublevar); // 89.95 = 89.949997
	     }
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbFortranPS kbLangC kbLangFortran kbVC kbVC100 kbVC150 kbVC151 kbVC200 kbVC400 kbVC500 kbVC600 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbFortranSearch kbvc150 kbvc100 kbZNotKeyword2 kbZNotKeyword3 kbVC500 kbVC600 kbVC151 kbVC200 kbFORTRANPower32100NT kbFORTRANPower100DOS kbFORTRANPower100aDOS kbVC32bitSearch kbVC500Search
	Version           : :1.0,1.0a,1.5,1.51,2.0,4.0,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
