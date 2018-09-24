# utl-Fill-in-the-missing-values-with-the-last-non-missing-in-a-group
Fill in the missing values with the last non missing in a group. Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.

    Fill in the missing values with the last non missing in a group

    see
    https://tinyurl.com/y8f87bo2
    https://github.com/rogerjdeangelis/utl-import-excel-workbooks-in-all-folders-and-subfolders

    see stackoverflow
    https://tinyurl.com/y7nnznve
    https://stackoverflow.com/questions/52431904/find-first-non-missing-str-value-in-panel-use-value-to-forward-and-back-fill-b



     WORK.HAVE total obs=12  |  RULES
                             |
                   TICKER_   |  TICKER_
     ID    TIME     HAVE     |   WANT
                             |
     1      1       ABCDE    |   YYYYY   Fill in the missing ticker haves with the last
     1      2                |   YYYYY   nin missing value in the id group
     1      3                |   YYYYY
     1      4       YYYYY    |   YYYYY
     1      5                |   YYYYY

     2      4                |   ZZZZZ
     2      5       ZZZZZ    |   ZZZZZ
     2      6                |   ZZZZZ

     3      1                |

     4      2       OOOOO    |   OOOOO
     4      3       OOOOO    |   OOOOO
     4      4       OOOOO    |   OOOOO


    PROCESS
    =======

    data want;

      do until (last.id);
        set have;
        by id;
        if not missing(ticker_have) then ticker_want=ticker_have;
      end;

      do until (last.id);
        set have;
        by id;
        output;
      end;

    run;quit;


    OUTPUT
    ======

     WORK.WANT total obs=12

                    TICKER_    TICKER_
      ID    TIME     HAVE       WANT

      1      1       ABCDE      YYYYY
      1      2                  YYYYY
      1      3                  YYYYY
      1      4       YYYYY      YYYYY
      1      5                  YYYYY
      2      4                  ZZZZZ
      2      5       ZZZZZ      ZZZZZ
      2      6                  ZZZZZ
      3      1
      4      2       OOOOO      OOOOO
      4      3       OOOOO      OOOOO
      4      4       OOOOO      OOOOO

    *                _              _       _
     _ __ ___   __ _| | _____    __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|

    ;

    data have;
     input id$ time$ ticker_have$;
    cards4;
    1 1 ABCDE
    1 2 .
    1 3 .
    1 4 YYYYY
    1 5 .
    2 4 .
    2 5 ZZZZZ
    2 6 .
    3 1 .
    4 2 OOOOO
    4 3 OOOOO
    4 4 OOOOO
    ;;;;
    run;quit;

