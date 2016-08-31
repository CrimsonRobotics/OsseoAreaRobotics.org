# [Osseo Area Robotics](http://www.osseoarearobotics.org)

Maintained by [Crimson Robotics](http://www.crimsonrobotics.com), FIRST Robotics Competition Team 2526. 

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
