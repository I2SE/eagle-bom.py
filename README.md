eagle-bom.py
============

**This script is a replacement of the eagle ulp that creates a bom.**

It was initially written to fix a problem that eagle had with grouping parts with the same values but different attributes. The UPL did not make two BOM lines out of this scenario. This problem does not exist any more in eagle!

A side effect of using the ULP is that you do not need to have eagle on your machine that generates the releases.

The script is compatible with python 2.7, 3.2 and 3.3

[![Build Status](https://travis-ci.org/I2SE/eagle-bom.py.svg?branch=master)](https://travis-ci.org/I2SE/eagle-bom.py)

You can use eagle-bom.py as follows:
------------------------------------

execute the script: "python eagle-bom.py"

this will give you a usage help as this:
usage: 
	mandatory arguments
	-c / --csv=		 csv where you want to store the BOM
	exclusive mandatory arguments (i.e. choose one of the following)
	-b / --brd=		 eagle board file that you want to use as input for the BOM
	-s / --sch=		 eagle schematic file that you want to use as input for the BOM
	
	optional arguments
	-h / --help		 print this help
	-t / --type=		 specify the type ('value' or 'part' are valid values) of the output csv, default:part
	-v / --variant=		 specify which variant should be used, default is to use the active variant as saved in the board file
	--separator=		 specify the separator that should be used as delimiter between each column in the output csv file, use 'TAB'to specify tabulator as separator
	--notestpads		 excludes all parts that have a attriute 'TP_SIGNAL_NAME' with a value
    --eagleversion       print the version of eagle that was used to generate the board or schematic (only needs arguments for board or schematic, not for csv)
	
	special attributes for EAGLE parts that are interpreted by this script:
		EXCLUDEFROMBOM		parts with this attribute set to a value other than blank will be excluded from the bom
		DO_NOT_PLACE		usually should have the value 'yes' for instructing the manufacturer to leave this part unplaced
		PROVIDED_BY		specify where the manufacturer gets the parts from
		additionally DNP markings from eagle variants are converted to use the DO_NOT_PLACE format
