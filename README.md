# csv2html
Command line converter from csv to html, written in AWK

 csv2html - creates a html-page (or table only) from csv input, with some nice features
 --------
````
 Usage: csv2html [-h|--Help]             # this information
                 [-V|--Version]          # prints the version of this program
                 [--Copyright]           # prints the copyright of csv2html
                 [-C|--copyrightfooter   # makes a footer with (C) by csv2html
                 [-H|--html-header]      # creates surrounding HTML-Header, Style, Body
                 [-S|--style-only]       # outputs only the build-in CSS-Style
                 [-c|--colorscheme NAME] # choose a coloring ('show' gives the names)
                 [-d|--delim DELIM]      # the delimiter of the csv-file (Default=";")
                 [-e|--empty-line]       # produces empty lines before headerlines
                 [-i|--info-titles]      # title-tags over td with info from the head
                 [-j|--javascript]       # enables highlighting of rows via javascript
                 [-n|--number-lines]     # creates an extra first column with numbering
                 [-r|--rawdata]          # creates anchor to show the rawdata
                 [-s|--sorting]          # Javascript-based sorting in browser, needs n|t
                 [-t|--totals COLS]      # extra row with total of COLS = i[,j].. (if "n")
                 [-u|--uniquecols COLS]  # extra row with number of unique entries in COLS
                 [-x|--extratables COLS] # extra tables with value frequency in COLS
                                         # if "h" after i, headerlines be counted, too
                 [-y|--my-copyright TXT] # creates a footer with specified copyright
                 [--titler TXT]          # text for the titler, if not mentioned in input
                 [--header HEADERTXT]    # text for the header, if not mentioned in input
                 [--format FORMATTXT]    # text for the format, if not mentioned in input
                 [--before TXT]          # text that ist printed before the table
                 [--behind TXT]          # text that ist printed after the table
                 [--warnings]            # Show warnings during processing the input

`********************************************************************************************
 description of input data
 -------------------------
 `- semicolon (DELIM) separated text with optional rows for title, table-head and format
 - TITLER, HEADER or FORMAT must occure as first lines, each can be omitted, also als args
 - TITLER := TITLER;[Texttexttext]
 - HEADER := HEADER;[headercolumn1];[headercolumn2];[headercolumn3]...
 - FORMAT := FORMAT;[l|c|r][b|i][n|t][g][ahref=text%text|aname=text%text];...
          where l=left, c=center, r=right text-align; b=bold, i=italic font;
          n (numeric) and t (text) is needed when 'sorting' is enabled. g for graphic
          default: align left  and font regular. Following must be the last option:
          "ahref" marks this column to be a "A HREF-Link" with the given URL,
            where % is replaced with the data from the column
            e.g.: ahref=https://www.w3.org/wrap.cgi?%?view and data = "foo" gives
            <a href="https://www.w3.org/wrap.cgi?foo?view">foo</a>
          the "aname" tag marks this as an anker in the current document "A ID"
          ahref works only on normal rows, whereas aname works on header and normal lines
 - BEFORE = BEHIND := text is printed before/after the table (ascii/html/pre...) (n-times)
 - one empty line in the rest of the file indicates a following "headerline" (with own CSS)
 - two empty lines indicates a "headerline" in one column (a colspan)

`********************************************************************************************
