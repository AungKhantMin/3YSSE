The All Things You need to know about Chapter 9 (Working With Form)

Form

syntax
```html
<form action="File To Handle Form Data" method="POST or GET">
	Input Method Here
</form>
```
Input Method

1. Text Input

syntax

```html
<label for="Name To Map With Input Id"></label>
<input type="text" name="Variable Name We will Use in PHP" id="Name To Map With Label">
```

2. Password Input

syntax
```html
<label for="Name To Map With Input Id"></label>
<input type="password" name="Variable Name We will Use in PHP" id="Name To Map With Label">
```
3. Radio Input

syntax

```html
<label for="Name To Map With Input Id"></label>
<input type="radio" name="Variable Name We will Use in PHP" id="Name To Map With Label">
```

4. Checked Box

syntax

```html
<label for="Name To Map With Input Id"></label>
<input type="checkbox" name="Variable Name We will Use in PHP" id="Name To Map With Label">
```

5. Submit Buttons
Use To Submit The Form Values

syntax

```html
<input type="submit" name="Variable Name We will Use in PHP" value="Submit Or What Ever You Want To Show In Button">
```

6. Reset Button
Use To Reset Form

syntax

```html
<input type="reset" name="Variable Name We Will Use In PHP" value="Reset Or What Ever You Want To Show In Button">
```

7. Select Box

- Single Select Box

syntax

```html
<select name="Variable Name We Will Use In PHP" size="1">
	<option value="Value We Will Use In PHP">Name Of Choice Here</option>
</select>
```

8. Multi Select Box

syntax

```html
<select name="eg: choice[]" multiple="multiple" size="What Ever You Want or Numbers Of Options">
	<option value="Value We Will Use In PHP">Name Of Choice Here</option>			
</select>
```

Note That We will get array when we receive it

9. Text Area

syntax

```html
<label for="Name To Map With Input Id"></label>
<textarea name="Variable Name We Will Use In PHP" id="Name To Map With Label" rows="rows size in Numbers"  cols="clos size in Numbers"></textarea>
```

10. Hidden Input

```html

	<input type="hidden" name="step" value="1">

```


Usually, There Are Two Method To Sent and receive the data from html form

1. GET Method

syntax

```php
$_GET['name we give in html form']
```
2. POST Method

```php
$_POST['name we give in html form']
```

Note That, We can only use the same method for sending and receiving

For Each Loop To Play With Array

sytnax

```php
foreach ($array as $value){
	here code
}
```


Validate Form Logic Code

#### Single Step Form
 These Following Code is Enough For Validation But We need To Conisdered How We will Show The Error To User

```php
if (!$_POST['submit']){  // Check Any Value Is Sent Or Not
	displayForm(array()) // If There Is No Value We will Show The From To User To Fill IN
}
else{ // If There Is Value We can know that the form data is already sent

	// We will Do Error Checking In This Block

	$requireFields = array(require field name here); // we will check if there is required data or not using this array
	$missingFields = array();  // we will add missing field name in this array

	foreach ( $requireFields as $require){
		if (!isset($_POST['$require'] or !$_POST['require'])){ // We check That if POST value of Require field is set or not
			$missingFields[] = $require;  // if not we will add thems to require field
		}
	}

	if($missingFields){
		displayForm($missingFields); // if there is error we will show the display form again
	}
	else{
		displayThanks(); // if there is no error we will show thanks message
	}
}

```

Error Messaging Logic Code

```php
// These Following Code Show the error to user



function displayForm($missionFields){
	<label <?php validateValue($FieldName, $missingFields); ?> ></label>
	<input type="text" name="first_name" value="<?php setValue('first_name'); ?>" >
	<input type="password" name="password" value="" > 	
	<input type=”radio” name=”gender” id=”genderFemale” value=”F”<?php setChecked( “gender”, “F” )?> />
	<option value=”superWidget”<?php setSelected( “favoriteWidget”,“superWidget” ) ?>>The SuperWidget</option>
}

// ValidateValue Function Is Use To Checked Is This Field Is Missing Or No
// If missing We Will print and css class and show error

function validateValue($fieldName, $missingFields){
	if(in_array($fieldName, $missingFields)){  // in_array() Function Check That Is The First Parameter is In the Array Or not
		echo "class='error'";
	}
}

function setValue($fieldName){
	if($_POST['$fieldName'] and isset($_POST['$fieldName'])){ // We checked Is there is any value ? if yes we will show it to user
		echo "$_POST[$fieldName]";
	}
}

function setChecked($fieldName, $fieldValue){
	if ($_POST['$fieldName'] and $_POST['$fieldName'] == '$fieldValue') {
		echo "checked='checked'";
	}
}

function setSelected($fieldName, $fieldValue){
	if ($_POST['$fieldName'] and $_POST['$fieldName'] == '$fieldValue') {
		echo "selected='selected'";
	}
}
```


###	Multiple Step Form Logic

#### We divide Registration Form Into Multiple Step So First Thing we need to Considered is how to carry data and Registration step We will use hidden input to carry data and step. Validation And Setting Value Are the Same With Single Form


Logic Code Of Multi Step

```php

//We Checked if there is step value post data or not. if there is step value
// we will call the function corresponding to the step
// if not we will show the first step of the form

if (isset($_POST['step']) and ($_POST['step'] >=1 and $_POST['step'] <=3) ) {
	call_user_func(processStep.(int)$_POST['step']);
}
else {
	displayStep1();
}

function processStep1(){   // We will show second step in process step1
	displayStep2();					 // Because  We already show the first step to user if there is no value in $_POST['step']
}

function processStep2(){
	if (isset($_POST['submit'])) {						// Here We will Check If there is any submit value
		if ($_POST['submit'] == "< Back") { 		// If There is value we will check and run
			displayStep1();
		}
		elseif ($_POST['submit'] == "Next >") {
			displayStep3();
		}
	}
}

function processStep3(){									 // same as above
	if (isset($_POST['submit']) {
		if ($_POST['submit'] == "< Back") {
			displayStep2();
		}
		else {
			displayThanks();
		}
	}
}

```
