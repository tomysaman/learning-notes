# cfscript cheat sheet

---

### Assign a variable
```
foo = "bar";
```

### Single Line Comment
```
mojo = 1; // This is a comment
```

### Multiline Comment
```
/* This is a comment
	that can span
	multiple lines
*/
```

### Array Literal
```
fruit = [ "apples", "oranges" ];
```

### Struct Literal
```
fruit = { item1="apples", item2="oranges" };
```

### If / Else If / Else
```
if (fruit IS "apple") {
	WriteOutput("I like apples");
} else if (fruit IS "orange") {
	WriteOutput("I like oranges");
} else {
	WriteOutput("I like fruit");
}
```

### FOR Loop
```
for (i=1; i LTE ArrayLen(array); i=i+1) {
	WriteOutput(array[i]);
}
```

### FOR IN Loop (Structure/Array)
```
data = { item1="a", item2="b" };
// data = [ "a", "b" ];
for (item in data) {
	WriteOutput(item);
}
```

#### FOR IN Loop (Query)
```
cars = QueryNew( "make,model", "cf_sql_varchar,cf_sql_varchar", [["Honda","Civic"],["Toyota","Camery"]] );
for (car in cars) {
	WriteOutput(car.make & " " & car.model & "<br>");
}
```

### While Loop
```
x = 0;
while (x LT 5) {
	x = x + 1;
	WriteOutput(x);
}
```

### Do / While Loop
```
x = 0;
do {
	x = x+1;
	WriteOutput(x);
} while (x LTE 0);
```

### Switch Case
```
switch(fruit) {
	case "apple":
		WriteOutput("I like Apples");
		break;
	case "orange":
		WriteOutput("I like Oranges");
		break;
	default: 
		WriteOutput("I like fruit");
}
```

### Try / Catch / Throw / Finally / Rethrow
```
try {
	throw(message="Oops", detail="xyz");
} catch (any e) {
	WriteOutput("Error: " & e.message);
	rethrow;
} finally {
	WriteOutput("I run even if no error");
}
```

### CFInclude
```
include "template.cfm";
```

### CFSavecontent
```
savecontent variable="result" {
	writeoutput("some content...");
}
```

### Continue Statement
```
for (row in query) {
	if (row.skip) {
		continue; // skip the rest of the codes for this iteration, but stay in the loop
	}
	//...
}
```

### Break Statement
```
for (row in query) {
	if (row.currentrow > 10) {
		break; // break out of the loop
	}
	...
}
```

### Component
```
component extends="fruit" {
	property name="variety" type="string";
	
	public boolean function isGood() { 
		return true;
	}
	
	private void eat(required numeric bites) {
		//do stuff
	}
}
```

### Function (Component Method)
```
public boolean function isLarger( required numeric input1, numeric input2 = 0 ) {
	if ( arguments.input1 LT arguments.input2 ) {
		return true;
	} else {
		return false;
	}
}
```

### Transactions
```
transaction {
	//do stuff
	if (good) {
		transaction action="commit";
	else {
		transaction action="rollback";
	}
}
```
