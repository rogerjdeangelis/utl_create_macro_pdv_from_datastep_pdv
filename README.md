# utl_create_macro_pdv_from_datastep_pdv
Create macro pdv from datastep pdv.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.
    Create macro pdv from datastep pdv

    Related Problem;
      Create a macro pdv corresponding to name='Alice" in sashelp.class
      (related to ops question)

      For related methods to create macro variables see

        github
        https://github.com/rogerjdeangelis/utl_create_many_macro_variables


        Eight techniques

            1. %INPUT
            2. %SYSCALL SET(DSID);
            3. ARRAY MACRO (SEE DO_OVER)
            4. DATASTEP DO_OVER
            5. SQL DO_OVER
            6. DATASTEP AND 60 MACRO VARIABLES

    see
    https://tinyurl.com/ycpoewgg
    https://communities.sas.com/t5/SAS-Programming/Dynamicaly-using-column-names-for-into-statement/m-p/488805


    INPUT
    =====

     SASHELP.CLASS total obs=19

        NAME       SEX    AGE    HEIGHT    WEIGHT |     RULE
                                                  |
        Alfred      M      14     69.0      112.5 |
        Alice       F      13     56.5       84.0 | ==> convert to macro pdv
      ...                                         |


     EXAMPLE OUTPUT
     --------------

     %put &=name  &=sex  &=age  &=height  &=weight;

     NAME=Alice     SEX=F  AGE=13  HEIGHT=56.5  WEIGHT=84



    PROCESS
    -------

    %symdel name sex age height weight; * just in case you rerun;

    %let dsid = %sysfunc(open(sashelp.class(where=(name="Alice")),i));
    %syscall set(dsid);
    %let rc   =%sysfunc(fetchobs(&dsid,1));
    %let rc   =%sysfunc(close(&dsid));

    %put &=name  &=sex  &=age  &=height  &=weight;

    *                _               _       _
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|

    ;

     just use sashelp.class(where=(name="Alice"))


    * see process for sulution;

