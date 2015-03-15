
```
#!/bin/sh
# Utility script to create express project and make it ready with coffee scripts
# Assumes the availability of (express, js2coffee) node modules on path.

PROJECTDIR="$1"

if [ "$PROJECTDIR" = "" ]; then
        echo "Usage: $0 projectname";
fi

express $PROJECTDIR

echo "   converting js to coffee and installing dependencies"

cd $PROJECTDIR
js2coffee app.js > app.coffee; rm app.js
js2coffee routes/index.js > routes/index.coffee; rm routes/index.js
npm install

echo "   \n$PROJECTDIR is ready now."
echo "   \$ cd $PROJECTDIR"
echo "   \$ coffee app.coffee"
```