<div align="center">

## isDate\(\)


</div>

### Description

1) Validate a date entered in a text box without having to use multiple boxes for day, month, year.

2) Implement a short, mathematical method

3) Provide feedback about incorrect entries
 
### More Info
 
a date in numeric form, day/month/year, one or two digits for day and month. Assume 2 digit years are for 2000.

Makes use of 400 year cycle calendar for leap years.

Corrected, editted date or "ERROR: " message.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Cecil Denney](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/cecil-denney.md)
**Level**          |Intermediate
**User Rating**    |3.6 (18 globes from 5 users)
**Compatibility**  |ASP \(Active Server Pages\)
**Category**       |[Validation/ Processing](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/validation-processing__4-16.md)
**World**          |[ASP / VbScript](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/asp-vbscript.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/cecil-denney-isdate__4-6605/archive/master.zip)

### API Declarations

Copyright 2001, The Jesse Tree


### Source Code

```
<%
'copyright 2001, The Jesse Tree
'This Web page illustrates the use of the date functions
' Developed by Cecil Denney, Automation consultant to
' The Jesse Tree, 2622 Market Street, Galveston, TX 77550
option explicit
dim i, Date1, Date2
%>
<html>
<head>
<Script Language="JavaScript">
// The IsDate() a short, clean JavaScript function that uses the 400 year cycle
//  calendar to validate a date.
// It accepts one or two digits for the day, month, or year. However, for the year,
//  two digits are assumed to be 2000+
// CheckDate() uses isDate() to check the date and display the result or an error message.
function isDate(theDate)
{
	var dtval = theDate.split("/")
	if (dtval.length != 3) {return "ERROR: Format is 'mm/dd/yyyy'" }
	else {
			var mo = dtval[0]-1+1;
			var day = dtval[1]-1+1;
			var yr = dtval[2]-1+1;
			yr = (yr < 100) ? yr + 2000 : yr;
			if (yr > 9999){return "ERROR: Maximum year 9999."}
			var days = 0
			if (mo >= 13){ return "ERROR: Maximum 12 months." }
	    else {
					switch (mo)
					{
					case 2:
						// for February (implements 400 year cycle calculation)
						days = (((yr%4 == 0 && yr%100 != 0) || yr%400 ==0) ? 29 : 28 );
						break;
					default:
						// for January thru December except February
						days = 30 + ((mo < 8) ? mo%2 : (mo%7)%2);
			   	}
					if (days < day){return "ERROR: Maximum of "+days+" for month "+mo+"."}
					else {return mo+"/"+day+"/"+yr}
					//return dtval[0]-1+1
				 }
	   }
}
function CheckDate(){
var indate = document.all.Users.value;
indate = isDate(indate);
document.all.Calculated.value = indate;
}
</Script>
</head>
<body>
Enter Date: <input id="Users" type="text" name="TestDate" size="30" onblur="CheckDate()"><br>
Calculated: <input id="Calculated" type="text" name="Calculated" size="40">
</body>
</html>
```

