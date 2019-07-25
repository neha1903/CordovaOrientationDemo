# CordovaOrientationDemo
With the Help of Cordova Plugin Screen Orientation the Demo App





Add This  cordova-plugin-screen-orientation to your Cordova Project
    
    
<!DOCTYPE html>
<html>
    <head>
        <meta name="format-detection" content="telephone=no" />
<!--        <meta name="viewport" content="user-scalable=no, initial-scale=1,  maximum-scale=1, minimum-scale=1, width=device-width, height=device-height" />   can be used on resize event      -->
        <meta name="viewport" content="user-scalable=no, initial-scale=1, maximum-scale=1, minimum-scale=1, width=device-width">
        <link rel="stylesheet" type="text/css" href="css/index.css">
        
        <title>Hello World</title>
        
         <style>
            /* portrait */
            @media screen and (orientation: portrait) {
              /* portrait-specific styles */
              body {
                background-color: white;
              }
            }
            /* landscape */
            @media screen and (orientation: landscape) {
              /* landscape-specific styles */
              body {
                background-color: orange;
              }
            }
        </style>
        <script src="cordova.js"></script>
        <script>
            
            function onBodyLoad() {
//                alert("Body Load");
                document.addEventListener("deviceready", onDeviceReady, false);
                 //set the orientationchange event listener
                window.addEventListener('orientationchange', onOrientationChange);
                 //for devices that don't fire orientationchange we can use on resize event i.e window.addEventListener("resize", onResize, false);

                 //Fire this at the start to set the initial orientation on the page
                updatePage();
            }
            
            function onDeviceReady() {
                console.log("Cordova is Ready");
//                alert(screen.orientation.type );
                update();
            }
            
            function update(){                
                var a = (screen.orientation.type);
                    
                if(a == 'landscape-primary' || a == 'landscape-secondary'){
                     document.getElementById("s").innerHTML = "GOOD BYE";
                     document.getElementById("n").innerHTML = "Turn Portrait to Say Hello";
                         
                }else{
                     document.getElementById("s").innerHTML = "Hello";
                     document.getElementById("n").innerHTML = "Turn Landscape to Say Good Bye";
                }
            }
            
            function updatePage() {
                screen.orientation.addEventListener('change', function(){
                    update();                    
                });                
            }
            
            function onOrientationChange() {
                 console.log("Orientation has changed");
                 switch (window.orientation) {
                 case 90:
                   console.log("Device is in Landscape mode");
                   break;
                 default:
                   console.log("Device is in Portrait mode");
                   break;
                 }
                 updatePage();
            }
            
            
        </script>
        
    </head>     

                
        
   <body onload="onBodyLoad()">
        <h1 id="s"></h1>
          <p id ="n"></p>
    </body>
    
</html>

