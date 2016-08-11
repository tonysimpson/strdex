# strdex
File Index Operation Utility

```
Usage: strdex init [OPTIONS] [(--follow | -f) | (--wait-other | -w)] [--use backend] FILENAME
       strdex add [OPTIONS] [(--follow | -f)] FILENAME INDEX
       strdex remove FILENAME INDEX
       strdex list [--info] [FILENAME]
       strdex query [OPTIONS] [(--follow | -f)] [--index] FILENAME QUERY...
       strdex purge FILENAME
       
options:
      -u / --use BACKEND
      
      strdex provides simple and fast solution to indexing and quering the contents of
      unstructured or structured text files. To use strdex you create an intial mapping
      of your target file using 'strdex init' then you can add and query indexs. Indexs
      are added by piping to 'strdex add' - one line per line in the target file e.g.
        awk '(match($0, "bob", ma); print ma[0];}' somefile | strdex add somefile bob
      to match all the lines with a timestamp key:
        awk '(match($0, "timestamp=([^,]+)", ts); print ts[1];}' somefile | strdex add somefile timestamp
      you can then get all the lines with bob
        strdex query somefile bob
      this will match all none blank lines in the index and print those lines (all lines
      containig the work "bob"). You can also jus the value in the index rather than the
      line:
        strdex query somefile I/bob
      you can also match everything in an index with a regex:
        strdex query somefile I/timetamp/re:05:05
      will print all timestamps with from 05:05:00 to 05:05:59
      including L in the query will put the line at that location e.g.:
        strdex query somefile  bob I/timetamp/re:05:05 L 
      would line the timestamp then the original line then the content of the bob index 
      for each line with a bob.
```

      
       
