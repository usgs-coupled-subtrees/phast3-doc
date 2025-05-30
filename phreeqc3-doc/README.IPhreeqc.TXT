README

        IPhreeqc--Modules Based on the Geochemical Model PHREEQC for Use
                   in Scripting and Programming Languages
        
This file describes how to compile the IPhreeqc library and use
it in C++, C, and Fortran programs. The library may be compiled
after generating either a Visual Studio solution for Windows with 
CMake or a Makefile for Linux with configure. All source and 
compilation-related files are available at the following web site:

http://wwwbrr.cr.usgs.gov/projects/GWC_coupled/phreeqc/index.html.

-----------------------------------------------------------------------------------
TABLE OF CONTENTS
-----------------------------------------------------------------------------------

	A. Distribution file
	B. Documentation
	C. Installing Windows COM versions
	D. Downloading and unzipping the distribution file
	E. Linux compiling, testing, and installing the IPhreeqc library
	F. Windows compiling, testing, and installing the IPhreeqc library
	G. Using the library
	H. Contacts

-----------------------------------------------------------------------------------
A. Distribution file
-----------------------------------------------------------------------------------

	The following distribution packages (containing the software, 
	compilation-related files, and an advection example in
        C++, C, and Fortran) are available for Linux and Windows:

        IPhreeqcCOM-@VERSION@-@REVISION@-win32.msi  Windows
        IPhreeqcCOM-@VERSION@-@REVISION@-x64.msi    Windows
        iphreeqc-@VERSION@-@REVISION@.zip           Windows
        iphreeqc-@VERSION@-@REVISION@.tar.gz        Linux

-----------------------------------------------------------------------------------
B. Documentation
-----------------------------------------------------------------------------------

	Descriptions and examples of IPhreeqc methods for C++, C, and Fortran
	are available in HTML format in the doc directory of the distribution. 

	Charlton, S.R., and Parkhurst, D.L., 2011, Modules based on the geochemical model 
	   PHREEQC for use in scripting and programming languages: Computers & Geosciences,
	   vol. 37, no. 10, p. 1653-1663.

	   *The following two user's guides are available in electronic format. Portable
	   Document Format (PDF) files are included in the doc subdirectory of all
	   PHREEQC program distributions.

	Parkhurst, D.L., and Appelo, C.A.J., 2013, Description of input and examples
	   for PHREEQC version 3--A computer program for speciation, batch-reaction,
	   one- dimensional transport, and inverse geochemical calculations: U.S.
	   Geological Survey Techniques and Methods, book 6, chap. A43, 497 p.
	   http://pubs.usgs.gov/tm/06/a43/.

	Parkhurst, D.L., and Appelo, C.A.J., 1999, User's guide to PHREEQC (Version
	   2)-- A computer program for speciation, batch-reaction, one-dimensional
	   transport, and inverse geochemical calculations: U.S. Geological Survey
	   Water-Resources Investigations Report 99-4259, 312 p.
	   http://pubs.er.usgs.gov/publication/wri994259.

	   *The following two reports document the theory and implementation of
	   isotopes in PHREEQC. Portable Document Format (PDF) of Thorstenson and
	   Parkhurst (2002) is included in the doc subdirectory of the PHREEQC program
	   distribution.

	Thorstenson, D.C., and Parkhurst, D.L., 2002, Calculation of individual isotope
	   equilibrium constants for implementation in geochemical models: U.S.
	   Geological Survey Water-Resources Investigations Report 02-4172, 129 p.
	   http://pubs.er.usgs.gov/publication/wri024172.

	Thorstenson, D.C., and Parkhurst, D.L., 2004, Calculation of individual isotope
	   equilibrium constants for geochemical reactions: Geochimica et Cosmochimica
	   Acta, v. 68, no. 11, p. 2449-2465.

	   *Brief description of the program PhreeqcI.

	Charlton, S.R., and Parkhurst, D.L., 2002, PhreeqcI--A graphical user interface
	   to the geochemical model PHREEQC: U.S. Geological Survey Fact Sheet
	   FS-031-02, 2 p.

-----------------------------------------------------------------------------------
C. Installing Windows COM versions
-----------------------------------------------------------------------------------
	
	For 64-bit computers, download both 32- and 64-bit versions:
	
	IPhreeqcCOM-@VERSION@-@REVISION@-win32.msi  
	IPhreeqcCOM-@VERSION@-@REVISION@-x64.msi    	
	
	Double click on each .msi file and follow the instructions.
	
	IPhreeqcCOM is installed and ready to use for 32- and 64-bit applications.
	
	To test the COM, you can open the Excel file and run the "runphreeqc" macro 
	(view->macros):
	C:\Program Files\USGS\IPhreeqcCOM 3.2.0-9755\examples\com\excel\runphreeqc.xls
	
-----------------------------------------------------------------------------------
D. Downloading and unzipping the distribution file
-----------------------------------------------------------------------------------

	Follow the steps using gunzip, 7zip, or other compression program that can unzip a tar.gz/zip file:

	Steps in extracting files                       Explanation
	----------------------------------------        -----------------------------------
	gunzip iphreeqc-@VERSION@-@REVISION@.tar.gz     Uncompress the tar.gz file.
	tar -xvpof iphreeqc-@VERSION@-@REVISION@.tar    Extract files from the tar file.

	The directory iphreeqc-@VERSION@-@REVISION@ is created when the files are
	extracted; if this directory already exists, you may want to delete or rename
	it before extracting the files. The following directory structure is created 
	(the contents of each directory are shown to the right):

	iphreeqc-@VERSION@-@REVISION@                   Source code and configure/CMake files
	     ./config                                   More configure files
	     ./database                                 Database files for PHREEQC
	     ./doc                                      Documentation files 
	     ./examples                                 Advection example for Fortran, C++, and C
	     ./src                                      Source code for IPhreeqc
	     ./tests                                    Tests that check that C++, C, and Fortran(optional)
                                                        are able to compile, link and run.

	Note:  A compiled executable is not included in the distribution.

-----------------------------------------------------------------------------------
E. Linux compiling, testing, and installing the IPhreeqc library
-----------------------------------------------------------------------------------

	In general, to compile the software, you will need:

		(a) a C++ compiler, and
		(b) knowledge of configure, Make, 
			the compiler, and the Linux operating system.

	A Makefile is generated by configure, and the Makefile is used to
	compile, test, and install the software.

  E.1.  Change directory to the directory that was extracted from the tar file.

        cd iphreeqc-@VERSION@-@REVISION@
        
  E.2.  Make a directory, for example, build.
	
	mkdir build
	
  E.3.  Change directory to build.
	
	cd build

  E.4.  Run configure

	Many of the options for configure can be seen by typing:
    
    	../configure --help
    
	Most common options:
    	--prefix=dir specifies the directory for installation of the
    		library. Default is /usr/local, $HOME would install
    		to your home directory.
    	--enable-fortran-test=yes specifies that you do want to include the Fortran test
    		files during "make check", which compiles, links, and runs programs 
    		that use IPhreeqc.
    		
	Run configure as follows:	
    	
    	../configure [options] 

  E.5.  Compile the IPhreeqc library
	
	make [-j 4]
	
    	Optionally, use -j n--where n is the number of compilations make runs in parallel.
	
  E.6.  Compile and run the test cases. The files in the directory tests are compiled
	and linked to the IPhreeqc library. The Fortran files are optionally included
	(--enable-fortran-test configure option).
	
	make check
	
  E.7.  Install the IPhreeqc library. By default the program is installed in /usr/local/bin
	and /usr/local/share/doc/iphreeqc. Alternatively, the directory defined by --prefix
	in the configure command is used. 
    
    	make install
    	
	The locations of various files are given for default installation (no
	--prefix definition). 
    
	Libraries:
		/usr/local/lib/libiphreeqc.a            (Static library)
		/usr/local/lib/libiphreeqc.so           (Shared object library)
		/usr/local/lib/libiphreeqc.la           (libtool library file)
		    
	Include files:
		C++ and C headers for user's code:
		/usr/local/include/IPhreeqc.h           (C header)
		/usr/local/include/IPhreeqc.hpp         (C++ header)
		
		Optionally, user's code may need one or more of the following:
		/usr/local/include/Var.h                
		/usr/local/include/IPhreeqcCallbacks.h  
		/usr/local/include/Keywords.h
		/usr/local/include/PHRQ_io.h
	
	Documentation:
		/usr/local/share/doc/iphreeqc/IPhreeqc.pdf
		/usr/local/share/doc/iphreeqc/html/index.html (IPhreeqc API)
		/usr/local/share/doc/iphreeqc/RELEASE (Release notes)
		/usr/local/share/doc/iphreeqc/README (this readme file)
		/usr/local/share/doc/iphreeqc/NOTICE (User rights notice)

	Databases: 
		/usr/local/share/doc/iphreeqc/database
			  Amm.dat
			  ColdChem.dat
			  core10.dat
			  frezchem.dat
			  iso.dat
			  llnl.dat
			  minteq.dat
			  minteq.v4.dat
			  phreeqc.dat
			  pitzer.dat
			  sit.dat
			  stimela.dat
			  Tipping_Hurley.dat
			  wateq4f.dat
		
	Advection example for Fortran, C++, and C: 
		/usr/local/share/doc/iphreeqc/examples
		
	Fortran interface
		/usr/local/share/doc/iphreeqc/src/IPhreeqc_interface.F90
			
    
-----------------------------------------------------------------------------------
F. Windows compiling, testing, and installing the IPhreeqc library
-----------------------------------------------------------------------------------

	In general, to compile the IPhreeqc library, you will need:

		(a) CMake (build process manager)
		(b) a C++ compiler,
		(c) familiarity with the compiler and the Windows operating system.
   
  F.1. Download and install CMake

	CMake can be downloaded from http://www.cmake.org/. If you download
	the executable, CMake is installed when you execute it.

  F.2  Generate a Visual Studio solution

	CMake has many options other than Visual Studio, but here we assume
	that you are using some version of Visual Studio. On the first use
	of CMake, it may be necessary to close all Visual Studio instances. 
	
	Open CMake. Fill in the top two lines.
		Where is the source code: 
			The top level directory (ie c:/iphreeqc-@VERSION@-@REVISION@).
		Where to build the binaries: 
			A new directory. It is suggested that the name
			of the directory include the characteristics of 
			the library that is built, including the VS
			version, 32/64 bit, dll/lib.
			for example, vs2012_64_dll.
	
	Click Configure. From the pulldown menu select the 64-bit version 
	for your Visual Studio. Normally, the default radio button should
	be sufficient. Click Finish. 
	
	Options in the top panel:
	(1) BUILD_SHARED_LIBS--If checked, .dll files will be
		created. If not checked, a .lib file will be created.
		Note that .dll files have a .lib file associated with them,
		but it is not the same .lib generated when
		BUILD_SHARED_LIBS is not checked.
	(2) CMAKE_INSTALL_PREFIX--Sets the the install directory where the 
		library and header files will be saved. It is suggested that
		an INSTALL directory be defined inside the directory chosen 
		for the binaries.
	(3) BUILD_CLR_LIBS--If checked, will compile the CLR version of the
	        library. This will enable the charting capabilities of
	        phreeqc through the use of Zedgraph.  This option is only
	        available if BUILD_SHARED_LIBS is checked.
	(4) IPHREEQC_ENABLE_MODULE--Uncheck if you want to
		use the deprecated (old-style) include file (IPhreeqc.f90.inc 
		or IPhreeqc.f.inc) to define IPhreeqc in Fortran files.
		Leave checked to use IPhreeqc as a Fortran module (USE IPhreeqc), 
		which is recommended. Leave checked if not using Fortran. 
	(5) IPHREEQC_FORTRAN_TESTING--Sets whether the test calculations
		(tests directory) will include Fortran test files. A Fortran
		compiler is required. 
	
	Click Configure until the screen is not red. If the screen remains 
	red, you will have to deal with the CMake error messages.
	
	Click Generate.
	
	You should now have a Visual Studio solution file (.sln) in the 
	directory chosen for the binaries (second line of CMake screen). 
	At any point, you can delete the contents of the directory and
	start over. You can make solutions for different Visual Studios,
	or different options in other directories.
	
  F.3. Compile and install IPhreeqc

	Open the Visual Studio solution in the build directory defined in CMake.
	
	The default configuration is "Debug". If you want a release libraries
	(or dlls) and examples,	change the configuration to "Release".

	Build ALL_BUILD. IPhreeqc is compiled.

	Build RUN_TESTS. Programs that test IPhreeqc are compiled and run, 
	and optionally (CMake IPHREEQC_FORTRAN_TESTING option) the Fortran test
	project. 
	

	Build INSTALL. The libraries, header files, Fortran module source
	files, phreeqc database files, and documentation are installed in the
	install directory selected in CMake.

		Install\library directory (lib or dll) may include:
			IPhreeqc.lib       (Release)
			IPhreeqcd.lib      (Debug)
			IPhreeqcmsr.lib    (MinSizeRel)
			IPhreeqcrwdi.lib   (RelWithDebInfo)
			IPhreeqc.dll       (Release Shared)
			IPhreeqcd.dll      (Debug Shared)
			IPhreeqcmsr.dll    (MinSizeRel Shared)
			IPhreeqcrwdi.dll   (RelWithDebInfo Shared)		
			ZedGraph.dll       (CLR/Charting)

		Install\include files:
			C++ and C headers for user's code:	
				IPhreeqc.hpp         (C++ header)
				IPhreeqc.h           (C header)

			Optionally, you may need one or more of the following:
				Var.h                
				IPhreeqcCallbacks.h  
				Keywords.h
				PHRQ_io.h

		Install\src files:
			To use IPhreeqc in Fortran:
				IPhreeqc_interface.F90

		Install\Database files:
			Amm.dat
			frezchem.dat
			iso.dat
			llnl.dat
			minteq.dat
			minteq.v4.dat
			phreeqc.dat
			pitzer.dat
			sit.dat
			stimela.dat
			wateq4f.dat
				
		Install\doc files:
			IPhreeqc.pdf          IPhreeqc journal article
			html\index.html       IPhreeqc API documentation
			NOTICE                User rights notice 
			README                This readme file
			RELEASE               Release notes

		Install\examples files:
			c, cpp, fortran       Advection example


	Note: In order to use the CLR version (Charting) the Zedgraph.dll file
	must be registered either by installing the Phreeqc or the PhreeqcI MSI,
	or through the use of the Visual Studio Tool gacutil.

-----------------------------------------------------------------------------------        			
G. Using the library
-----------------------------------------------------------------------------------

  G.1. C++
     
     In C++, you will include the IPhreeqc.hpp header file and 
     create an IPhreeqc instance:

     #include "IPhreeqc.hpp"
     IPhreeqc iphreeqc;

     or

     IPhreeqc *iphreeqc = new IPhreeqc();

     You will need to link to the IPhreeqc.lib that you installed.

  G.2. C

     In C, you will include the C interface header, IPhreeqc.h, and
     create an IPhreeqc instance.

     #include "IPhreeqc.h"
     int id;
     id = CreateIPhreeqc();

     You will need to link to the IPhreeqc.lib that you installed.

  G.3. Fortran

     In Fortran, you will need to include the source file IPhreeqc_interface.F90
     in your project files. This file defines the IPhreeqc Fortran module.

     USE IPhreeqc
     INTEGER(KIND=4) id
     id = CreateIPhreeqc()

     You will need to link to the IPhreeqc.lib that you installed.

-----------------------------------------------------------------------------------
H. CONTACTS
-----------------------------------------------------------------------------------

Inquiries about this software distribution should be directed to:

e-mail:  h2osoft@usgs.gov or dlpark@usgs.gov

