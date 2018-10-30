# google-shade

I would like to create a software that enables users to shade areas on a globe, find where they want to keep track of easily, and zoom in and out to facilitate this. In other words, I want to enable users to easily and in a way that can be added to their Google account, add polygons to Google Maps. 

Code examples I will be exploring: 

function initialize() {
  var myLatLng = new google.maps.LatLng(24.886436490787712, -70.2685546875);
  var myOptions = {
    zoom: 5,
    center: myLatLng,
    mapTypeId: google.maps.MapTypeId.TERRAIN
  };

  var bermudaTriangle;

  var map = new google.maps.Map(document.getElementById("map_canvas"),
      myOptions);

  var triangleCoords = [
      new google.maps.LatLng(25.774252, -80.190262),
      new google.maps.LatLng(18.466465, -66.118292),
      new google.maps.LatLng(32.321384, -64.75737),
      new google.maps.LatLng(25.774252, -80.190262)
  ];

  // Construct the polygon
  bermudaTriangle = new google.maps.Polygon({
    paths: triangleCoords,
    strokeColor: "#FF0000",
    strokeOpacity: 0.8,
    strokeWeight: 2,
    fillColor: "#FF0000",
    fillOpacity: 0.35
  });

  bermudaTriangle.setMap(map);

  // add an event listener
  google.maps.event.addListener(bermudaTriangle, 'click', function() {
      this.setMap(null);
  });

}
