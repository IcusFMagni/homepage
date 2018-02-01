# angular-material-intro

## Background
Bootstrap is the most popular web design framework

Not the only one though: other tech companies have released their own frameworks, including Tinder, AirBnB, Ebay, and Google

Today, we're talking about google

Angular and Angular Material are both created and maintained by Google

Why not just use Bootstrap?

- Bootstrap requires jQuery to properly work
- Angular documentation suggests not using both Angular and jQuery to avoid errors
- There is an option called UI Bootstrap that works with Angular, but that is outside the scope of this lecture, and may not always be supported
- One downside to Angular Material is that it requires a lot of dependencies, which is why I have this repo with all of the necessary dependencies already sourced in
- Need to make sure that version numbers match with some of the dependencies, otherwise it will not work

[Angular Material Documentation](https://material.angularjs.org/latest/)

## Layout
Bootstrap is based on a grid layout, everything laid out in rows and columns

Angular Material is based on a flex layout

- Allows any div to build rows/columns
- Can set layouts for specific screen size breakpoints (desktop vs tablet vs phone)
- Child divs have flex attribute, so they will resize when necessary

Angular Material documentation is full of code snippets you can use and play around with

html:

```HTML
<body ng-app="myApp">
	<div layout="column">
		<header>
			<h1>Angular Material is Awesome!</h1>
		</header>
		<div ng-controller="MaterialController as mc" class="md-padding">
			<div layout="row" layout-xs="column"
				<div flex class="first-box box">
					I'm above on mobile, and to the left on larger devices
				</div>
				<div flex class="second-box box">
					I'm below on mobile, and to the right on larger devices
				</div>
			</div>
		</div>
	</div>
</body>
```
Can also set divs to be specific widths

```HTML
<div layout="row">
	<div flex="30" flex-gt-sm="20" class="first-box box">
		Here flex is 30
	</div>
	<div flex="70" flex-gt-sm="60" class="second-box box">
		Here flex is 70
	</div>
	<div flex hide-sm hide-xs class="third-box box">
		This one hides sometimes
	</div>
</div>
```
Can add CSS like normal

```CSS
header {
	width: 100%;
	padding-top: 20px;
	padding-bottom: 20px;
	background-color: PowderBlue;
}

h1 {
	text-align: center;
	color: black;
	font-size: 3em;
}

.box {
	height: 200px;
	color: white;
	font-size: 2em;
	padding: 10px;
}

.first-box {
	background-color: turquoise;
}

.second-box {
	background-color: tomato;
}

.third-box {
	background-color: springgreen;
}
```

## Alerts / Dialogs
May have heard of Sweet Alerts from solo projects

html:

```HTML
<div layout="row" layout-wrap layout-margin layout-align="center">
	<md-button class="md-primary md-raised" ng-click="mc.showAlert($event)">Alert Dialog</md-button>
</div>
```

controller:

```JavaScript
myApp.controller('MaterialController', function($mdDialog) {
	console.log('MaterialController loaded!');
	
	var vm = this;
	
	vm.showAlert = function(ev) {
		$mdDialog.show(
			$mdDialog.alert()
			.parent(angular.element(document.querySelector('#popupContainer'))
			.clickOutsideToClose(true)
			.title('This is an alert title')
			.textContent('You can specify something here')
			.ariaLabel('Alert Dialog Demo')
			.ok('Got it!')
			.targetEvent(ev)
		);
	};
};
```

$event is used to scope events

## Toasts
Doesn't block UI, just alerts user

Mimics Android design

html:

```HTML
<md-button class="md-primary md-raised" ng-click="mc.openToast($event)">Show Toast</md-button>
```

controller:

```JavaScript
myApp.controller('MaterialController', function($mdDialog, $mdToast) {
	vm.openToast = function(ev) {
		$mdToast.show($mdToast.simple().textContent('Hello!'));
	};
});
```

## Centering
Anyone who has tried to center something horizontally and vertically at the same time knows that it's tough!

html:

```HTML
<div layout="row" layout-align="center center">
	<div class="box first-box">One</div>
	<div class="box second-box">Two</div>
	<div class="box third-box">Three</div>
</div>
```

## Material Icons
[Material Icons Documentation](https://material.io/icons/)

html:

```HTML
<i class="material-icons">local_pizza</i>
```
