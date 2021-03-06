---
layout: page
title: "Q156301: INFO: STL Sample for the partition Function"
permalink: /kb/156/Q156301/
---

## Q156301: INFO: STL Sample for the partition Function

{% raw %}

	Article: Q156301
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): _IK
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Standard C++ Library, used with:
	   - *EDITOR Please do not choose this product*Microsoft Visual C++ 32-bit Edition* use 241, 265, 225, version 4.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The sample code below illustrates how to use the partition, begin, end, and
	bind2nd STL functions in Visual C++.
	
	MORE INFORMATION
	================
	
	Required Header
	---------------
	
	  <algorithm>
	   
	
	Prototype
	---------
	
	     template<class BidirectionalIterator, class Predicate> inline
	     BidirectionalIterator partition(BidirectionalIterator first,
	                                     BidirectionalIterator last,
	                                     Predicate predicate)
	
	NOTE: The class/parameter names in the prototype do not match the version in the
	header file. Some have been modified to improve readability.
	
	Description
	-----------
	
	The partition algorithm arranges elements in the range [first, last) such that
	the elements for which predicate returns true are before the elements for which
	predicate returns false. The algorithm returns an iterator positioned at the
	first element for which predicate returns false.
	
	Sample Code
	-----------
	
	  ////////////////////////////////////////////////////////////////////// 
	  // 
	  // Compile options needed: /GX
	  // 
	  // partition.cpp : Illustrates how to use the partition function.
	  // 
	  // Functions:
	  // 
	  //   partition  - Partition a range using a predicate.
	  // 
	  //   begin      - Returns an iterator that points to the first element
	  //                in a sequence.
	  // 
	  //   end        - Returns an iterator that points one past the end of
	  //                a sequence.
	  // 
	  //   bind2nd    - Returns true for elements for which the condition
	  //                is true.
	  // 
	  // Written by Kalindi Sanghrajka
	  // of Microsoft Product Support Services,
	  // Software Core Developer Support.
	  // Copyright (c) 1996 Microsoft Corporation. All rights reserved.
	  ////////////////////////////////////////////////////////////////////// 
	
	  // disable warning C4786: symbol greater than 255 character,
	  // okay to ignore
	  #pragma warning(disable: 4786)
	
	  #include <iostream>
	  #include <vector>
	  #include <algorithm>
	  #include <functional>
	  using namespace std;
	
	  void main()
	  {
	      const int VECTOR_SIZE = 8 ;
	
	      // Define a template class vector of integers
	      typedef vector<int, allocator<int> > IntVector ;
	
	      //Define an iterator for template class vector of integer
	      typedef IntVector::iterator IntVectorIt ;
	
	      IntVector Numbers(VECTOR_SIZE) ;   //vector containing numbers
	
	      IntVectorIt start, end, it ;
	
	      start = Numbers.begin() ;   // location of first
	                                  // element of Numbers
	
	      end = Numbers.end() ;       // one past the location
	                                  // last element of Numbers
	
	      //Initialize vector Numbers
	      Numbers[0] = 6 ;
	      Numbers[1] = 20 ;
	      Numbers[2] = 10 ;
	      Numbers[3] = 15 ;
	      Numbers[4] = 12 ;
	      Numbers[5] = 7 ;
	      Numbers[6] = 9 ;
	      Numbers[7] = 10 ;
	
	      cout << "Before calling partition" << endl ;
	
	      // print content of Numbers
	      cout << "Numbers { " ;
	      for(it = start; it != end; it++)
	          cout << *it << " " ;
	      cout << " }\n" << endl ;
	
	      // partition the sequence such that all the elements
	      // less than 11 appear before all the elements greater than 11
	      it =  partition(start, end, bind2nd(less<int>(), 11)) ;
	
	      cout << "After calling partition" << endl ;
	
	      // print content of Numbers
	      cout << "Numbers { " ;
	      for(it = start; it != end; it++)
	          cout << *it << " " ;
	      cout << " }\n" << endl ;
	
	  }
	
	Output:
	
	Before calling partition
	Numbers { 6 20 10 15 12 7 9 10 }
	
	After calling partition
	Numbers { 6 10 10 9 7 12 15 20 }
	
	REFERENCES
	==========
	
	Visual C++ Books On Line: Visual C++ Books:C/C++:Standard C++ Library Reference.
	
	Additional query words: STL partition begin end bind2nd
	
	======================================================================
	Keywords          : _IK 
	Technology        : kbVCsearch kbAudDeveloper kbVCLibrary
	Version           : winnt:
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
