# javascript scripting
... Introduction to control structures with javascript. 

Two lectures ago we spoke about programming in general terms. The foundational programming control structures were mentioned, these being selection, iteration and sequence:

![oracle programming](http://docs.oracle.com/cd/A87860_01/doc/appdev.817/a77069/03_strua.gif "oracle programming")

This looks at these control structures as they are implemented in javascript.

##Sequence

```
Javascript Rocks!

<script>
  document.write("Hello World!");
  document.write("<br />");
  document.write(" so there!");
</script>
```

You can see this in action at [https://rhildred.github.io/javascriptscripting/index.html](https://rhildred.github.io/javascriptscripting/). The general idea is that when the computer performs a sequence it does one thing after another.

##Iteration

Someone in class nailed it when they said that iteration will happen forever until an ending condition is met. In honour of my love of marshmallow filled cookies, I present the following example message to my wife, who buys groceries.

```
<script>
var x = 0;
while(x < 100){
  document.write("I love Vivas! Please buy some.");
  document.write("<br />");
  x = x + 1;
}
</script>
```

You can see this is action at [https://rhildred.github.io/javascriptscripting/ilovevivas.html](https://rhildred.github.io/javascriptscripting/ilovevivas.html). Of course this is much faster than me typing this over and over.

##Selection

```
<script>
var score = 75;
if(score > 55){
  document.write("You Passed");
}else{
  document.write("You failed");
}
document.write("<br />");
</script>

```

You can see this is action at [https://rhildred.github.io/javascriptscripting/youpassed.html](https://rhildred.github.io/javascriptscripting/youpassed.html). This is mildly interesting, but to change the message that appears, you need to edit the code.  What we really need to do  is code it once, then anyone can figure out their passing or failing status.

##Selection with a user interface

The Angular team from Google theorizes that user interfaces and triggering events [are best done declaratively](https://en.wikipedia.org/wiki/AngularJS#Philosophy). I agree. For our user interface we will need an html form:

```
<form>
<label>Input test score</label><input />
<button>Get Status</button>
<p>You passed or failed would go here</p>
</form>
```

Angular lets us link the event of clicking the button, declared in our form, to an imperative selection between passing and failing.

```
<script src="https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.3.15/angular.js"></script>
<script>
  angular.module("myApp", []).controller("myCtrl", function ($scope) {
    $scope.calculate = function(){
      if($scope.score > 55){
        $scope.message = "you passed!"
      }else{
        $scope.message = "you failed";
      }
    }
  });
</script>
<form ng-app="myApp" ng-controller="myCtrl">
<label>Input test score</label><input ng-model="score" />
<button ng-click="calculate()">Get Status</button>
<p>{{message}}</p>
</form>
```

You can see this is action at [https://rhildred.github.io/javascriptscripting/youpassed.html](https://rhildred.github.io/javascriptscripting/youpassed.html). The whole repository is viewable at [https://github.com/rhildred/javascriptscripting](https://github.com/rhildred/javascriptscripting) Everything that begins with ng- or {{ links javascript code to the html elements. This is a powerful technique for adding a user interface to our programs. Happy Coding!!!