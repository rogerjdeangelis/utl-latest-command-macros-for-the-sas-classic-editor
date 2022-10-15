# utl-latest-command-macros-for-the-sas-classic-editor
    %let pgm=utl-latest-command-macros-for-the-sas-classic-editor;

    /*--- The best integrated development environment initially created by the geniuses at the IBM Thomas Watson Reseach Center ---*/

    /*--- None of this works with the WPS World Programming System ---*/

    %macro offPac();

    Win 19 64 SAS 9.4M7 64bit
    Logitech G203 Prodigy 5 Button Gamming Mouse

    Chapters

      1. setup
      2. simple command macros
      3. mouse settings
      4. function key settings
      5. cmd macros


    %let pgm=sas_perpac;

    /*              _
    / |    ___  ___| |_ _   _ _ __
    | |   / __|/ _ \ __| | | | `_ \
    | |_  \__ \  __/ |_| |_| | |_) |
    |_(_) |___/\___|\__|\__,_| .__/
                             |_|
    */

    https://tinyurl.com/tbm73sy6
    https://github.com/rogerjdeangelis/utl-how-to-set-up-the-classic-1980s-classic-editor

    Also

    related GitHub repos
    https://github.com/rogerjdeangelis?tab=repositories&q=classic&type=&language=&sort=

    Youtube
    https://tinyurl.com/ydkjc9w7
    https://www.youtube.com/playlist?list=PLS2pNYD0QwbdHoSnn3p0_xSYDt1y1iDze

    External macros
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories
    /*   _                 _                           _
     ___(_)_ __ ___  _ __ | | ___    ___ _ __ ___   __| |  _ __ ___   __ _  ___ _ __ ___  ___
    / __| | `_ ` _ \| `_ \| |/ _ \  / __| `_ ` _ \ / _` | | `_ ` _ \ / _` |/ __| `__/ _ \/ __|
    \__ \ | | | | | | |_) | |  __/ | (__| | | | | | (_| | | | | | | | (_| | (__| | | (_) \__ \
    |___/_|_| |_| |_| .__/|_|\___|  \___|_| |_| |_|\__,_| |_| |_| |_|\__,_|\___|_|  \___/|___/
                    |_|

    /*--- After setting up the classic 1980s editor try these simple command macros first ---*/
    /* after that try the 44 command macros without settng up the mouse

    /* sum a column of numbers
     _        _
    | |_ ___ | |___   __
    | __/ _ \| __\ \ / /
    | || (_) | |_ \ V /
     \__\___/ \__| \_/

    */
    /*--- sum a column of numbers in the editor ---*

    options comdmac

    /*--- INPUT --*/
    /*--- Hilite a column of numbers and type totv on command line and proc means will run ---*/

    /* editor should look like this
    SAS
    edit fie view tool Solutions Window Help
    Command ---> totv
    00001
    00002  11
    00003  12
    00004  13
    00004  14
    ..

    Hilite the 11 12 13 14

    ---*/

    /*---  PROCESS ---*/

    %macro totv / cmd des="Hilite a column of numbers and an proc means will run";
       store;
       %let rc=%sysfunc(dosubl('
          filename clp clipbrd ;
          data _totv;;
            infile clp;;
            input x;;
          run;quit;;
          proc means data=_totv n sum mean std min q1 median q3 max;;
          run;quit;
          filename clp clear;
          '));
    %mend totv;

    /*--- Command ---> totv ---*/

    /*--- OUTPUT
                                   Analysis Variable : X
                                                            Lower                   Upper
    N         Sum        Mean     Std Dev     Minimum    Quartile      Median    Quartile     Maximum
    -------------------------------------------------------------------------------------------------
    4  50.0000000  12.5000000   1.2909944  11.0000000  11.5000000  12.5000000  13.5000000  14.0000000
    -------------------------------------------------------------------------------------------------

    ---*/
    /*
      _____   ____  __
     / _ \ \ / /\ \/ /
    |  __/\ V /  >  <   rvaluate expression in proram window
     \___| \_/  /_/\_\

    */
    /*--- INPUT ---*/

    /*--- editor should look like this
    SAS
    edit fie view tool Solutions Window Help
    Command ---> totv
    00001
    00002  (11 + 22)*3
    ..

    Hilite (11 + 22)*3

    ---*/

    %macro evx / cmd des="Hilite expression 2*(3+1) and type evx and 8 will appear in log";
       store;
       %let rc = %sysfunc(dosubl('
          filename clp clipbrd ;
          data _null_;
            infile clp ;
            input;
            put _infile_;
            call symputx("__evl",_infile_);
          run;quit;
          data _null_;
            result=&__evl;
            put result=;
          run;quit;
          filename clp clear ;
       '));
    %mend evx;

    /*--- OUTPUT IN LOG ---*/

    SYMBOLGEN:  Macro variable __EVL resolves to (11 + 22)*3
    RESULT=99


    /*
     ___ _   _ _ __ _____   __
    / __| | | | `_ ` _ \ \ / /
    \__ \ |_| | | | | | \ V /
    |___/\__,_|_| |_| |_|\_/

    */

    %macro totv / cmd des="Hilite a column of numbers and an proc means will run";
       store;
       %let rc=%sysfunc(dosubl('
          filename clp clipbrd
          data _totv;
            infile clp;
            input x;
          run;quit;
          proc means data=_totv n sum mean std min q1 median q3 max;
          run;quit
          '));
    %mend totv;


    WPS (WORLD PROGRAMMING SYSTEM) DOES NOT SUPPORT COMMAND MACROS.

    Note you do not need to use function keys or mouse buttons, instead you can use the command line only.

    /*____                                              _   _   _
    |___ /    _ __ ___   ___  _   _ ___  ___   ___  ___| |_| |_(_)_ __   __ _ ___
      |_ \   | `_ ` _ \ / _ \| | | / __|/ _ \ / __|/ _ \ __| __| | `_ \ / _` / __|
     ___) |  | | | | | | (_) | |_| \__ \  __/ \__ \  __/ |_| |_| | | | | (_| \__ \
    |____(_) |_| |_| |_|\___/ \__,_|___/\___| |___/\___|\__|\__|_|_| |_|\__, |___/
                                                                        |___/
    */
            MOUSE MAPPINGS
            ==============    1                      2
               _________      LMB                    RMB
             /     ___   \
             | 1 |   | 2 |    FOCUS & POINTING      SUBMIT   either hilited code or entire program
             |   | 5 |   |    BLOCK SUBMIT          SHF RMB  ls   List 40 obs _last_ table also in paste buffer
             | 3 |   |   |                          CTL RMB  lsh  List 40 obs hilited table
             |   | 6 |   |    3
             | 4 |   |   |    FOWARD SIDE BUTTON(FSB)
             |   |___|   |    FSB F11 ~run;quit     Insert run;wuit; at cursor location
             \___________/    SHF FSB F11 taila     Last 40 obs for _last_ table
                              CTL FSB F11 tailha    Last 40 obs hilited table
                              ALT FSB F11 lsfha     run hilited code batch

                              4
                              BACK SIDE BUTON(BSB)
                              BSB F12                Magic String
                              SHF BSB F12 frqva      Hilite variable in _last_ table proc freq will run
                              CTL BSB F12 cntva
                              ALT BSB F12 unva

                              5
                              SCROLL MOUSE BUTTON
                              SMB (F1)               Version Program
                              SHF SMB (F1) dmpa      Proc contents _last_ table with sample values
                              CTL SMB (F1) cona      Proc contents _last_ table (or just type con) in log
                              ALT SMB (F1) sqldesha  Hilite table and a sql describe will appear in log

                              6
                              MMB F2                  Submit code in notepad
                              SHF MSB FSB F2 lsaa     List all obs _last_ table
                              CTL MSB FSB F2 lsaha    List all obs hilited table table
                              ALT MSB FSB F2 xlrha    SAS table in excel

    /*  _       __                    _
    | || |     / _|_   _ _ __   ___  | | _____ _   _ ___
    | || |_   | |_| | | | `_ \ / __| | |/ / _ \ | | / __|
    |__   _|  |  _| |_| | | | | (__  |   <  __/ |_| \__ \
       |_|(_) |_|  \__,_|_| |_|\___| |_|\_\___|\__, |___/
                                               |___/
    */

    I have a strip above my function keys with ashor descrition of what the function key does
    The mouse uses some of these keys because my hand is most often on the mouse and it is quicker to push
    then reah for a key. Note you can use the function keys instead of the mouse or type the command(wutout the
    a suffix.
    The available keys tend to assigned depending on the project?

    F1         pgm;file &pgm..sas;file c:\ver\&pgm.&_q..sas;%let _q=%eval(0&_q +1);
    F2         note;notesubmit;
    F3         home;cntuh;
    F4         home;copy cmt;
    F5         store;note;notesubmit '%dmpha;';
    F6         home;conh;
    F7         log;file ".\pgm.log";note z;notesubmit '%utl_logcurchk;';
    F8         rfind
    F9         rchange
    F11         ~run;quit;
    F12        ~;;;;%end;%mend;/*'*/ *);*};*];*/;/*"*/;run;quit;%end;end;run;endcomp;%utlfix;
    SHF F1     note;notesubmit '%dmpa;';
    SHF F2     note;notesubmit;
    SHF F6     ~n ? "hil";n=*"PFil Mason";n gt:"Phil";n le:"Phim"; sql - eqt equal runcated
    SHF F7     ~libname x excel ".xls";proc sql;update x;set y=2;where n="Roger"
    SHF F8             ~avalible
    SHF F9             ~avalible
    SHF F10    ~options minoperator;%macro t(x=a)/minoperator;%if &x in (a b c) %then
    SHF F11    note;notesubmit '%taila;';
    SHF F12    store;note;notesubmit '%frqva;';
    CTL F1     note;notesubmit '%cona;';
    CTL F2     store;note;notesubmit 'lsaha;';
    CTL F3      ~available
    CTL F11    store;note;notesubmit '%tailha;';
    CTL F12    store;note;notesubmit '%cntva;';
    ALT F1     store;note;notesubmit '%sqldesha;';
    ALT F2     store;note;notesubmit '%xlrha;';
    ALT F3     proc report data=sashelp.class named list wrap;columns _all_;run;quit;
    ALT F11    store;note;notesubmit '%lsfha;';
    ALT F12     store;note;notesubmit '%unva;'
    CTL B       ~available
    CTL D      ~data;retain a b 1;proc tabulate;var a b;table a(n)*f=5.*b(n)*f=5.;run;
    CTL E      note e.e
    CTL G      note g.g
    CTL H      note h.h
    CTL I       ~availible
    CTL J       ~available
    CTL K      :mcu
    CTL L      :mcl
    CTL M      ~proc format;value $a;proc catalog cat=formats;modify a.formatc(desc='OK');run;
    CTL Q      c ';' ' ' all;c "'" " " all;c '*/' '  ' all;c '/*' '  ' all;
    CTL R      wattention;
    CTL T      ~proc tabulate data=class;class sex age;table age,sex*(n pctn<age>)/rts=8
    CTL U      ~do until(last.s);set c;by s;a+ag;end;do until(last.s);set c;by s;output;end;a=0
    CTL W      ~x 'tree "c:/temp" /F /A | clip'
    CTL Y      ~where name like "B_B" "%B%" "B%B"
    RMB        log;clear;out;clear;pgm;submit;home;log;z;z;
    SHF RMB    store;note;notesubmit '%lsa;'
    CTL RMB    store;note;notesubmit '%lsha;'
    MMB        ~mapped to F1SHF MMB
    SHF MMB    ~mapped to shf F1
    CTL MMB~   mapped to ctl F1

    /*___                        _   _
    | ___|     ___ _ __ ___   __| | | | _____ _   _ ___
    |___ \    / __| `_ ` _ \ / _` | | |/ / _ \ | | / __|
     ___) |  | (__| | | | | | (_| | |   <  __/ |_| \__ \
    |____(_)  \___|_| |_| |_|\__,_| |_|\_\___|\__, |___/
                                              |___/
    */

    I suggest you try them one at a time, before including the package of macros.

    Most command macros can be simplified using %dosubl. No need to call the second macro.
    Almost all of these can be mapped to function keys,  mouse actions or the command line.
    Some of these are over 40 years old. You never lose them because they are pure text no fancy binary catalog.
    Over two dozen command macros can be mapped to a 7 button mouse.
    In some cases you need to preface the mouse action  with ctrl, shift or alt.
    If right handed, mouse actions  are quick, because left hand hovers over ctrl, shift and alt
    making one keystroke then mouse button very fast.
    You can execute all of sas, perl, python or R from the command line.

    data;retain a b 1;proc tabulate;var a b;table a(n)*f=5.*b(n)*f=5.;run;
    data;retain a b c 1;proc tabulate;;var a b c;table a(n)*f=5.*b(n)*f=5.*c(n)*f=5.;run;
    proc tabulate;class_l;var a b c;table _l,a(n)*f=5.*b(n)*f=5.*c(n)*f=5.;run;

    COMMAND     DES

    keylist     Type keylist and a list of your function keys will appear in the log
    evlh        Hilite expression 2*(3+1) and type evlh and 8 will appear in log
    sumv        Hilite a column of numbers and an proc means will be run
    sumr        Hilite row of numbers type sumr and the sum will appear in the log and macro variable __sumr
    frq         Type frq sex*age on command line for a crosspatb frequency on sex*age for last dataset
    frqh        Highlight dataset and type frqh sex and  for on frequency on sexxage
    frqv        Hilite variable in _last_ table proc freq will run
    ls          Type ls and a list of first 40 obs of last table in output window and paste buffer
    lsh         Type lsh for list and output in paste buffer of hilited table
    lsfh        Hilight table type lsfh for 40 obs formatted list and output in paste buffer
    lsa         Ttpe lsal to list all obs from the last dataset
    lsah        Type lsah for a list of all obs in output and in paste buffer of hilited table
    lsw         Type lsw age14 and first 40 obs that satisfy the filter in the _last_ table in pastebuffer and list
    lswh        Hilight table and type lswh age14 and first 40 obs that satisfy filter in output and paste buffer
    tail        Type tail and last 40 obs of last dataset in paste buffer and output window
    tailh       Hilite table and type tailh and the last 40 obs will be in output window and in paste buffer
    con         Type con and contents of last dataset in outptut
    conh        Highlight table and type conh on command line. Results in output window
    dmp         Type dmg andmiddle observation of last dataset printed vertically
    dmph        Type dmph middle observation of highlighted dataset printed vertically with type length and sample value
    cnth        Hilite table and type cnth age sex and distinct counts of age sex cobinations in paste buffer
    cntuh       Hilite table and count distinct usubjid and number of obs are in paste bufferand log
    cntv        Hilight variable in _last_ table and get count and distinct counts on variable
    cuth        Hilite a block of code and type cuth and mutiple spaces will be reduced to single spaces
    iota        Type iota 10 and 10 rows with 01 02 03 - 10 will be added to the editor
    parh        Hilite a line of code and type parh to test for unbalanced parens
    cliph       Hilite a sas statement and macro variable  _clip will contain the statement
    xit         When exiting sas type xit and last program will open next time you start SAS
    avgby       Hilite table type avgby sex age for means by sex age also output dataset avgby
    avgh        Hilite table and type avgh for proc means output and table avgh will be created
    unv         Hilite a variable from the _last_ table and proc unvariate will be run on that variable
    debugh      Highlight macro and type debugh to debug the macro https://www.youtube.com/watch?v=JrxooHTx0c8
    vu          Type vu for viewtable of last dataset created
    vuh         Type vuh for viewtable of highlighted dataset
    xlsh        Highlight table and type xlsh and the table  will appear in excel uses libname need pc acces
    xplo        Type xplo ONEaTWO and exploded letters will be saved in past buffer. Use lower case for spaces
    cm          Hilite the blank line and subsequent block of code and the code will be commened out
    sasbatch    Highlight code type sasbatch on command line and the hilited code will be run batch
    xlr         Hilite a table and tyoe xlr and table will open up in excel. No need for pc acces to excel
    xpy         Type xpy roger for program banner with large font https://github.com/rogerjdeangelis/utl_program_banners
    doendh      Hilite block of macro code and match dos and ends
    sqldesh     Hilite table and type alt and scroll button and sql descibe will appear in log

    * unfortunately SAS eremoved the keydef function a long tome agoe, so you need to manually enter key
      definitions. You cannot even paste into the dunction keys.

    Here ar emy settings
    %inc "c:/oto/utl_logcurchk.sas";
    %inc "c:/oto/sas_perpac.sas";

    %mend offPac;

    /* load performance package into your autocall folder                      */
    /* if you need to update. Make cjhanges here and resave performane package */

    filename ft15f001 "c:/oto/sas_perpac.sas";
    parmcards4;
    /*
     _                     _                                              _
    (_)_ __  ___  ___ _ __| |_    ___ ___  _ __ ___  _ __ ___   ___ _ __ | |_
    | | `_ \/ __|/ _ \ `__| __|  / __/ _ \| `_ ` _ \| `_ ` _ \ / _ \ `_ \| __|
    | | | | \__ \  __/ |  | |_  | (_| (_) | | | | | | | | | | |  __/ | | | |_
    |_|_| |_|___/\___|_|   \__|  \___\___/|_| |_| |_|_| |_| |_|\___|_| |_|\__|

    Using the classic editor insert an empty commment block at the
    cursor position, put A in prefix area and hit PF 4

      To insert a comment at cursor position

      1. create empty comment block

       * *************************************
       * *
       * *
       * *************************************

         note "* *" allows you to update comment lines without end comment moving right;

      2. Type "save cmt" to save comment block in sasuser.profile.cmt.source
      3. Create function key f4 with copy cmt
      4. Finally, type A in the prefix area where you want the comment
      5. Hit F4
    */


    /*
      ___ _ __ ___
     / __| `_ ` _ \
    | (__| | | | | |
     \___|_| |_| |_|

    */

    /* comment out a block of code */
    %macro cm / cmd des="Hilite the blank and subsequent and subsequent block of code and the code will be commened out";
          c ' ' '/*' first;c ' ' '*/' last;
    %mend cm;


    /*         _     _
     ___  __ _| | __| | ___  ___
    / __|/ _` | |/ _` |/ _ \/ __|
    \__ \ (_| | | (_| |  __/\__ \
    |___/\__, |_|\__,_|\___||___/
            |_|
    */


    %macro sqldesh / cmd des="Hilite table and type alt and scroll button and sql descibe will appear in log";
       store;note;notesubmit '%sqldesha;';
       run;
    %mend sqldesh;

    %macro sqldesha;
       %symdel __sql;
       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         put _infile_;
         call symputx('__sql',_infile_);
       run;quit;
       proc sql;
           describe table &__sql;
       ;quit;
    %mend sqldesha;

    /*             _           _       _
     ___  __ _ ___| |__   __ _| |_ ___| |__
    / __|/ _` / __| `_ \ / _` | __/ __| `_ \
    \__ \ (_| \__ \ |_) | (_| | || (__| | | |
    |___/\__,_|___/_.__/ \__,_|\__\___|_| |_|

    */
    %macro sasbatch /cmd des="highlight code type sasbatch on command line";
       store;note;notesubmit '%sasbatcha;';
    %mend sasbatch;

    %macro sasbatcha;

         %utlfkil(d:/log/__clp.sas);
         %utlfkil(d:/log/__clp.log);
         %utlfkil(d:/log/__clp.lst);

      FILENAME clp clipbrd ;
      DATA _NULL_;
        INFILE clp;
        INPUT;
        file "d:/log/__clp.sas";
        put _infile_;
        putlof _infile_;
      RUN;quit;

      filename sin pipe %sysfunc(compbl("c:\PROGRA~1\sas94\SASFoundation\9.4\sas.exe -sysin d:/log/__clp.sas
            -log d:/log/__clp.log -autoexec c:\oto\tut_oto.sas
           -print d:/log/__clp.lst -sasautos c:/oto"));

       data _null_;
         infile sin;
         input;
         put _infile_;
       run;quit;

       x notepad.exe d:/log/__clp.log;

    %mend sasBatcha;

    /*          _ _
      _____   _| | |__
     / _ \ \ / / | `_ \
    |  __/\ V /| | | | |
     \___| \_/ |_|_| |_|

    */

    %macro evlh / cmd des="Hilite expression 2*(3+1) and type evlh  and 8 will appear in log";
       store;note;notesubmit '%evla;';
       run;
    %mend evlh;

    %macro evla;
       %symdel __evl;
       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         put _infile_;
         call symputx('__evl',_infile_);
       run;quit;
       data _null_;
         result=&__evl;
         put result=;
       run;quit;
    %mend evla;

    /*
     ___ _   _ _ __ _____   __
    / __| | | | `_ ` _ \ \ / /
    \__ \ |_| | | | | | \ V /
    |___/\__,_|_| |_| |_|\_/

    */

    %macro sumv / cmd des="Hilite a column of numbers and an proc means will run";
       store;note;notesubmit '%sumvha;';
       run;
    %mend sumv;

    %macro sumvha;
       filename clp clipbrd ;
       data _sumh_;
         infile clp;
         input x;
       run;quit;
       proc means data=_sumh_ n sum mean std min q1 median q3 max;run;quit
    %mend sumvha;

    /*    _
    __  _| |_ __
    \ \/ / | `__|
     >  <| | |
    /_/\_\_|_|

    */

    %macro xlrh /cmd des="Hilite a table and tyoe xlr and table will open it in excel. No need for pc acces to excel";
       store;note;notesubmit '%xlrha;';
       run;
    %mend xlrh;

    %macro xlrha/cmd;

        %local argx;

        filename clp clipbrd ;

        data _null_;
           infile clp;
           input;
           argx=_infile_;
           call symputx("argx",argx);
           putlog argx=;
        run;quit;

        /* %let argx=sashelp.class; */

        %utlfkil(%sysfunc(getoption(work))/_rpt.xlsx);

        ods listing close;

        ods excel file="%sysfunc(getoption(work))/_rpt.xlsx"
                options(
                   sheet_name                 = "&argx"
                   autofilter                 = "yes"
                   frozen_headers             = "1"
                   gridlines                  = "yes"
                   embedded_titles            = "yes"
                   embedded_footnoteS         = "yes"
                   );

        proc report data=&argx missing style(column)=[textalign=left verticalalign=top] split="_";
        title "SAS table &argx";
        run;quit;

        ods excel close;

        ods listing;

        options noxwait noxsync;
        /* Open Excel */
        x "'C:\Program Files\Microsoft Office\OFFICE14\excel.exe' %sysfunc(getoption(work))/_rpt.xlsx";
        run;quit;

    %mend xlrha;

    /*
     ___ _   _ _ __ ___  _ __
    / __| | | | `_ ` _ \| `__|
    \__ \ |_| | | | | | | |      sashelp.class
    |___/\__,_|_| |_| |_|_|

    */

    %macro sumr /cmd parmbuff des='Hilite row of numbers type sumr and the sum will appear in the log and macro variable __sumr';
        /* hilite 1 2 3 4 5 and */
        store;note;notesubmit '%sumrh;';
       run;
    %mend sumr;

    %macro sumrh;
       %global __sumr;
       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         row=translate(_infile_,'+',' ');
         call symputx('row',row);
       run;
       %let __sumr=%sysevalf(&row);
       %put &=__sumr;
    %mend sumrh;

    /* %put &=__sumr;  */


    /*       _
    (_) ___ | |_ __ _
    | |/ _ \| __/ _` |
    | | (_) | || (_| |
    |_|\___/ \__\__,_|

    */

    %macro iota(utliota1)/cmd des="Type iota 10 and 10 rows with 01 02 03 - 10 will be added to the editor";
       sub '%iotb';
    %mend iota;
    /*          _   _
      ___ _   _| |_| |__
     / __| | | | __| `_ \
    | (__| |_| | |_| | | |
     \___|\__,_|\__|_| |_|

    */
    %macro cuth/cmd des="Hilite a block of code and type cuth and mutiple spaces will be reduced to single spaces";
      /* USAGE
         hilight a block of code and type cuth on command line
        this changes two spaces to one space
        becomes
        1          5    3        6
        1 5 3 6
      */

      %do i=1 %to 20;
        c '  ' ' ' all;
      %end;
    %mend cuth;

    /*                _
     _ __   __ _ _ __| |__
    | `_ \ / _` | `__| `_ \
    | |_) | (_| | |  | | | |
    | .__/ \__,_|_|  |_| |_|
    |_|
    */

    %macro parh / cmd des="Hilite a line of code and type parh to test for unbalanced parens";
       store;note;notesubmit '%parha;';
       run;
    %mend parh;

    %macro parha ;
       filename clp clipbrd ;
       data _null_;
         retain add 0;
         infile clp;
         input ;
         lft=countc(_infile_,'(');
         rgt=countc(_infile_,')');
         lftrgt=lft - rgt;
         abslftrgt=abs(lftrgt);
         select;
            when (lftrgt=0) putlog "**********************" // "Parentheses match  ()"  // "**********************";
            when (lftrgt>0) putlog "**********************" // "Missing " lftrgt ") parentheses  "  // "**********************";
            when (lftrgt<0) putlog "**********************" // "Missing " abslftrgt  "( parentheses  "  // "**********************";
            otherwise;
         end;
       run;
    %mend parha;

    /*    _ _
    __  _(_) |_
    \ \/ / | __|
     >  <| | |_
    /_/\_\_|\__|

    */

    %macro xit/ cmd des='When exiting sas type xit and last program will open next time you start SAS';
      pgm;file &pgm..sas;file c:\ver\&pgm.&_q..sas;%let _q=%eval(0&_q +1);
      home;save pgm_last r;%sysfunc(sleep(1,1));bye;
    %mend xit;


    /*          _
      ___ _ __ | |_ _   _
     / __| `_ \| __| | | |  data class;
    | (__| | | | |_| |_| |   set sashelp.class;
     \___|_| |_|\__|\__,_|   usubjid=age;
                            run;quit;
    */

    %macro cntuh /cmd parmbuff des="Hilite table and count distinct usubjid and number of obs are in paste buffer";

       %local _vars;
       %let _vars=&syspbuff;
       %put _vars=&_vars;
       %let _vars=%sysfunc(translate(&_vars,%str(,),%str( )));
       store;note;notesubmit '%cntuha;';
       run;
    %mend cntuh;

    %macro cntuha;

       %local _cnt_ _obs_;

       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         put _infile_;
         call symputx('_sasdataset',_infile_);
         call symputx("__dtetym",put(datetime(),datetime23.));
       run;

       %put &=_sasdataset;
       %put &=_vars;

       proc sql noprint;
        select put(count(distinct usubjid), comma18.) into :_cnt_ separated by '' from &_sasdataset;
        select put(count(*), comma18.) into :_obs_ separated by '' from &_sasdataset;
       quit;

      filename __dm clipbrd ;
      data _null_;file __dm; put "";run;quit;
      data _null_;
         length msg $255;
        file __dm;
        msg=cats('/','*',"--- Number of unique usubjid=&_cnt_ for in &_sasdataset (obs=&_obs_) &__dtetym ---",'*','/');
        putlog msg;
        put msg;
      run;quit;
      filename __dm clear;
    run;quit;
    title;
    %mend cntuha;



    /*    _ _
      ___| (_)_ __
     / __| | | `_ \
    | (__| | | |_) |
     \___|_|_| .__/
             |_|
    */

    %macro cliph / cmd des="Hilite a line of  and macro variable _clip will contain the statement";
       store;note;notesubmit '%clipha;';
       run;
    %mend cliph;

    %macro clipha/cmd
     %global _clip;
     %local rc fileref fid len ;
     %let rc = %sysfunc( filename( fileref, , clipbrd ) );
     %if &rc eq 0 %then %do;
     %let fid = %sysfunc( fopen( &fileref, s, 32767, v) );
     %if &fid ne 0 %then %do;
     %do %while( %sysfunc( fread( &fid ) )=0 );
     %let len = %sysfunc( frlen( &fid ) );
     %let rc = %sysfunc( fget( &fid, _clip, &len ) );
     %*put len = &len line = %superq( line );
     %end;
     %let rc = %sysfunc( fclose( &fid ) );
     %end; %else %do;
     %put failed to open clipboard fileref.;
     %end;
     %let rc = %sysfunc( filename( fileref ) );
     %end; %else %do;
     %put %sysfunc( sysmsg( ) );
     %end;
    %mend clipha;


    /*          _   _
      ___ _ __ | |_| |__
     / __| `_ \| __| `_ \
    | (__| | | | |_| | | |
     \___|_| |_|\__|_| |_|

    */

    %macro cnth/cmd parmbuff  des='hilite table and type cnth age sex and distinct counts of age sex cobinations in paste buffer';
       %local _vars;
       %let _vars=&syspbuff;
       %put _vars=&_vars;
       %let _vars=%sysfunc(translate(&_vars,%str(,),%str( )));
       %put &=_vars;
       store;note;notesubmit '%cntha;';
       run;
    %mend cnth;


    %macro cntha;

       %local _cnt_ _obs_;

       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         put _infile_;
         call symputx('_sasdataset',_infile_);
         call symputx("__dtetym",put(datetime(),datetime23.));
       run;

       %put &=_sasdataset;
       %put &=_vars;

       proc sql noprint;
        select put(count(*), comma18.) into :_cnt_ separated by '' from ( select distinct &_vars from &_sasdataset);
        select put(count(*), comma18.) into :_obs_ separated by '' from &_sasdataset;
       quit;

      filename __dm clipbrd ;
      data _null_;file __dm; put "";run;quit;
      data _null_;
         length msg $255;
         file __dm;
        msg=cats('/','*',"----- Number of unique levels=&_cnt_ for &_vars from &_sasdataset (obs=&_obs_) &__dtetym -----",'*','/');
        putlog msg;
        put msg;
      run;quit;
      filename __dm clear;
    run;quit;
    title;
    %mend cntha;

    /*                _
      __ ___   ____ _| |__  _   _
     / _` \ \ / / _` | `_ \| | | |
    | (_| |\ V / (_| | |_) | |_| |   sashelp.class
     \__,_| \_/ \__, |_.__/ \__, |
                |___/       |___/
    */
    %macro avgby /cmd parmbuff des="Hilite table type avgby sex age for means by sex age also output dataset avgby";

       /* usage
           hilight sashelp.class and
           type avgby sex age (on classic 1980s command line)
           output will be in paste buffer
       */

       %let argx=&syspbuff;
       store;note;notesubmit '%avgbya;';
       run;
    %mend avgby;

    %macro avgbya;
       options ls=255;
       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         put _infile_;
         call symputx('argd',_infile_);
         call symputx("__dtetym",put(datetime(),datetime23.));
       run;
       dm "out;clear;";
       options nocenter;
       footnote;
       ODS NOPROCTITLE;
       title1 "Means by &argx datasets &argd &__dtetym";
       proc means data=&argd missing n nmiss sum mean min q1 median q3 max;
       class &argx;
       output out=avgby;
       run;
       title;
       ODS PROCTITLE;
       dm "out;top;"
      ;
    %mend avgbya;

    /*        _ _
    | |_ __ _(_) |  data class;
    | __/ _` | | |   set sashelp.shoes;
    | || (_| | | |  run;
     \__\__,_|_|_|

    */

    %macro tail /cmd des="type tail and last 40 obs of last dataset in paste buffer and output window";
       note;gsubmit '%taila;';
    %mend tail;


    %macro taila /cmd ;
      %put XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX;
      footnote;
      options nocenter;
      %utlfkil("%sysfunc(pathname(work))/__dm.txt");
      proc sql noprint;
            select
               put(count(*),comma18.)
              ,count(*)
            into
              :tob  trimmed
             ,:tobs  trimmed
      from _last_;quit;
      data _null_; call symputx("__dtetym",put(datetime(),datetime23.)); run;
      title "last 41 obs from %upcase(%sysfunc(getoption(_last_))) total obs=&tob &__dtetym";
      proc printto print="%sysfunc(pathname(work))/__dm.txt";
      %let pobs=%sysfunc(ifn(&tobs > 40, %eval(&tobs - 40),1));
      proc print data=_last_ ( firstObs= &pobs ) width=min uniform  heading=horizontal;
      format _all_;
      run;
      proc printto;
      run;quit;
      title;
      filename __dm clipbrd ;
      data _null_;file _dm; put "";run;quit;
      data _null_;
         infile "%sysfunc(pathname(work))/__dm.txt" end=dne;
         input;
         file __dm ;
         put _infile_;
         file print;
         put _infile_;
      run;quit;
      filename __dm clear;
      run;quit;
      title;
      dm "out;";
    %mend taila;


    /*        _ _ _
    | |_ __ _(_) | |__
    | __/ _` | | | `_ \
    | || (_| | | | | | |
     \__\__,_|_|_|_| |_|

    */

    %macro tailh /cmd des="hilite table and type tailh and the last 40 obs will be in output window and in paste buffer";
       /* hilight sashelp.shoes and type tailh on command line
          The last 40 obs will be put in the paste buffer.
    */

       store;note;notesubmit '%tailha;';
    %mend tailh;

    %macro tailha /cmd des="last 40 obs of highlight dataset and type tailha for a list of 10 obs";
      FILENAME clp clipbrd ;
      DATA _NULL_;
        INFILE clp;
        INPUT;
        put _infile_;
        call symputx('argx',_infile_);
      RUN;
      footnote;
      options nocenter;
      %utlfkil("%sysfunc(pathname(work))/__dm.txt");
      proc sql noprint;
            select
               put(count(*),comma18.)
              ,count(*)
            into
              :tob  trimmed
             ,:tobs  trimmed
      from &argx;quit;
      data _null_; call symputx("__dtetym",put(datetime(),datetime23.)); run;
      title "last 41 obs from %upcase(&argx) total obs=&tob &__dtetym";
      proc printto print="%sysfunc(pathname(work))/__dm.txt";
      %let pobs=%sysfunc(ifn(&tobs > 40, %eval(&tobs - 40),1));
      proc print data=&argx ( firstObs= &pobs ) width=min uniform  heading=horizontal;
      format _all_;
      run;
      proc printto;
      run;quit;
      title;
      filename __dm clipbrd ;
      data _null_;file _dm; put "";run;quit;
      data _null_;
         infile "%sysfunc(pathname(work))/__dm.txt" end=dne;
         input;
         file __dm ;
         put _infile_;
         file print;
         put _infile_;
      run;quit;
      filename __dm clear;
      run;quit;
      title;
      dm "out;";
    %mend tailha;

    /*
    | |___
    | / __|
    | \__ \
    |_|___/

    */

    %macro ls / cmd des='Type ls and a list of first 40 obs of last table in output window and paste buffer';
       note;notesubmit '%lsa;';
    %mend ls;

    %macro lsa /cmd ;
      dm "out;clear;";
      %utlfkil("%sysfunc(pathname(work))/__dm.txt");
      data _null_; call symputx("__dtetym",put(datetime(),datetime23.)); run;
      options nocenter;
      title;
      proc sql noprint;select put(count(*),comma18.) into :tob  separated by ' ' from _last_;quit;
      proc printto print="%sysfunc(pathname(work))/__dm.txt";
      proc print data=_last_ ( Obs= 40 ) width=min uniform  heading=horizontal;format _all_;
      format _all_;
      run;
      proc printto;
      filename __dm clipbrd ;
      title "Up to 40 obs %upcase(%sysfunc(getoption(_last_))) total obs=&tob &__dtetym";
      data _null_;
         infile "%sysfunc(pathname(work))/__dm.txt" end=dne;
         input;
         file __dm ;
         put _infile_;
         file print;
         put _infile_;
      run;quit;
      filename __dm clear;
      title;
      dm "out;";
    %mend lsa;


    /*     _
    | |___| |__
    | / __| `_ \   data shoes;;
    | \__ \ | | |  set sashelp.class
    |_|___/_| |_|  run;quit;

    */

    %macro lsh /cmd des='Type lsh for list and output in paste buffer of hilited table';
       store;note;notesubmit '%lsha;';
    %mend lsh;

    %macro lsha;
      dm "out;clear;";
      FILENAME clp clipbrd ;
      DATA _NULL_;
        INFILE clp;
        INPUT;
        put _infile_;
        call symputx('argx',_infile_);
        call symputx("__dtetym",put(datetime(),datetime23.));
      RUN;
      title;
      proc sql noprint;select put(count(*),comma18.) into :tob  separated by ' ' from &argx;quit;
      proc printto print="%sysfunc(pathname(work))/__dm.txt" new;
      proc print data=&argx( Obs= 40 )  width=min uniform  heading=horizontal;
      format _all_;run;
      proc printto;
      filename __dm clipbrd ;
      title "Up to 40 obs from %upcase(&argx) total obs=&tob &__dtetym";
      data _null_;
         infile "%sysfunc(pathname(work))/__dm.txt" end=dne;
         input;
         file __dm ;
         put _infile_;
         file print;
         put _infile_;
      run;
    %mend lsha;

    /*      __ _
    | |___ / _| |__    data fmt;
    | / __| |_| `_ \     date=today();          sashelp.shoes
    | \__ \  _| | | |    format date date9.;
    |_|___/_| |_| |_|    output;output;output;
                       run;
    */

    %macro lsfh /cmd des='Hilight table type lsfh for 40 obs formatted list and output in paste buffer';
       store;note;notesubmit '%lsfha;';
    %mend lsfh;

    %macro lsfha;
      dm "out;clear;";
      FILENAME clp clipbrd ;
      DATA _NULL_;
        INFILE clp;
        INPUT;
        put _infile_;
        call symputx('argx',_infile_);
        call symputx("__dtetym",put(datetime(),datetime23.));
      RUN;
      title;
      proc sql noprint;select put(count(*),comma18.) into :tob  separated by ' ' from &argx;quit;
      proc printto print="%sysfunc(pathname(work))/__dm.txt" new;
      proc print data=&argx( Obs= 40 )  width=min uniform  heading=horizontal;
      run;
      proc printto;
      filename __dm clipbrd ;
      title "Up to 40 obs from %upcase(&argx) with formatted variables  total obs=&tob &__dtetym";
      data _null_;
         infile "%sysfunc(pathname(work))/__dm.txt" end=dne;
         input;
         file __dm ;
         put _infile_;
         file print;
         put _infile_;
      run;
    %mend lsfha;

    /*
    | |___  __ _
    | / __|/ _` |   data class;
    | \__ \ (_| |   set sashelp.shoes;
    |_|___/\__,_|   run;

    */

    %macro lsa / cmd des="Ttpe lsal to list all obs from the last dataset";
       note;notesubmit '%lsala;';
       run;
    %mend lsa;

    %macro lsaa /cmd;
      %local __tob __dtetym;
       dm "out;clear;";
      proc sql noprint;select put(count(*),comma18.), put(datetime(),datetime23.)
      into :__tob trimmed, :__dtetym trimmed
      from _last_;quit;
      title "All obs from %upcase(%sysfunc(getoption(_last_))) total obs=&__tob &__dtetym";
      proc print data=_last_  heading=horizontal width=min;
       footnote;
       format _all_;
       run;
       title;
       dm "out;top";
    %mend lsaa;

    /*           _
    | |___  __ _| |__
    | / __|/ _` | `_ \
    | \__ \ (_| | | | |
    |_|___/\__,_|_| |_|

    */

    %macro lsah /cmd des='Type lsah for a list of all obs in output and in paste buffer of hilited table';
       store;note;notesubmit '%lsalha;';
    %mend lsah;

    %macro lsaha;
      %local tob __dtetym;
      dm "out;clear;";
      FILENAME clp clipbrd ;
      DATA _NULL_;
        INFILE clp;
        INPUT;
        put _infile_;
        call symputx('argx',_infile_);
        call symputx("__dtetym",put(datetime(),datetime23.));
      RUN;
      proc sql noprint;select put(count(*),comma18.) into :tob trimmed from &argx;quit;
      proc print data=&argx  width=min uniform  heading=horizontal;
      title "All obs from &argx total obs=&tob &__dtetym";
      format _all_;run;
    %mend lsaha;


    /*
    macro oldmac;
    data class;
     set sashelp.class;
    run;quit;
    %
    */

    /*   _                      _ _
      __| | ___   ___ _ __   __| | |__
     / _` |/ _ \ / _ \ `_ \ / _` | `_ \
    | (_| | (_) |  __/ | | | (_| | | | |
     \__,_|\___/ \___|_| |_|\__,_|_| |_|

     %do i=1 to 10;
       %do j=1 to 10 ;
         x=2;
         x=2;
         x=3;
       end;

    **********************

    Missing 2  %END

    **********************
    */

    /* match %do and %end */
    %macro doendh / cmd des='Hilite block of macro code and match dos and ends';
       store;note;notesubmit '%doendha;';
       run;
    %mend doendh;

    %macro doendha;
       filename clp clipbrd ;
       data _null_;
         retain lft rgt 0 ;
         infile clp end=dne;
         do until(dne);
             input ;
             lft=lft+count(upcase(_infile_),'%DO ');
             rgt=rgt+count(upcase(_infile_),'%END;');
             put lft= rgt=;
         end;
         lftrgt=lft - rgt;
         abslftrgt=abs(lftrgt);
         select;
            when (lftrgt=0) putlog "**********************" // '%DO %END  match'  // "**********************";
            when (lftrgt>0) putlog "**********************" // 'Missing ' lftrgt ' %END  '  // "**********************";
            when (lftrgt<0) putlog "**********************" // 'Missing ' abslftrgt  ' %DO;  '  // "**********************";
            otherwise;
         end;
       run;
    %mend doendha;

    /*
    | |_____      __
    | / __\ \ /\ / /  data class;
    | \__ \\ V  V /      set sashelp.class;   lsw "sex='F'"
    |_|___/ \_/\_/    run;quit;

    */

    %macro lsw /cmd parmbuff des='Type lsw "age=14" and first 40 obs that satisfy the filter in the _last_ table in pastebuffer and list
       %let argx=&syspbuff;
       %put &=argx;
       note;notesubmit '%lswa;';
    %mend lsw;

    %macro lswa/cmd;
      dm "out;clear;";
      title;footnote;
      data _null_; call symputx("__dtetym",put(datetime(),datetime23.)); run;
      proc printto print="%sysfunc(pathname(work))/__dm.txt" new;
      proc sql noprint;select put(count(*),comma18.) into :tob  separated by ' ' from _last_;quit;
      proc print data=_last_(obs=40 where=(%sysfunc(dequote(&argx)))) width=min uniform heading=horizontal;format _all_;
      proc printto;
      filename __dm clipbrd ;
      title "Up to 40 obs %upcase(%sysfunc(getoption(_last_))) total obs=&tob &__dtetym";
      data _null_;
         infile "%sysfunc(pathname(work))/__dm.txt" end=dne;
         input;
         file __dm ;
         put _infile_;
         file print;
         put _infile_;
      run;quit;
      filename __dm clear;
      dm "out;top;";
      run;quit;
    %mend lswa;

    /*              _
    | |_____      _| |__
    | / __\ \ /\ / / `_ \
    | \__ \\ V  V /| | | |   sashelp.class lswh "age=14 and sex='F'"
    |_|___/ \_/\_/ |_| |_|

    */

    %macro lswh /cmd parmbuff Des='hilight table and type lswh "age=14" and first 40 obs that satisfy filter in output and paste buffer'
       %let argx=&syspbuff;
       store;note;notesubmit '%lswha;';
       run;
    %mend lswh;

    %macro lswha;
       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         put _infile_;
         call symputx('argd',_infile_);
       run;
       dm "out;clear;";
       proc datasets lib=work nodetails nolist;
       delete frqh;
       run;quit;
       options nocenter;
       data frqh;
          set &argd(where=(%sysfunc(dequote(&argx))));
       run;quit;
       title "Up to 40 obs from from &argd(where %sysfunc(dequote(&argx))) total obs=&tob &__dtetym ";
       proc print data=frqh(obs=100 )  width=min;
       format _all_;
       run;
       dm "out;top;";
    %mend lswha;


    /*                _
      __ ___   ____ _| |__
     / _` \ \ / / _` | `_ \    data class;
    | (_| |\ V / (_| | | | |     set sashelp.class;   age
     \__,_| \_/ \__, |_| |_|   run;quit;
                |___/
    */

    %macro avgh / cmd des="Hilite table and type avgh for proc means output and table avgh will be created";
       store;note;notesubmit '%avgha;';
       run;
    %mend avgh;

    %macro avgha;
       proc datasets lib=work nodetails nolist;
         delete avgh;
       run;quit;
       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         _infile_=upcase(_infile_);
         call symputx("__dtetym",put(datetime(),datetime23.));
         cmd=catx(' ',
              'proc means data= ',_infile_,'n nmiss sum mean min q1 median q3 max;'
             ,'Title SAS daatset',_infile_,"&__dtetym;",'output out=avgh;run;quit' );
         put cmd=;
         call execute (cmd);
         stop;
       run;
    %mend avgha;

    /*__
     / _|_ __ __ ___   __
    | |_| `__/ _` \ \ / /     data class;
    |  _| | | (_| |\ V /        set sashelp.class;
    |_| |_|  \__, | \_/         id = age ;
                |_|           run;quit;
    */

    %macro frqv / cmd
       des="Hilite variable in _last_ table andn proc freq hiltred variable";
       store;note;notesubmit '%frqva;';
       run;
    %mend frqv;

    %macro frqva;
       filename clp clipbrd ;
       title "proc freq table = %upcase(%sysfunc(getoption(_last_)))";
       data _null_;
         infile clp;
         input;
         cmd=catx(' ',
           'proc freq  data=_last_ levels order=freq;tables',_infile_,'/missing;run;quit');
         call execute (cmd);
       run;
    %mend frqva;

    /*          _
      ___ _ __ | |___   __
     / __| `_ \| __\ \ / /
    | (__| | | | |_ \ V /
     \___|_| |_|\__| \_/

    var         obs   uniques
    -------------------------
     age         19         6

    */

    %macro cntv / cmd des="Hilight variable in _last_ table and get count and distinct counts on variable";
       store;note;notesubmit '%cntva';
       run;
    %mend cntv;

    %macro cntva/cmd;
       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         cmd=catx(' ','proc sql;select','"',_infile_,'" as var, count(*) as obs, count(distinct',_infile_,') as uniques from _last_;quit
         putlog cmd;
         call execute (cmd);
       run;
    %mend cntva;

    /*
     _   _ _ ____   __
    | | | | `_ \ \ / /
    | |_| | | | \ V /
     \__,_|_| |_|\_/

    */

    %macro unv / cmd des="Hilite a variable from the _last_ table and proc unvariate will be run on that variable";
       store;note;notesubmit '%unva;';
       run;
    %mend unv;

    %macro unva;
       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         cmd=catx(' ','proc univariate data=_last_ plot;var',_infile_,';run;quit');
         call execute (cmd);
       run;
    %mend unva;

    /*   _
      __| |_ __ ___  _ __
     / _` | `_ ` _ \| `_ \
    | (_| | | | | | | |_) |
     \__,_|_| |_| |_| .__/
                    |_|
    */

    %macro dmp /cmd des="Type dmg andmiddle observation of last dataset printed vertically";
       note;notesubmit '%dmpa';
       run;
    %mend dmp;

    %macro dmpa;
       /* all this to get middle record */
       %local tob __dtetym;
       proc sql;select count(*),put(datetime(),datetime23.)  into :tob trimmed, :__dtetym trimmed from _last_;quit;
       data _null_;
          If _n_=0 then set _last_ nobs=mobs;
          rec=max(int(mobs/2),1);
          set _last_ point=rec;
          array chr[*] $80 _character_;
          array num[*] _numeric_;
          put "Middle Observation(" rec ") of table = &argx - Total Obs &tob &__dtetym";
          putlog // ' -- CHARACTER -- ';
          putlog @1 "Variable" @33 'Typ' @40 'Value' @67 'Label' /;
          do i=1 to dim(chr);
             nam=vname(chr[i]);
             typ=vtype(chr[i]);
             len=vlength(chr[i]);
             lbl=vlabel(chr[i]);
             putlog @1 nam @34 typ @35 len @40 chr[i] $44. @67 lbl $40.;
          end;
          putlog // ' -- NUMERIC -- ';
          putlog @1 "Variable" @33 'Typ' @40 'Value' @67 'Label' /;
          do i=1 to dim(num);
             nam=vname(num[i]);
             typ=vtype(num[i]);
             len=vlength(num[i]);
             lbl=vlabel(num[i]);
             numc=put(num[i],best. -l);
             putlog @1 nam @34 typ @41 len @40 numc   @67 lbl $40.;
          end;
          stop;
       run;quit;
    %mend dmpa;

    /*   _                 _
      __| |_ __ ___  _ __ | |__
     / _` | `_ ` _ \| `_ \| `_ \
    | (_| | | | | | | |_) | | | |   sashelp.class
     \__,_|_| |_| |_| .__/|_| |_|
                    |_|
    */

    %macro dmph /cmd des="Type dmph middle observation of highlighted dataset printed vertically with type length and sample value";
       store;note;notesubmit '%dmpha;';
       run;
    %mend dmph;
    %macro dmpha;
       %local  __dtetym tob
       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         put _infile_;
         call symputx('argx',_infile_);
       run;
       /* all this to get middle record */
       %symdel tob;

       proc sql;select count(*),put(datetime(),datetime23.)  into :tob trimmed, :__dtetym trimmed from _last_;quit;
       run;

       data _null_;

          If _n_=0 then set &argx nobs=mobs;
          rec=max(int(mobs/2),1);
          set &argx point=rec;
          call symputx("__dtetym",put(datetime(),datetime23.));
          totobs=put(&tob,comma16. -l);
          put "Middle Observation(" rec ") of table = &argx - Total Obs &tob &__dtetym";
          putlog // ' -- CHARACTER -- ';
          putlog @1 "Variable" @33 'Typ' @40 'Value' @67 'Label' /;

          array chr[*] _character_;
          array num[*] _numeric_;
          do i=1 to dim(chr);
             nam=vname(chr[i]);
             typ=vtype(chr[i]);
             len=vlength(chr[i]);
             lbl=vlabel(chr[i]);
             putlog @1 nam @34 typ @35 len @40 chr[i] $44. @67 lbl $40.;
          end;
          putlog // ' -- NUMERIC -- ';
          do i=1 to dim(num);
             nam=vname(num[i]);
             typ=vtype(num[i]);
             len=vlength(num[i]);
             lbl=vlabel(num[i]);
             numc=put(num[i],best. -l);
             putlog @1 nam @34 typ @41 len @40 numc   @67 lbl $40.;
          end;
          stop;
       run;quit;
    %mend dmpha;

    /*__
     / _|_ __ __ _
    | |_| `__/ _` |
    |  _| | | (_| |  sashelp.class
    |_| |_|  \__, |
                |_|
    */

    %macro frq /cmd parmbuff des="Type frq sex*age on command line for a crosspatb frequency on sex*age for last dataset";
    /*-----------------------------------------*\
    |  frq sex*age                              |
    \*-----------------------------------------*/
       %let argx=%scan(&syspbuff,1,%str( ));
       %*syslput argx=&argx;
       note;notesubmit '%frqa;';
       run;
    %mend frq;

    %macro frqa;
       dm "out;clear;";
       *rsubmit;
       options nocenter;
       footnote;
       data _null_;
          call symputx("__dtetym",put(datetime(),datetime23.));
       run;quit;

       title1 "Frequency of &argx datasets %sysfunc(getoption(_last_)) &__dtetym";
       proc freq data=_last_ levels;
       tables &argx./list missing;
       run;
       title;
       *endrsubmit;
       dm "out;top;";
    %mend frqa;


    /*__           _
     / _|_ __ __ _| |__
    | |_| `__/ _` | `_ \
    |  _| | | (_| | | | |
    |_| |_|  \__, |_| |_|
                |_|
    */

    %macro frqh /cmd parmbuff des="highlight dataset and type frqh sex and  for on frequency on sexxage";
       %let argx=%scan(&syspbuff,1,%str( ));
       store;note;notesubmit '%frqha;';
       run;
    %mend frqh;

    %macro frqha;
       filename clp clipbrd ;
       data _null_;
         infile clp;
         input;
         put _infile_;
         call symputx('argd',_infile_);
         call symputx("__dtetym",put(datetime(),datetime23.));
       run;
       dm "out;clear;";
       options nocenter;
       footnote;
       title1 "frequency of &argx datasets &argd &__dtetym";
       proc freq data=&argd levels;
       tables &argx./list missing out=frqh;
       run;
       title;
       dm "out;top;";
    %mend frqha;

    %macro prtwh /cmd parmbuff;
    /*-----------------------------------------*\
    |  highlight dataset in editor              |
    |  prt "sex='F'"                    |
    \*-----------------------------------------*/
       %let argx=&syspbuff;
       store;note;notesubmit '%prtwha;';
       run;
    %mend prtwh;

    /*   _      _                 _
      __| | ___| |__  _   _  __ _| |__
     / _` |/ _ \ `_ \| | | |/ _` | `_ \
    | (_| |  __/ |_) | |_| | (_| | | | |
     \__,_|\___|_.__/ \__,_|\__, |_| |_|
                            |___/
    */

    %macro debugh/cmd des="Highlight macro and type debugh to debug the macro";
       store;note;notesubmit '%debugha;';
       run;
    %mend debugh;

    %macro debugha;
       %let rc=%sysfunc(filename(myRef,%sysfunc(pathname(work))/mactxt.sas));
       %let sysrc=%sysfunc(fdelete(&myRef));
       %let rc=%sysfunc(filename(&myref));
       filename clp clipbrd ;
       data _null_;
         infile clp;
         file "%sysfunc(pathname(work))/macraw.sas";
         input;
         put _infile_;
       run;
       filename mprint  "%sysfunc(pathname(work))/mactxt.sas";
       options mfile mprint source2;
       %inc "%sysfunc(pathname(work))/macraw.sas";
       run;quit;
       options nomfile nomprint;
       filename mprint clear;
       %inc "%sysfunc(pathname(work))/mactxt.sas";
       run;quit;
    %mend debugha;

    /*
      ___ ___  _ __
     / __/ _ \| `_ \
    | (_| (_) | | | |
     \___\___/|_| |_|

    */

    %macro con / cmd des="type con and contents of last dataset in outptut";
      note;notesubmit '%cona;';
    %mend con;

    %macro cona   / cmd des="create contents output";
    dm "out;clear;";
      options nocenter;
      footnote;
      proc contents data=_last_ position;
      run;
      title;
    run;
    dm "out;top;";
    %mend cona;

    /*               _
      ___ ___  _ __ | |__
     / __/ _ \| `_ \| `_ \
    | (_| (_) | | | | | | |  sashelp.class
     \___\___/|_| |_|_| |_|

    */


    %macro conh / cmd des="highlight table and type conh on command line. Results in output window";
      store;note;notesubmit '%conha;';
    %mend conh;


    %macro conha;
    FILENAME clp clipbrd ;
    DATA _NULL_;
      INFILE clp;
      INPUT;
      put _infile_;
      call symputx('argx',_infile_);
    RUN;
    dm "out;clear;";
    title "Contents of &argx.";
    options nocenter;
    proc contents data=&argx. position;
    run;
    title;
    dm "out;top";
    %mend conha;

    /*
    __   ___   _
    \ \ / / | | |
     \ V /| |_| |   sashelp.class
      \_/  \__,_|

    */

    %macro vu  / cmd des="Type vu for viewtable of last dataset created";
       vt _last_ COLHEADING=NAMES;
       run;
    %mend vu ;

    /*           _
    __   ___   _| |__
    \ \ / / | | | `_ \
     \ V /| |_| | | | |
      \_/  \__,_|_| |_|

    */

    %macro vuh / cmd des="Type vuh for viewtable of highlighted dataset";
       store;note;notesubmit '%vuha;';
       run;
    %mend vuh;

    %macro vuha;
    filename clp clipbrd ;
    data _null_;
      infile clp;
      input;
      put _infile_;
      call symputx('argx',_infile_);
    run;
    dm "vt &argx"  COLHEADING=NAMES;
    %mend vuha;

    /*    _     _
    __  _| |___| |__
    \ \/ / / __| `_ \
     >  <| \__ \ | | |
    /_/\_\_|___/_| |_|

    */

    %macro xlsh /cmd des="Highlight table and type xlsh and the table  will appear in excel uses libname need pc acces";;
       store;note;notesubmit '%xlsha;';
       run;
    %mend xlsh;

    %macro xlsha/cmd;

        filename clp clipbrd ;
        data _null_;
         infile clp;
         input;
         put _infile_;
         call symputx('argx',_infile_);
        run;

        %let __tmp=%sysfunc(pathname(work))\myxls.xlsx;

        data _null_;
            fname="tempfile";
            rc=filename(fname, "&__tmp");
            put rc=;
            if rc = 0 and fexist(fname) then
           rc=fdelete(fname);
        rc=filename(fname);
        run;

        libname __xls excel "&__tmp";
        data __xls.%scan(__&argx,1,%str(.));
            set &argx.;
        run;quit;
        libname __xls clear;

        data _null_;z=sleep(1);run;quit;

        options noxwait noxsync;
        /* Open Excel */
        x "'C:\Program Files\Microsoft Office\OFFICE14\excel.exe' &__tmp";
        run;quit;

    %mend xlsha;

    %macro xplo ( AFSTR1 )/cmd des="Type xplo ONEaTWO and exploded letters will be saved in past buffer. Use lower case for spaces";
    note;notesubmit '%xploa';

    %mend xplo;

    %macro xploa
    /  des = "Exploded Banner for Printouts";

    options noovp;
    title;
    footnote;

    %let uj=1;

    %do %while(%scan(&afstr1.,&uj) ne );
       %let uj=%eval(&uj+1);
       %put uj= &uj;
    %end;

    data _null_;
       rc=filename('__xplo', "%sysfunc(pathname(work))/__xplo");
       if rc = 0 and fexist('__xplo') then rc=fdelete('__xplo');
       rc=filename('__xplo');

       rc=filename('__clp', "%sysfunc(pathname(work))/__clp");
       if rc = 0 and fexist('__clp') then rc=fdelete('__clp');
       rc=filename('__clp');
    run;

    filename ft15f001 "%sysfunc(pathname(work))/__xplo";

    * format for proc explode;
    data _null_;
    file ft15f001;
       %do ui=1 %to %eval(&uj-1);
          put "D";
          put " %scan(&afstr1.,&ui)";
       %end;
    run;

    filename __clp "%sysfunc(pathname(work))/__clp";

    proc printto print=__clp;
    run;quit;

    proc explode;
    run;

    filename ft15f001 clear;
    run;quit;
    proc printto;
    run;quit;

    filename __dm clipbrd ;

       data _null_;
         infile __clp end=dne;
         file __dm;
         input;
         putlog _infile_;
         put _infile_;
         if dne then put / "#! &afstr1 ;";
       run;

    filename __dm clear;

    %mend xploa;

    /*              _ _     _
    | | _____ _   _| (_)___| |_
    | |/ / _ \ | | | | / __| __|
    |   <  __/ |_| | | \__ \ |_
    |_|\_\___|\__, |_|_|___/\__|
              |___/
    */

    %macro keylist / cmd des="Type keylist and a list og your function keys will be in the log";
       note;notesubmit '%keylista;';
       run;
    %mend keylist;

    %macro keylista;
       data _null_;
         cmd=cats('filename _cat catalog "sasuser.profile.','dmkeys.keys',
         '";data _null_;infile _cat;input;putlog _infile_ $171. ;run;quit;');
         putlog cmd;
         call execute(cmd);
       run;
    %mend keylista;

    /*
     data class;
      set sashelp.class;
      usubjid=put(age,z5.);
    run;quit;
    */


    /*
    __  ___ __  _   _
    \ \/ / `_ \| | | |
     >  <| |_) | |_| |
    /_/\_\ .__/ \__, |
         |_|    |___/
    */

    %macro xpy/cmd parmbuff des='Type xpy roger for program banner with large font https://github.com/rogerjdeangelis/utl_program_banner


    /* see https://github.com/rogerjdeangelis/utl_program_banners */

    %let afstr1=&syspbuff;

    note;notesubmit '%xpya';

    %mend xpy;

    %macro xpya;

    %local uj revslash;

    options noovp;
    title;
    footnote;

    data _null_;
       rc=filename('__xplp', "%sysfunc(pathname(work))/__xplp");
       if rc = 0 and fexist('__xplo') then rc=fdelete('__xplp');
       rc=filename('__xplp');
    run;

    %let revslash=%sysfunc(translate(%sysfunc(pathname(work)),'/','\'));
    %put &=revslash;
    run;quit;

    * note uou can altename single and double quotes;
    %utl_submit_py64_310(resolve('
    import sys;
    from pyfiglet import figlet_format;
    txt=figlet_format("&afstr1.", font="standard");
    with open("&revslash./__xplp","w") as f:;
    .    f.write(txt);
    '));

    filename __dm clipbrd ;

       data _null_;
         infile "%sysfunc(pathname(work))/__xplp" end=dne;
         file __dm;
         input;
         _infile_=translate(_infile_,"`","'");
         if _n_=1 then substr(_infile_,1,2)='/*';
         putlog _infile_;
         put _infile_;
         if dne then do;
            put '*/';
            putlog '*/';
         end;
       run;

    filename __dm clear;

    %mend xpya;
    ;;;;
    run;quit;

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
