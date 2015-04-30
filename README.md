# Producing Google Map with location markers in JavaScript
This research module highlights my progress in learning JavaScript to produce a interactive music map via Google Maps

#Description/Background 
I have created a python script that scrapes meta data from the EchoNest 'Million Song Subset' directory of music files. The script extracts the artist, song name, artist latitude, and artist longitude from each song and places the data into a 4 item vector that is placed into a list-of-lists structure in Python. I am going to use the location data for each of the songs in the subset to produce a pinpoint marker on a google map that is clickable and will give track info, etc. I knew nothing about JavaScript prior to starting this project, and had to learn the basics in order to produce the Google Map and include features on it. This served as a decent sized obstacle, as it took me a bit to become acclamated with using JavaScript and working from a server to run the html code and show the map on the web. HTML was also something completely new to me, it took some practice to get used to the syntax of the language. Learning some Javascript, HTML, and how to implement a Google Map using Javascript was the research problem that I assumed and worked towards solving.

#Learning Javascript
To learn some of the basics of JavaScript I watched a few videos on YouTube that provided brief tutorials. I learned the syntax of the langauge, how to place script headers, body headers, etc. Once I had a decent grasp on the basics I found examples of Google Maps produced in JavaScript from the web, and referred to those while implementing my map. I found examples that showed how to set listeners, center the map around a certain coordinate, add location markers, and used those examples to help produce my map.

#What I have not done that I plan on including in the Map
I want to include a search bar in the top left corner of the map display that will allow for user's to search the map for artists/songs of their choice. I am also thinking about a way to include some sort of directory that lists all of the artist/song combinations that are plotted on the map. I have also researched a way to embed a youtube search "behind the scenes" so that when a location marker is clicked YouTube will play the song without the video popping up.

#Javascript Code to Produce Google Map
```
<!DOCTYPE html>
<html> 
<head> 
  <meta http-equiv="content-type" content="text/html; charset=UTF-8" /> 
  <title>World Music Map</title> 
  <script src="http://maps.google.com/maps/api/js?sensor=false" 
          type="text/javascript"></script>
</head> 
<body>
  <div id="map" style="width: 1500px; height: 760px;"></div>

  <script type="text/javascript">
    var locations = [
      ['Bondi Beach', -33.890542, 151.274856, 4],
      ['Coogee Beach', -33.923036, 151.259052, 5],
      ['Cronulla Beach', -34.028249, 151.157507, 3],
      ['Manly Beach', -33.80010128657071, 151.28747820854187, 2],
      ['Maroubra Beach', -33.950198, 151.259302, 1]
    ];

    var map = new google.maps.Map(document.getElementById('map'), {
      zoom: 4,
      center: new google.maps.LatLng(34.815697, -41.200498),
      mapTypeId: google.maps.MapTypeId.ROADMAP
    });

    var infowindow = new google.maps.InfoWindow();

    var marker, i;

    for (i = 0; i < locations.length; i++) {  
      marker = new google.maps.Marker({
        position: new google.maps.LatLng(locations[i][1], locations[i][2]),
        map: map
      });

      google.maps.event.addListener(marker, 'click', (function(marker, i) {
        return function() {
          infowindow.setContent(locations[i][0]);
          infowindow.open(map, marker);
        }
      })(marker, i));
    }
  </script>
</body>
</html>
```
#Link to Map
http://student.cs.appstate.edu/formanbs/music/test.html
