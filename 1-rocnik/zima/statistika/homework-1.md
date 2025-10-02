```sas
data sad.cv1_2_update;
	set sad.cv1_2;
	label ROA="rentabilita aktiv"
		VAddedFmt="přidaná hodnota výroby";
run;

proc print data=SAD.cv1_2_update (obs=10) label;
run;

proc format;
  value VAddedFmt
    1 = "suroviny"
    2 = "polotovary"
    3 = "hromadná výroba"
    4 = "zakázková výroba"
  ;
run;

proc print data=sad.cv1_2_update (obs=10) label;
	format VAdded VAddedFmt.;
run;

proc sort data=sad.cv1_2 out=_cv_1_2_sorted;
	by VAdded;
run;

proc means data=_cv_1_2_sorted n min mean median max std p5 p95;
	by VAdded;
	var ROA;
	format VAdded VAddedFmt.;
run;

proc univariate data=_cv_1_2_sorted noprint;
	by VAdded;
	histogram ROA / normal;
	format VAdded VAddedFmt.;
run;

proc sgplot data=_cv_1_2_sorted;
    format VAdded VAddedFmt.;
    vbox ROA / category=VAdded;
    xaxis label="Přidaná hodnota výroby"; 
    yaxis label="Rentabilita aktiv (ROA)";
run;
```
