# Creating your own sprites for usin my Mapbox GL JS

Sprites cannot be added to code simply by pointing to a svg file.  Mapbox requires a specific json and png of sprites.  There is a tool that makes it quite simple to create this.

1. Create your svg icon 
2. Use spritezero to generate the json and png file
3. Create your own copy of mapbox styles 
4. add the file path to your sprites
5. eh voila


1. Create or aquire your svg icon
- There are tons of free, opensource svg icons out there.  Make sure you check the license for any that you are iterested in usuing.
- Or create your own  There are many online editors to do so.

2. Spritezero cli
-[https://github.com/mapbox/spritezero-cli](spritezero cli github page)
-Follow the instructions to get spritezero on your computer.  This will allow you to very simply generate the files you need.
-I did not have experience with nope and npm prior to this.  When I first tried to install I got a few erros.
-There was a problem with my npm installation preferences,
I wound up haveing to install as :
'''
$npm config get prefix
/usr/local


$ sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}

$ npm install -g spritezero-cli

'''
