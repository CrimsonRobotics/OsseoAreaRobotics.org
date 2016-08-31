# [Osseo Area Robotics](http://www.osseoarearobotics.org)

Maintained by [Crimson Robotics](http://www.crimsonrobotics.com), FIRST Robotics Competition Team 2526. 

# How it works

Data is pulled from a Google Sheets document with each line/row representing a new location/facility/school. The locations contain data stored in the sheet cells, pulled using Google Sheet's Publish to Web and the JSON export URL (not normally shown in Google Sheets, uses this template:

`https://spreadsheets.google.com/feeds/list/` + Spreadsheet ID + `/od6/public/values?alt=json`

Using [AngularJS 2](angular.io)'s [$http](https://docs.angularjs.org/api/ng/service/$http) feature, I pull the data from the sheet and save it to a local file. The list of schools are then printed using AngularJS's ng-repeat. Once a school has been selected, that school is set to the global variable `selectedSchool` , which triggers the next 'page'/section (which only shows ng-if="selected school exists"). The contents of this page is rendered using the data from the selected school.

# Adding data to the school pages

First, add the data as a new column in the Google Sheet. Lowercase slugify this text ("Test" => "test", "This is a test" => thisisatest", etc) and add it the the index.html script section where on object is getting pushed to the database:

```
$scope.allSchools.push({
              name: entry.gsx$schoolname.$t,
              flljr: entry.gsx$flljr.$t == 'TRUE',
              fll: entry.gsx$fll.$t == 'TRUE',
              frc: entry.gsx$frc.$t == 'TRUE',
              ftc: entry.gsx$ftc.$t == 'TRUE',
              vex: entry.gsx$vex.$t == 'TRUE',
              currentMessage: entry.gsx$currentmessage.$t,
              contactEmail: entry.gsx$contactemail.$t,
              hasWebsite: entry.gsx$websitetitle.$t.length > 0 && entry.gsx$websiteurl.$t.length > 0,
              websiteTitle: entry.gsx$websitetitle.$t,
              websiteURL: entry.gsx$websiteurl.$t
            });
```

Add your new data point has a key in the object, make the value equal to: `entry.gsx$sluggedtext.$t`, replacing `sluggedtext` with the slugged text from above.

## Template's Copyright and License - 
Template used is: [Start Bootstrap](http://startbootstrap.com/) - [Stylish Portfolio](http://startbootstrap.com/template-overviews/stylish-portfolio/)

Template released under the [MIT](https://github.com/BlackrockDigital/startbootstrap-stylish-portfolio/blob/gh-pages/LICENSE) license.
