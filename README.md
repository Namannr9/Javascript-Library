
# Javascript-library

In this project I created a Javascript library , which simplifies Javascript programming
and also easy to implement.Using this library user can create some components as well as validate 
form and handle ajax(GET/POST) request.

# Features:
- Handle ajax GET and POST type request.
- Form validation.
- Fill comboBox.
- Creating Accordion.
- Creating modal.

# Sending GET type request

```
<script> 
function getDesignation()
{
let titleSpan=$$$("title");
titleSpan.html("");
let code=$$$("code").value();
$$$.ajax({
"url":"servletTwo",
"data":{
"code":code
},
"methodType":"GET",
"success":function(responseData){
// code 
},
"failure":function(){
//code
}
});
}
</script>

```
```
<h1>GET Type request with data Example</h1>
Enter code <input type='text' id='code'>
<button type='button' onclick='getDesignation()'>Get Designation</button><br>
<br>
Title <span id='title'></span>
<br>
<a href='index.html'>Home</a>
```
# Sending POST type request

```
<script>
function saveEnquiry()
{
var firstName=$$$("firstName").value();
var lastName=$$$("lastName").value();
var age=$$$("age").value();
var customer={
"firstName" : firstName,
"lastName" :  lastName,
"age" : age
};
var whatever=$$$("whatever");
whatever.html("");
$$$.ajax({
"methodType":"POST",
"url":"servletThree",
"data":customer,
"sendJSON":true,
"success":function(responseData){
var customer=JSON.parse(responseData);
var a="First Name: "+customer.firstName+"<br>";
a=a+"Last Name: "+customer.lastName+"<br>";
a=a+"Age: "+customer.age;
whatever.html(a);
},
"failure":function(){
alert("Some problem");
}
});
}
</script>
```
```
<body>
<h1>Post type request Example</h1> 
<label>First Name </label><br><input type='text' id='firstName'><br><br>
<label>Last Name </label><br><input type='text' id='lastName'><br><br>
<label>Age </label><br><input type='text' id='age'><br><br>
<button type='button' onclick='saveEnquiry()'>Save</button><br>
<br>
<div id='whatever'></div>
</body>
```
# Form validation

```
<script>
// TMJRock user script starts here
function doSomething()
{
return $$$("someForm").isValid({
"nm":{
"required":true,
"maxLength":20,
"errorPane":"nmErrorSection",
"errors":{
"required":"Name required",
"maxLength":"Name cannot exceed 20 characters"
}
},
"ad":{
"required":true,
"errorPane":"adErrorSection",
"errors":{
"required":"Address required"
}
},
"ct":{
"invalid":-1,
"errorPane":"ctErrorSection",
"errors":{
"invalid":"Select city"
}
},
"gender":{
"required":true,
"errorPane":"genderErrorSection",
"errors":{
"required":"select gender"
}
},
"agree":{
"requiredState":true,
"displayAlert":true,
"errors":{
"requiredState":"Select I agree checkbox"
}
}
});
}
</script>
```
```
<body>
<h1>Form validation example</h1>
<form id='someForm' onsubmit='return doSomething()'>
<label>Name</label> <br><input type='text' name='nm' id='nm'> <span id='nmErrorSection'></span><br><br>
<label>Address</label> <br><textarea id='ad' name='ad'></textarea> <span id='adErrorSection'></span><br><br>
<label>Select city</label><br>
<select id='ct' name='ct'>
<option value='-1'>select city</option>
<option value='1'>Bombay</option>
<option value='2'>Delhi</option>
<option value='4'>Indore</option>
<option value='5'>Ujjain</option>
<option value='6'>Dewas</option>
</select>
 <span id='ctErrorSection'></span><br>
<br><br>
<label>Gender &nbsp;&nbsp;&nbsp;</label><br>
Male <input type='radio' name='gender' id='ml' value='M'>&nbsp;&nbsp;&nbsp;
Female <input type='radio' name='gender' id='fe' value='F'>&nbsp;&nbsp;&nbsp;
 <span id='genderErrorSection'></span>
<br><br>
<input type='checkbox' name='agree' id='ag' value='y'> I agree?
<br><br>
<button type='submit'>Registor</button>
</form>
</body>
```

## Output

![formValidation](https://user-images.githubusercontent.com/96347009/147807523-6ca434be-c198-41ea-ac88-d9b0e735729a.png)

# Fill ComboBox
```
<script>
function populateDesignations()
{
$$$.ajax({
"url": "servletOne",
"methodType": "GET",
"success": function(responseData){
var designations=JSON.parse(responseData);
$$$("designationCode").fillComboBox({
"dataSource": designations,
"text" : "title",
"value": "code",
"firstOption" : {
"text": "<select designation>",
"value" : "-1"
}
});
},
"failure": function(){
alert("Some problem");
}
});
}
window.addEventListener('load',populateDesignations);
</script>
```
```
<body>
<h1>Fill ComboBox Example</h1>
<select id='designationCode'>
</select>
</body>
```
## Output
![fillComboBox](https://user-images.githubusercontent.com/96347009/147808279-a3c18617-37fe-46e5-a545-6587dace75e5.png)

# Creating Accordion

```
<h1>Accordion Example</h1>
<div accordian="true">
<h3 accordianHeadrerBackgroundColor="#324B67">Some Heading.1..</h3>
<div accordianBackgroundColor="#ECEBDF ">
<h3>Advantages of Reading</h3>
When you learn a language, listening, speaking and writing are important, but reading can also be very helpful. 
<ul>
    <li>Builds your skill...</li>
    <li>Improves memory....</li>
    <li>Improves writing skills.</li>
    <li>many more...</li>
</ul>

There are many advantages associated with reading, including:
You will usually encounter new words when you read. If there are too many new words for you, then the level is too high
and you should read something simpler. But if there are, say, a maximum of five new words per page, you will learn this
vocabulary easily. You may not even need to use a dictionary because you can guess the meaning from the rest of the text
(from the context). Not only do you learn new words, but you see them being used naturally.
</div><br>
<h3 accordianHeadrerBackgroundColor="#F4CC14">Some Heading ..2..</h3>
<div>
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something

</div><br>
<h3 accordianHeadrerBackgroundColor="#4D1313">Some Heading ..3...</h3>
<div>
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
something something
</div>
</div>
<br>
<hr>
<br>
<div accordian='true'>
<h3>Heading 1...</h3>
<div>
Right now you are reading English. That means that you are using your brain in a very active way. Reading is a very
active process. It is true that the writer does a lot of work, but the reader also has to work hard. When you read a
text, you have to do some or all of these:
When you learn a language, listening, speaking and writing are important, but reading can also be 

</div><br>
<h3>Heading 2...</h3>
<div>
<h3>Advantages of Reading</h3>
When you learn a language, listening, speaking and writing are important, but reading can also be very helpful. There
are many advantages associated with reading, including:
You will usually encounter new words when you read. If there are too many new words for you, then the level is too high
and you should read something simpler. But if there are, say, a maximum of five new words per page, you will learn this
vocabulary easily. You may not even need to use a dictionary because you can guess the meaning from the rest of the text
(from the context). Not only do you learn new words, but you see them being used naturally.

</div><br>
<h3>Heading 3....</h3>
<div>
When you learn a language, listening, speaking and writing are important, but reading can also be very helpful. There
are many advantages associated with reading, including:
You will usually encounter new words when you read. If there are too many new words for you, then the level is too high
and you should read something simpler. But if there are, say, a maximum of five new words per page, you will learn this
vocabulary easily. You may not even need to use a dictionary because you can guess the meaning from the rest of the text
(from the context). Not only do you learn new words, but you see them being used naturally.
</div><br>
</div>
```
## Output

![AccordionImg](https://user-images.githubusercontent.com/96347009/147807405-627a5749-39f4-4af6-adf2-d286c2833bf8.png)



# Creating modal

```
<script>
// user written functions
function abBeforeOpening()
{
return true;
}
function abOpened()
{
}
function abBeforeClosing()
{
return true;
}
function abClosed()
{
}

function createModal1()
{
$$$.modals.show("ab");
}
</script>
```
```
<button style='background:#1d60c4dc;border:none;border-radius:2px;padding:10px;font-size:18px;color:#FFF' onclick='createModal1()'>Open Modal</button>
<div id='ab' style='display:none' forModal='TRUE' size="600x300" header="Modal Heading" footer="Modal footer" maskColor="#E9E5D5" modalBackgroundColor="#EEF1EF	" closeButton="true" beforeOpening="abBeforeOpening()" afterOpening="abOpened()" beforeClosing="abBeforeClosing()" afterClosing="abClosed()">

some text in model some text in model
some text in model some text in model
some text in model some text in model

<br>
<hr>
<h4>You can write here something...</h4><input type='text' id='myTextBox' value='you can write here...'>
<hr>
some text in model some text in model<br>
some text in model some text in model<br>
some text in model some text in model<br>
some text in model some text in model<br>
some text in model some text in model<br>
some text in model some text in model<br>
some text in model some text in model<br>
some text in model some text in model<br>
This is last line.
</div>
```

## Output
![modal](https://user-images.githubusercontent.com/96347009/147807531-9577a30a-22d3-43c6-af47-747703bb5122.png)

## Installing 
- Step 1 - Download JSLibrary.js file and JSLibraryStyle.css file.
- Step 2 - Include this JS and css file to your file.

`<script src='js/JSLibrary.js'></script>`

`<link rel="stylesheet" href="css/JSLibraryStyle.css">`
