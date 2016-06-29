#DOC

##Creating a new game
```javascript
var game = new Game(
    38 * 32, //canvas width
    20 * 32, //canvas height
    "#game_container",//canvas parent
    {
    update: update,
    render: render
    }
);

var access = game.access();
//access allows you to access native canvas functions
//exemple: access.fillRect();
```
##Ressources managing

###Preload ressources (image and json are supported)

```javascript
var assets = new Loader(
    [
        {
            file: 'images/tileset.png',
            key: 'tileset',
            type: 'image'
        },
        {
            file: 'images/characters.png',
            key: 'characters',
            type: 'image'
        },
        {
            file: 'json/jacky.json',
            key: 'jacky',
            type: 'json'
        }
    ],
    function () {
        alert("all assets are ready to use!"); //callback
    }
);

assets.load(); //start the downloading of ressources
```
###Knowing the state of the downlading

this line return the state of all downloads in percent (from 0 to 100)

```javascript
assets.getDownloadState();
//this line return the state of all downloads in percent (from 0 to 100)
```
##Creating game loop (with delta time)

```javascript
function update() {
  access.clearRect(0, 0, game.w, game.h);
        rect.x -= deltaSpeed(rect.xv, game.delta); //calculating delta speed
}
function render() {
 access.fillRect(rect.x, rect.y, rect.w, rect.h);
}
```

##Keyboard and event managment
```javascript
 /*
 AVAILABLE EVENTS:
    Z
    S
    Q
    D
    W
    A
    SPACE
    ENTER
    ARROWTOP
    ARROWBOTTOM
    ARROWLEFT
    ARROWRIGHT
    */
    
//If you want to listen arrowleft and arrowright events
var keyboard = new KeyboardHandler();
keyboard.listen([keyboard.ARROWLEFT, keyboard.ARROWRIGHT]);

//Detect key pressed in 'game update'
function update() {
    
    if (keyboard.isDown(keyboard.ARROWLEFT)) {
        //arrow left is pressed !
    } else if (keyboard.isDown(keyboard.ARROWRIGHT)) {
         //arrow right is pressed !
    }
    
}
```
