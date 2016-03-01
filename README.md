# jQuery Mapify #

A jQuery plugin for quickly adding maps via the Google Maps API. To add a map to an element, use the `mapify()` method:

    $('.foo').mapify({
        points: [
            {
                lat: 53.3171819,
                lng: -3.4955914
            }
        ]
    });

By default, the plugin will automatically load the required JavaScript API and will centre and zoom the map to show all the points. The default map type is `google.maps.mapTypeId.ROADMAP`. You can add as many points to the map as you like.

## Options ##

`points` is an array of coordinates to display on the map. You can add multiple points and each point can have a marker, title, and information window:

    $('.foo').mapify({
        points: [
            {
                lat: 53.3171819,
                lng: -3.4955914,
                marker: true,
                title: 'Marker title',
                infoWindow: 'Info window content'
            },
            {
                lat: 53.9586419,
                lng: -1.1156968,
                marker: '/custom/marker/image.png'
            }
        ]
    });

`type` sets the map type. You can use the constants supplied by Google, or a case-insensitive string that matches those types. The default type is `roadmap`:

    $('.foo').mapify({
        ...
        type: 'hybrid'
    });

`center` sets the centre of the map to a custom location. This is optional. By default, the map will use `fitBounds()` to find the center of the map based on the points:

    $('.foo').mapify({
        ...
        center: {
            lat: 53.3171819,
            lng: -3.4955914
        }
    });

`zoom` sets the zoom level of the map. By default, the map will use `fitBounds()` so that all points will be visible on the map:

    $('.foo').mapify({
        ...
        zoom: 12
    });

`responsive` forces the map to reset its centre and zoom level when the browser window is resized. By default, this is set to `false`.

    $('.foo').mapify({
        ...
        responsive: true
    });

`callback` lets you do something else with the map and its data. It is a function that takes the map, the bounds, and the settings as its arguments:

    $('.foo').mapify({
        ...
        callback: function(map, bounds, settings) {
            console.log(map);
        }
    });