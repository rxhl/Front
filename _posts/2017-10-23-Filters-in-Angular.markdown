---
layout: post
title: Filters in AngularJS 
comments: true
---

Filters provide an easy way to format the view. In this post, we will explore in-built and custom filters in AngularJS. 

<img class="no-shadow" alt="AngularJS logo" src="/Front/assets/img/8/ng.png" style="width: 30%; height: auto; display: block; margin: 0 auto;"/>

Recently, I switched back to Angular (1.6x) after a brief stint at React due to work requirements and have been enjoying the transition quite a bit. OK, let's get started!  

### **Filters in AngularJS**

>Filters can be added in AngularJS to format data.

Thank you [w3schools](https://www.w3schools.com/), it could not have been more self-referential. Angular provides a bunch of in-built filters to format data like currency and date among others. They can be used directly with the data binding expressions with the `|` operator.

**index.html**

{% highlight html%}
{% raw %}
<!DOCTYPE html>
<html ng-app="myModule">
<head>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.6/angular.min.js"></script>
    <script src="js/main.js"></script>
</head>
<body>
    <div ng-controller="myController">
        <p>Name: {{ ben.name | uppercase }}</p>
        <p>DOB: {{ ben.dob | date:"dd/MM/yyyy" }}</p>
        <p>Salary: {{ ben.salary | currency }}</p>
    </div>
</body>
</html>
{% endraw %}
{% endhighlight %}

**js/main.js**

{% highlight javascript%}
var myApp = angular
	.module("myModule", [])
	.controller("myController", function($scope) {
		var ben = {
			name: "Ben",
        		dob: new Date("November 23, 1993"),
        		salary: 100000,
		}    
		$scope.ben = ben;
	});
{% endhighlight %}

Here is what the DOM renders.

{% highlight html%}
Name: BEN 
DOB: 23/11/1993 
Salary: $100,000.00
{% endhighlight %}

The currency filter uses `$` by default but can be changed as needed.

{% highlight html%}
{% raw %}
{{ ben.salary | currency: "GBP" }}
{% endraw %}
{% endhighlight %}

Now that's nifty. Angular can recognize the types and format accordingly.

### **The filter Filter**

>The filter filter can only be used on arrays, and it returns an array containing only the matching items.

Let's add few cats to `main.js`.

{% highlight javascript%}
var myApp = angular
	.module("myModule", [])
	.controller("myController", function($scope) {
		var animals = ["lion", "tiger", "lynx", "puma", "jaguar", "leopard", "cheetah", "panther"];
		$scope.animals = animals;
	});
{% endhighlight %}

Now if we only want to display animals with an `i` in their names, we can use `filter` with the binding expression in `index.html`.

{% highlight html%}
{% raw %}
<ul>
  <li ng-repeat="x in animals | filter : 'i'">
    {{ x }}
  </li>
</ul>
{% endraw %}
{% endhighlight %}

And it will display only **lion** and **tiger**.

### **Custom Filters**
In-built filters are good, but the custom ones are great! Angular allows us to create our own filters for arrays, objects and everything else. 

Going back to our first example, assume that the gender is stored as a number.

* 1 for male
* 2 for female
* 3 for non-binary

And here is the modified `ben` object.

{% highlight javascript%}
var ben = {
  name: "Ben",
  dob: new Date("November 23, 1993"),
  salary: 100000,
  gender: 3, // dangling comma 
}    
{% endhighlight %}

To display `3` as the corresponding gender title, all we need is to declare a little function in `main.js`.

{% highlight javascript%}
var myApp = angular
  .module("myModule", [])
  .filter("gender", function() {
    return function (gender) {
      switch(gender) {
        case 1: return "Male";
        case 2: return "Female";
        case 3: return "Non-Binary";
      }
    }
  })
  .controller("myController", function($scope) {
    var ben = {
      name: "Ben",
      dob: new Date("November 23, 1993"),
      salary: 100000,
      gender: 3, 
    }
    $scope.ben = ben;
  });
{% endhighlight %}

We just created a custom filter `gender` that can be used within the data binding expression.

{% highlight html%}
{% raw %}
<p>Gender number: {{ ben.gender }}<p>
<p>Gender: {{ ben.gender | gender }}<p>
{% endraw %}
{% endhighlight %}

And its expected result.

{% highlight html%}
Gender number: 3
Gender: Non-Binary
{% endhighlight %}

### **Furthermore**

* [AngularJS Docs for Filter](https://docs.angularjs.org/api/ng/filter/filter)
* [Building custom filters in AngularJS](https://scotch.io/tutorials/building-custom-angularjs-filters)