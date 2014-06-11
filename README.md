#Ignite UI directives for AngularJS (Preview)
Use the directives found in `igniteui-angular.js` to use [Ignite UI](http://igniteui.com) controls in [AngularJS](http://angularjs.com) pages. [Work with the running samples here](http://igniteui.github.io/igniteui-angular).

#Requirements

- [jQuery](http://www.jquery.com) v1.7 and later
- [AngularJS](http://www.angularjs.org) v1.0 and later
- [Ignite UI](http://www.igniteui.com) 13.1 and later

#Building
Build will produce an obfuscated and minified version of the `src/igniteui-angular.js` in the `dist/igniteui-angular.min.js`.  
The build uses [Grunt](http://gruntjs.com/), so you need [Node.js](http://nodejs.org/) installed on your machine.  
To build the project use the following steps:

1. Open a console in the folder where the **igniteui-angular** project is located
2. Run `npm install`
3. Run `grunt build`

#Getting Started

## Page setup

In the page markup include the Ignite UI AngularJS directives file found in `dist/igniteui-angular.min.js` along with the Ignite UI scripts:

	<script src="jquery.min.js"></script>
	<script src="jquery-ui.min.js"></script>
	<script src="angular.min.js"></script>

	<script src="infragistics.core.js"></script>
	<script src="infragistics.lob.js"></script>

	<script src="igniteui-angular.min.js"></script>
	
Reference the `igniteui-directives` in your AngularJS module:

	var sample_app = angular.module('igniteui-sample-app', ['igniteui-directives']);

## Initializing controls
Controls can be initialized in two ways: 

1. Markup Initialization: directly in an HTML page by using custom tags
2. Controller Initialization: a control placeholder is located in an HTML page, but its initialization options are located in the page controller

<a id="markup"></a>
## Markup Initialization

### Custom tags
Each control implements a custom tag directive where the tag name is formed by splitting each capital letter in the control name with the `-` symbol (This naming convention follows the standard Angular normalization process).

**Note**: It is recommended to use closing tags (`</ig-combo>`) over the self-closing tags (`<ig-combo/>`), because the latter are known to make issues on some browsers (depending on the used document mode).

#### Examples:

- igCombo &rarr; `<ig-combo>`
- igGrid &rarr; `<ig-grid>`  
- igDataChart &rarr; `<ig-data-chart>`  
- igDialog &rarr; `<ig-dialog>`  
- igDateEditor &rarr; `<ig-date-editor>`  
- igEditor &rarr; `<ig-editor>`  
- igMaskEditor &rarr; `<ig-mask-editor>`  
- igNumericEditor &rarr; `<ig-numeric-editor>`  
- igPercentEditor &rarr; `<ig-percent-editor>`  
- igTextEditor &rarr; `<ig-text-editor>`  
- igDatePicker &rarr; `<ig-date-picker>`  
- igTree &rarr; `<ig-tree>`  
- igMap &rarr; `<ig-map>`  
- igUpload &rarr; `<ig-upload>`  
- igVideoPlayer &rarr; `<ig-video-player>`

### Configuring Control Options
Simple type control options (`string`, `number`, `bool` etc.) are configured as an attributes on the control element. The options follow the same naming convention logic as the tag name.

#### Examples:
- igGrid.options.localSchemaTransform &rarr; `<ig-grid local-schema-transform="true">`  
- igCombo.options.caseSensitive &rarr; `<ig-combo case-sensitive="true">`  

Defining complex type control options (`arrays` & `objects`) are configured as a child elements of the main control.

#### Example:

	<ig-grid>
		<features>
			<feature name="Filtering">
			</feature>
		</features>
	</ig-grid>

### Handling events
Binding to control events is done again with attributes. Event attribute names are prefixed with the prefix `event-` followed by the event name delimited with the `-` symbol. Once defined the attribute values corresponds to a function name in the scope so you can gain access to the events.

#### Examples:

- igGrid.events.dataBind &rarr; `<ig-grid event-data-bind="dataBindHandler">`  
- igCombo.events.textChanged &rarr; `<ig-combo event-text-changed="textChangedHandler">`  
- igDateEditor.events.keypress &rarr; `<ig-date-editor event-keypress="keypressHandler">`  

## Controller Initialization
Each control also implements a custom attribute directive where the attribute name is formed by splitting each capital letter in the control name with the `-` symbol (this naming convention follows the standard Angular normalization process) and the attribute value corresponds to the scope object holding the control options.

#### Examples:

- igCombo &rarr; `<div id="combo" data-ig-combo="combo_options"></div>`  
- igGrid &rarr; `<table id="grid" data-ig-grid="grid_options"></table>`  
- igDataChart &rarr; `<div id="chart" data-ig-data-chart="data_chart_options"></div>`  
- igDialog &rarr; `<div id="dialog" data-ig-dialog="dialog_options"></div>`  
- igDateEditor &rarr; `<input id="dialog" data-ig-date-editor="date_editor_options"></input>`  
- igEditor &rarr; `<input id="editor" data-ig-editor="editor_options"></input>`  
- igMaskEditor &rarr; `<input id="editor" data-ig-mask-editor="mask_editor_options"></input>`  
- igNumericEditor &rarr; `<input id="editor" data-ig-numeric-editor="numeric_editor_options"></input>`  
- igPercentEditor &rarr; `<input id="editor" data-ig-percent-editor="precent_editor_options"></input>`  
- igTextEditor &rarr; `<input id="editor" data-ig-text-editor="text_editor_options"></input>`  
- igDatePicker &rarr; `<input id="editor" data-ig-date-picker="date_picker_options"></input>`  
- igTree &rarr; `<ul id="tree" data-ig-tree="tree_options"></ul>`  
- igMap &rarr; `<div id="map" data-ig-map="map_options"></div>`  
- igUpload &rarr; `<div id="upload" data-ig-upload="upload_options"></div>`  
- igVideoPlayer &rarr; `<div id="video" data-ig-video-player="video_options"></div>`

## Two-way Data Binding
The following controls currently support two-way data binding:

1. igGrid
2. igCombo
3. igEditors
4. igTree

**Note**: When using control API methods which modify the data source outside the Angular framework you need to explicitly call [Scope.$apply()](https://docs.angularjs.org/api/ng/type/$rootScope.Scope#$apply) in order to see Angular view updated.

##Testing
There are two kinds of tests in Igniteui-angular: Unit tests and End to End tests. All of them are written in [Jasmine](http://jasmine.github.io/).

####Setup
Simply do:

	npm install

The command is preconfigured and it will also call `bower install` behind the scenes.

####Running Unit Tests
The easiest way to run the unit tests is to use the npm script:

	npm test

This will start the [Karma](http://karma-runner.github.io/0.12/index.html) test runner and execute the tests.

####End to end testing
These tests are run with the [Protractor](https://github.com/angular/protractor) test runner, it simulates interaction.
So first the web server should be brought up:

	npm start

So that Protractor can execute the tests against it. Starting the tests is done with:

	npm run protractor

**Note**: Protractor is built upon WebDriver and this should be installed:

	npm run update-webdriver

This will download and install the latest version of the stand-alone WebDriver tool.

---------------------------------------

##What is Ignite UI?
[![Ignite UI Logo](http://infragistics-blogs.github.io/github-assets/logos/igniteui.png)](http://igniteui.com)

[Ignite UI](http://igniteui.com/) is an advanced HTML5+ toolset that helps you create stunning, modern Web apps. Building on jQuery and jQuery UI, it primarily consists of feature rich, high-performing UI controls/widgets such as all kinds of charts, data visualization maps, (hierarchical, editable) data grids, pivot grids, enhanced editors (combo box, masked editors, HTML editor, date picker, to name a few), flexible data source connectors, and a whole lot more.  Too many to list here - check out [the site](http://igniteui.com/) for more info and to [download](https://igniteui.com/download) a trial.

Ignite UI is not just another library created in someone's free time. It is commercial-ready, extremely well-tested, tuned for top performance, designed for good UX, and backed by [Infragistics](http://www.infragistics.com/), an experience-focused company with a track record of over 24 years of experience in providing enterprise-ready, high-performance user interface tools for web, windows and mobile environments.

[![Infragistics Logo](http://infragistics-blogs.github.io/github-assets/logos/infragistics.png)](http://infragistics.com)
>>>>>>> origin/master
