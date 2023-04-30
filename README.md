# SalesTrax v0.1.5

---

**Program Name**: SalesTrax  
**Version**: 0.1.5  
**Status**: Prototype  
**Created on**: 2023-04-09  
**Last updated**: 2023-04-28  
**Created with**: Python 3.11.2  
**Author**: Danny Fleenor  
**Contributors**:
- Alex Clark, Fredrik Lundh, Secret Labs AB: `PIL` image processing library
- Anonymous Contributors: Python standard `os` library
- DaedalicEntertainment: `tktooltip` tooltip module
- Danny Fleenor: Program design and development; logo image
- Fredrik Lundh, Guido van Rossum, Steen Lumholt: `tkinter` GUI library
- Georg Brandl: `webbrowser` browser interface library
- Isarra (Wikimedia Commons): Question mark image
- J. D. Hunter: `matplotlib` figure generation library
- Mockaroo LLC: Generation of large mock datasets
- Wes McKinney: `pandas` file import library
- www.aha-soft.com: Shortcut bar images

### Description:  
As a Disclaimer™, I find it worth mentioning that this is a college project begun after only three weeks of learning
Python. In _absolutely_ no way will I claim it is perfect. By choosing to use this program, you accept responsibility
for the fallout of potentially clumsy coding. It is not designed to be harmful, of course, but I cannot attest to
how your system may or may not react to it; I'm not well-versed enough in Python programming to know that.

Having said that, at this time, _SalesTrax_ functions as a simple file merger and data visualizer for tabular
financial documents. It reads CSV, ODS, and Excel documents, removes duplicate records, and provides a framework for
manual record exclusions in the output file, which include CSV, ODS, and XLSX format. Note that any imported
documents should have consistent column ordering between files, but there are no other solid requirements for file
content.

As of update 0.1.2, more than one record can now be selected at once, allowing CTRL and SHIFT clicking for multiple
selection. Clicking on a column header will sort the table using that column as the sort criterion, and the "Hide
Saved," "Hide Temp," "Hide Invalid," and "Hide Deleted" shortcut buttons (along with their respective "View" menu
counterparts) are now functional. Any active sorting or filtering can be reset back to program defaults by pressing
either the "Toggle Filter..." button on the shortcut bar or its counterpart in the "View" menu cascade.

As of update 0.1.3, basic user-defined validation control is now available. By clicking any of the options under the
"Lists" menu cascade, users can enter strings to check for in specific fields, and any record that doesn't have one
of the defined strings will be invalidated, excluding it from export. There is an "Auto-Populate" button for each
field, which will take all the values from the currently loaded records (filter-aware) and fill the listbox with
those values. Individual values can then be deleted from the list to exclude them. Alternatively, this blacklist
functionality can be reversed into a whitelist by only adding those strings that you wish to keep, which can be done
manually with the "Add New Entry" button. This whitelist/blacklist system is meant to be used as a placeholder for
proper filtering algorithms for the time being, as proper filtering is as yet still unimplemented. Note that if a
blacklisted value is added BACK to a validation list, any matching records will become valid again, but they will be
classified as "Temporary" records, regardless of their previous status. I am unsure of how to remedy this. If at any
point, you wish to no longer use validation control for a field, simply delete all the entries in that field's
Validation Control tab, and the entire system will ignore that field in subsequent validation checks.

Update 0.1.4 added individual record editing as well as simple line and bar charts generated by user-defined
datasets. To edit a record, simply double click it in the viewport table, and a popup will allow you to change the
values in that record. Click "Accept" when you're done, and it will update the record instantly! It follows the same
record validation process as every other validation check, so invalid datatypes will be ignored and user-defined
validation controls will be respected, but it won't prevent mathematical miscalculations. I plan to remedy the math
thing soon, though, and there are also plans to add a "New Record" feature for creating entirely new records. The
chart generation features take filters into account and only displays data in saved records, allowing for further
customization of data inclusion. Results are also auto-sorted by the column chosen for the x-axis, so you don't have
to worry about your figures looking all wonky. Some datatype combinations are not yet supported (namely, string
values in the y-axis), but I'll be working to improve that in the next major update. Pie charts, too, are being
finicky, so I'm postponing them for the time being.

0.1.5 was a tiny update that only added a few things. First, there is now a "Total Bar," which keeps accurate sums
for numeric columns. It is filter-aware, too, only summing columns from currently visible records, so it will change
if you hide records with filters. Open Document Spreadsheet compatibility is now fixed, as well. Prior to the 0.1.5
update, the '.ods' format was still available in the import and export lists as a valid format even if you didn't
have the required module to read/write that format, but the program would crash if `odfpy` wasn't installed. Now,
'.ods' won't even appear as a valid file format unless `odfpy` is installed on your system. That's it. Small update,
I know, but I've been meaning to make those features for too long, and I didn't want to put them off any longer.

As mentioned in the last few updates, PROPER filtering will not be available until a later update, but I'm already
developing an algorithm for that in a separate testing file. It's just being difficult. Soon™, though!

### Notes Regarding PyCharm:
When editing this file in PyCharm, the program will raise a total of 33 warnings and 4 light warnings, none of which
are legitimate problems. I've pointed most of them out in comments where they occur, but I thought I should go ahead
and mention them here as well. Most of them stem from PyCharm incorrectly recognizing dictionaries as lists, some
fail to recognize lists as lists, and others warn about direct object references that are intentional. In any case,
all 33 warnings and 4 light warning are illegitimate, and attempting to correct them _will_ break the program (trust
me, I tried it). Just do your best to ignore them, or better yet, view the file in Visual Studio Code, which doesn't
throw any warnings at all.

### Installation:
While SalesTrax itself isn't particularly large, it does have a few hefty dependencies, and none of them are packaged
with the code. To ensure everything required by SalesTrax is installed, simply open a command prompt instance in the
SalesTrax root folder (the one where `main.py` can be found) and run the following line:
```
pip install -U -r requirements.txt
```
Pip will handle the all the heavy lifting from there, installing all of the required dependencies for SalesTrax, and
once it's complete, you can run `main.py`.