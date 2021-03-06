I wrote two small perl programs/scripts that can convert tables of rust readings into numeric numbers according to published scales. In case of complex readings such as seedling reading ";1242-3+" a double weighting of the first reading was used for mean calculation. For adult plant rust data conversion, a similar double weighting method was proposed by Dr. Matt Rouse (USDA-CDL) and implemented in our programs.

### Note 1: Following the convention in perl, the column numbers are counted from zero, thus, 5,7,9 ... means columns 6,8,10 .....etc.



(1). seedling data conversion 

usage: perl convert_rust_reading.seedling.pl --typo sample_data_seedling/typo.seedling.txt --pheno sample_data_seedling/TCAP_seedling.txt --columns 5,7,9,11,13,15,17

My method differs from the Zhang et al PlosOne 2014 9(7) in the following:
(1) It tolerates unlimited number of segregations in your reading such as ";123-3+422+33333-33-";
(2) It uses all of the information (i.e., not just the first and last reading); it double weighs the first reading and keep the middle ones too.
(3) It is fully automated, all extra spaces, slashes, splitting and mathematic weighting and calculations will be taken care of
(4) It is written in perl; Mac machines (OS X 2002 or later) have perl pre-installed.  So the way you can use it, if you have a Mac, is simply dowload all these attachements into one folder. Open terminal, navigate to  the folder using "cd ~/Downloads/folderGWAS" (replace path with your actual folder path); then type command line. That said, the programs are compatible for Windows files, as long as you know how to access a Linux like system (either local or via SSH), or you know how to install perl in your local Windows machine.

(2). Adult plant rust data conversion


usage : perl convert_rust_reading.field.multiplex.pl --typo sample_data_field/typo.field.txt --pheno sample_data_field/pheno_LrAM381_summary_Liang2015.txt  --columns 3,4,5,6,7

This script is for conversion of multiple traits or the same trait under multiple environments. Usage 2 (just like the seedling phenotype data conversion script) can take practically unlimitted number of columns or readings.

The scales for adult plant rust response types are based on published Stubbs 1986 CIMMYT mannual. The calculation of severity, response and coeficient of infection are similarly double weighted by the first reading. 

The author might consider rewrite the programs in Python, and implement the methods in an R function. If you use this script, or borrowed some of the methods for data conversion or algorithem designs, please cite a publication: "Gao, L., Turner, M. K., Chao S., Kolmer, J. and Anderson J. A. (2016) Genome wide association study of seedling and adult plant leaf rust resistance in elite spring wheat breeding lines. PLoS One 11:e0148671"

####### An equivalent Python  script for seedling data conversion can be accessed here: https://github.com/umngao/misc_Python/blob/master/convert_rust_reading_seedling.py
####### An equivalent Python  script for field data conversion can be accessed here:   https://github.com/umngao/misc_Python/blob/master/convert_rust_reading_field.py

