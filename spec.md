# t-activity-search Specification

### Component Use

``` html

<t-activity-search 
		options={{searchOption}} 
		resources={{resources}} 
		init-model={{searchModel}} 
		on-do-search="{{doSearch}}"
		lang="en">
</t-activity-search>

```


### Search Option to Component

```javascript

	var searchOption = {
		date : {
			// from-date allowed from current date. Value 0 means same day seach allowed.
			fromDateAllowFromNow : 0,
            
			//default to-date if from-date is selected
			defaultDuration : 7,
			format : "mm/dd/yyyy"
		}

	}
```

### Globalization Resource Input

```javascript
	var resources = {
		watermark : {
			fromDate : "MM/DD/YYYY",
			toDate : "MM/DD/YYYY",
			destination : "City, Airport, Address or Point of Interest"
		},
		errorMessage : {
		    destinationError : "Please enter your destination",
			fromDateError : "Please enter from date",
			toDateError : "Please enter to date"
		}
	}
```

### Search Model 

```javascript
	var searchModel = {
	  "location": {
	    "name": "Las Vegas, NV, USA",
	    "geoCode": "36.1147074,-115.1728497",
	    "type": "address",
	    "code": "",
	    "cityName": "Clark County",
	    "countryCode": "US",
	    "stateCode": "NV",
	    "formattedAddress": "Las Vegas, NV, USA"
	  },
	  "fromDate": {
	    "date": "06/02/2017"
	  },
	  "toDate": {
	    "date": "013/02/2017"
	  },
	  "type": "Activity"
	}
```

## Important Information

- Auto-suggest - When user start typing auto-suggest should suggest results only after entering minimum 3 char.
- Auto-suggest - Once user stop entering the data, auto-suggest should fire after a gap of 50 ms (Milli seconds).
- Auto-suggest - Text box (Destination) will show loader while processing and after selection of item, it should started showing close icon to clear the data.
- Auto-suggest - Should allow user to select an items says "Las Vegas, NV, United States - McCarran International Airport (LAS)" but after selection in text box it will appear as "LAS - Las Vegas" (Short version)
- Auto-suggest - Spec should categorised with CITY / AIRPORT and POINTS OF INTEREST. 
- Auto-suggest - On selection of search button pass on the location object of user selection.
- Component Events - doSearch (Triggers	event with search data) and initializeSearch (Listens to this event to set defautl state as per data passed)
- Misc items to be handled from CSS like:
1. Background color of outer container.
2. Mixin (to control outer width)
3. Button color etc.


## Test Cases

- Basic validation - Don't enter or select anything and click Search
- Destination - If user don't select from autosuggest and click search with proper dates
- Auto-suggest - When user starts typing auto-suggest should start giving results after min. 3 char
- Auto-suggest - Should fire when user stop typing - Delay should be min 50ms
- Auto-suggest - Destination text box to show loader/spinner while processing and close icon after selection to clear
- Date - fromDate/toDate - Calender should be available
- Date - User should allow to type in fromDate/toDate dates
- Button name should change on click of Search to "Searching" or whatever the name set in property

## Steps to Start
- Set Github repository at your end for this project, we will merge them later
- You can use Google/Vaadin's elements (like calender element and textboxes etc.)
- You can use some Tavisca's elements like auto-suggest if required from https://github.com/atomelements/t-autosuggest but all the features and properties mentioned in scope should be added. (Fork the existing element and create V2)
- APIs Integration - Use Tavisca's APIs for integration purpose.

## Performance standard
- Any component if opened via [web page tester](https://www.webpagetest.org/), it should load under 500ms (milli seconds).

## Documents
- Visual designs for search components - https://projects.invisionapp.com/share/6E9PJ7R4Q#/screens/212067485
- API access : Url - http://demo.travelnxt.com/dev
- Tavisca Elements - https://github.com/atomelements and https://github.com/travelnxtelements
- Vaadin elements - https://vaadin.com/docs/-/part/elements/elements-getting-started.html
- Google - https://elements.polymer-project.org/browse?package=google-web-components
- Tavisca Web component style Guide - https://drive.google.com/open?id=0B7BT_2nBFNYVR2tscE9pRnVJYmc
- Tavisca Web component style Guide - https://drive.google.com/open?id=0B7BT_2nBFNYVR2tscE9pRnVJYmc