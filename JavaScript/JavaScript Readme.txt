
JavaScript for Client Side Web Application
------------------------------------------

JavaScript can be used for SErver Side web applications also.

Full Stack Developer:
	1) Storage ==> Database / NoSQL
	2) Backend building RESTful API ==> Spring/Spring Boot / JPA
	3) Front End: JS stacks

	JavaScript: Scripting language, loosely typed, dynamic typing
	JavaSCript executes on JS engines
	JS Engines: 
		V8 ==> Google ==> Chrome/ NodeJS
		Chakra => MS ==> IE
		SpiderMonkey -=> FireFox / Adobe Acrobat

	----------
	ES6 [ ES2015] /ES7
	ES5 ==> Javascript version 5
		As of now all browsers support ES5
	--
	Variables in ES5:

	"var" keyword is used to declare a variable

	var name = "Smith";

	var age = 24;

	var employed = false;

	Depending on literals assigned type of data can be:
	string, number, boolean, undefined, null, array, object

	var x; // x is undefined

	var p = null;

	------------------------------

	Functions in JavaScript: keyword "function" is used to declare a function in JS.
	Every function created is an object of "Function" --> extends "Object"

	function add(x,y) {
		return x + y;
	}

	var res = add(4,5); // 9
	res = add("Hello","World"); // HelloWorld
	res = add("Hello",5); // Hello5

	-------

	function add(x,y) {
		console.log(x + y);
	}

	var res = add(4,5); // undefined

	----------------------------------

	Scope of variables in JS:

	a.js
		var g = 100;

		function one() {
			var a = 10;							var b;
			if( g > a) {
				var b = 20; // hoisting ==> hoisted to function scope
				c = 30; // not delcared, implict ==> hoisted to global scope
			}

			console.log(g,a,b,c);
		}
		one();
		console.log(g,c);

	to avoid using variables without delcaration:

		"use strict"; // on top of file

	------------

	Functions are first class members in JS

	var f = function() {

	};

	--------------------------------------------------

	Objects in JS:
		1) JSON
			var obj = {};

		2) using Object
		
			var obj = new Object();
			obj.id = 1;
			obj.name = "Lee";
			obj.getDetails = function() {
				 return this.id + "," + this.name;
			}	

		3) Using Constructor function
			a) Object owned instance methods:
			function Person(id,name) {
				this.id = id;
				this.name = name;
				this.getDetails = function() {
				 				return this.id + "," + this.name;
				}	
			}

			Person(3,"T"); // Don't

			var p1 = new Person(4,"Danny");
			var p2 = new Person(24,"P");

			b) class owned instance methods:

					function Person(id,name) {
						this.id = id;
						this.name = name;
				}
				Person.prototype.getDetails = function() {
				 				return this.id + "," + this.name;
				}	

				var p1 = new Person(4,"Danny");
				var p2 = new Person(24,"P");
				===========

String.prototype.makeItRed = function() { return "<font color='red'>" + this + "</font>" }

document.write("Peter".makeItRed())

	----------------
	Be careful when you format JS files:
	JS: semi-colon insertion
	function add(x,y) {
		return 
			x + y;
	}

	var res = add(4,5); // undefined
==================================================

	DOM : Document Object Model
		==> represent your document [ HTML document] in the form of javascript objects

	JS allows us to acces DOM element using:
		a) document.getElementById("tbl")
			document.getElementById("name")
			returns a single dom element matching the id
		b) document.getElementByTagName("p");
			gets all paragraphs
			returns always an array
	------------------------------------------

	JS is event driven:

	a.js

	 console.log("Hello!!!");
	 document.getElementById("btn").addEventListener("click", function() {
	 	console.log("Clicked!!!")
	 });

	 setInterval(function() {
	 	console.log("Time Please!!!")
	 }, 200)

	 console.log("Bye!!!");
===========================================================
	High Order Functions in JS:
		a) functions which accept function as argument
			map, reduce, filter
		b) functions which return a function



		var res = [6,3,55,11,12,9].filter(function(v) { return v % 2 === 0; });

	var res = customers.filter(function(c) {
		return c.gender === 'female';
	});

	============

	function greeting(msg, name) {
		return msg + " " + name;
	}

	greeting("Good morning", "Roger");
	greeting("Good morning", "Peter");
	greeting("Good morning", "Anna");


	var greet = function(msg) {
				return function(name) {
					return msg + " " + name;	
				}
	}

	 var mg = greet("Good morning");
	 console.log(mg("Harry"));
	 console.log(mg("Tom"));

	 ==================
	 var a = 10;
	 var status = true;
	 
	 function outer() {
	 	function inner() {
	 		console.log(status);
	 	}
	 }
======================================

	ES5 JavaScript==> Most of the browsers support
	ECMA
	ES6 ==> ES2015 features 
		Most of the browsers yet to support ES6.
		Write code in ES6, then transpile to ES5
		Babel and Tracuer are popular traspilers for JS

	1) scope variable and constants
		const PI = 3.14159;
		"let" keyword for scope variable

		var g = 100;

		function test() {
			var a = 10;
			if( g > a) {
				let b = 20; // scope is within the block
			}
		}
	2) Arrow operator [ Lambda ]

		let add = (x,y) => x + y;

	3) default arguments
			
			let add = (x = 5,y = 10) => x + y;

			add(); // 15
			add(3); // 13
			add(1,2); // 3

			Earlier versions:

			function add(x,y) {
				x = x || 5;
				y = y || 10;
				return x + y;
			}

		4) new String literal
			Earlier versions supported: "Test", 'Test'
			New String literal: `` <-- ticks

			var name = "Peter";

			var msg = `
				Welcome to Rakuten, Mr/Mrs. ${name}
				have a nice day
			`;

		5) Deconstruction:

			var colors = [ 'red','green','blue','orange'];
			Old Way:
			var g = colors[1];

			New Way:

			var [ r,g,...others] = colors;

			r ==> "red"
			g ==> "green"

			others ==> ["blue","orange"];

			---------------

			Deconstructing Objects

			var p = {
				"id": 12,
				"name" : "Tim",
				"email" : "tim@rakuten.com"
			};

			//earlier console.log(p.name);

			var {name, email} = p;

			console.log(name);

			6) Modules

			lib.js

			export add = (x,y) => x + y;
			export sub  = (x,y) => x - y;

			mul = (x,y) => x * y;


			other.js

			import {add,sub} from './lib.js';

			console.log(add(4,5));


			Old way:

			<script src="lib.js"></script>
			<script>
				console.log(add(4,5));
			</script>


			Note:

			lib.js

			export default add = (x,y) => x + y;



			other.js

			import  add  from './lib.js';

			console.log(add(4,5));


			This is also valid:
			import * as lib from './lib.js';

			console.log(lib.add(4,5));

		7) Promise API:
			// Synchronous:
			function doTask() {

			}

			let res = doTask();
			// line is blocked, will execute only after doTask() completes
			console.log("Print!!");


			// Asynchronous
			function doTask() {

			};

			doTask().then(function(data) {
				use data
			},
			function(err) {
				error code
			}
			);

			console.log("Test!!!!"); // not blocked
================================================

	NodeJS: Environment built using V8 JS engine.
	Where can I use this?
		--> Built server side applications using JS as language
			Express framework similar to Spring boot for building RESTful web services.
		--> An environment to build client side web application
		
		package.json ==> pom.xml

		----------------
		Unit testing JAva: JUnit/TestNG

		Unit Testing JavaScript:
			jest/ Mocha / jasmine
			we also have some assertion libraries : chaijs

	================

	import is ES 6 module system

	require() is commonJS module system

	NodeJS by default uses commonJs module system

	Testing is about AAA : AssembleActionAssert

	describe() is to assemble

	eact test is done using "test" or "it"

	================

	JS build tools:
		a) GRUNT, GULP, WEBPACK

	Grunt is a JavaScript task runner, a tool used to automatically perform frequent tasks such as minification, compilation, unit testing, and linting. It uses a command-line interface to run custom tasks defined in a file. 

	Development Code ==> Production Code

	1) Development code is modularized with many "js" files.
		In Product loading all these files is not feasable

		<script src="a.js"></script>
		<script src="b.js"></script>
		<script src="c.js"></script>
		<script src="d.js"></script>

	2) Code needs to be minified and uglified
		Minification is a process of removing "white space"
		Uglify: converts big names to smaller names
			function addInteger ==> function ai
			_o, _a


	3) "linting" check your development for coding conventions and stds
		same as "checkstyle/spotbugs/PMD" for Java
	4) Unit testing and code coverage
	5) we may write code in "typescript" or "ES6/7"
		which needs to be converted to "ES5" for browser support

	==========================================================

	Clientside Web application development.

	Handling DOM at low level and creating pages is difficult

	document.createElement("div");

	document.getElementById("app");

	We can use View Template Libraries
		Popular Template Libraries:
			Client side
			a) Underscore
			b) Mustache
			c) Handlebars
			Server side
			a) Pug
			b) EJS
			c) Jade
	We can use DOM handling libraries: jQuery
	
	$("<div/>");

	equal to document.createElement("div");

	$("#app");

	equal to document.getElementById("app");

	===========

	We have Client side web application frameworks:
	1) Backbone
	2) Angular

	---

	React is a template library
	---------------------------
	Who are using it? Facebook, Instagram, Reddit, Netflix

	Example:
	<div id="app"></div>

	// functional component in React
	// returns JSX ==> JavaScript + XML
	function Employee() {
  		return (
    		<div>
      			Employee Information !!!
    		</div>
  			);
	};

	ReactDOM.render(<Employee/>, document.getElementById("app"));


	===

	<div id="app">
		<Employee />
	</div>


	function Employee({props}) {
  return (
    <div>
      Employee Information !!!
    </div>
  );
};

class Employees extends React.Component {
		state = {
			"emps" : ["Raj","Kumar","Anitha","Swetha"]
		};
  		render() {
  			return (
         		 <div>
  				 	  {
  				 	  	this.state.emps.map(e => {
  				 	  		return <Employee name={e} age ="24" />
  				 	  	})
  				 	  }
          		 </div>
  			);
  		}
	}


 
	function Employee(props) {
  		return (
    		<div>
     		 Employee {props.name}
    		</div>
  		);
	};

	===============

	npx create-react-app productapp

	is same as:
	a) npm i -g create-react-app
	   create-react-app productapp
	   =========

	   const data =[  
   {  
      "name":"Baked Salmon",
      "ingredients":[  
         {  
            "name":"Salmon",
            "amount":1,
            "measurement":"l lb"
         },
         {  
            "name":"Pine Nuts",
            "amount":1,
            "measurement":"cup"
         },
         {  
            "name":"Butter Lettuce",
            "amount":2,
            "measurement":"cups"
         },
         {  
            "name":"Yellow Squash",
            "amount":1,
            "measurement":"med"
         },
         {  
            "name":"Olive Oil",
            "amount":0.5,
            "measurement":"cup"
         },
         {  
            "name":"Garlic",
            "amount":3,
            "measurement":"cloves"
         }
      ],
      "steps":[  
         "Preheat the oven to 350 degrees.",
         "Spread the olive oil around a glass baking dish.",
         "Add the salmon, garlic, and pine nuts to the dish.",
         "Bake for 15 minutes.",
         "Add the yellow squash and put back in the oven for 30 mins.",
         "Remove from oven and let cool for 15 minutes. Add the lettuce and serve."
      ]
   },
   {  
      "name":"Fish Tacos",
      "ingredients":[  
         {  
            "name":"Whitefish",
            "amount":1,
            "measurement":"l lb"
         },
         {  
            "name":"Cheese",
            "amount":1,
            "measurement":"cup"
         },
         {  
            "name":"Iceberg Lettuce",
            "amount":2,
            "measurement":"cups"
         },
         {  
            "name":"Tomatoes",
            "amount":2,
            "measurement":"large"
         },
         {  
            "name":"Tortillas",
            "amount":3,
            "measurement":"med"
         }
      ],
      "steps":[  
         "Cook the fish on the grill until hot.",
         "Place the fish on the 3 tortillas.",
         "Top them with lettuce, tomatoes, and cheese."
      ]
   }
];

============

ReactDOM.render(<Menu title="Delicious Recipes" recipes={data}/>, document.getElementById('root'))

============
state = {
        "filterText" : "",
        products : [
            {id: 1, name: "iPhone"},
            {id: 2, name: "Oppo"},
            {id: 3, name: "iPhone XR"},
            {id: 4, name: "One plus 7"}
        ],
        complete : [
            {id: 1, name: "iPhone"},
            {id: 2, name: "Oppo"},
            {id: 3, name: "iPhone XR"},
            {id: 4, name: "One plus 7"}
        ]
    };


	   






	


	 