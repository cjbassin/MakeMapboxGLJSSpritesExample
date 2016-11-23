# Creating your own sprites for use in Mapbox GL JS
# This an example which is built off of the Mapbox GL JS example found [here](https://www.mapbox.com/mapbox-gl-js/example/animate-point-along-route/)

Sprites cannot be added to code simply by pointing to a svg file.  Mapbox requires a specific json and png of sprites.  There is a tool that makes it quite simple to create this.

1. Create your svg icon 
2. Use spritezero to generate the json and png file
3. Create your own copy of mapbox styles 
4. add the file path to your sprites
5. Check out your map


###Create or aquire your svg icon
- There are tons of free, opensource svg icons out there.  Make sure you check the license for any that you are iterested in usuing.
- Or create your own.  There are many online editors to do so.

### Spritezero cli
- [https://github.com/mapbox/spritezero-cli](spritezero cli github page)
- Follow the instructions to get spritezero on your computer.  This will allow you to very simply generate the files you need.
- I did not have experience with node and npm prior to this.  When I first tried to install I got a few errors.
- There was a problem with my npm installation preferences,
 - I wound up having to install as :
```
$npm config get prefix
/usr/local


$ sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}

$ npm install -g spritezero-cli

```
- Creating the icons
- Create a folder in your current directory that has the svg icon you have created ( 'spritetry' )
- Run spritezero with that folder as an input and a name for the output files ('outsprite')
- I also added --retina to get the retina version
```
$ spritezero outsprite spritetry/ --retina
```
### Style Sheets
Mapbox uses style sheets for the look and feel of their base maps.  You can create your very own with lots of personalization.  If you just want to add your own sprites then you really only to make one simple change.
Go to mapbox gljs github to get a version of the style sheet for the base map you are interested in and download into your working directory.  These are simple json files.  
Where it says:
```
"sprite": "sprite"
```
change to the name of your new sprite you used in spritezero above
```

"sprite": "outsprite",
```
See the example herein 'stylesheet1.json'

### HTML
#### Add your style sheet
The stylesheet is referenced when you create the map initially in the Mapbox GL JS code;
```
var map = new mapboxgl.Map({
    container: 'map',
    style: 'stylesheet1.json',
    center: [-122.414, 37.776],
    zoom: 6,
    pitch:09
});
```

###Call the icon
At the point where you are creating a layer for the map you can call the icon simply by usuing the name of the icon within the style sheet.  This is the name of the original svg file.  The sprite sheet you created maye have multiple sprites in them.  So you could create an entire set of personallized icons in one stylesheet
```
map.addLayer({
        "id": "point",
        "source": "point",
        "type": "symbol",
        "layout": {
            "icon-image": "Visible_Blue_Unicorn_Dexter",
            "icon-rotate": 0
        }
    });
```
### Check it out
- fire up a local server
- python -m http.server for python3
- python -m SimpleHTTPServer for python2 
 - and test out your html




