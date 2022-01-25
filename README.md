# Web Page for Paint Application

## AIM:

To design a static website for Paint Application using HTML5 canvas.

## DESIGN STEPS:

### Step 1:

Requirement collection.

### Step 2:

Creating the layout using HTML,CSS and canvas.

### Step 3:

Write javascript to capture move events.

### Step 4:

Perform the drawing operation based on the user input.

### Step 5:

Validate the layout in various browsers.

### Step 6:

Validate the HTML code.

### Step 6:

Publish the website in the given URL.

## PROGRAM :

~~~
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Paint Application</title>
    <link rel="icon" href="./img/logo.png" type="image/x-icon" />
    <style>
        #Canvas{
          background-color: #98fcff62;
          box-shadow: inset 0 0 5px #b6b6b6; 
          backdrop-filter: blur(15px);
          border-radius: 2px;
          border: 5px solid #EB7A81;
        }
        #buttons{
          background-color: #d4b8d3;
          border: 2px solid #690247;
          border-radius: 7px;
          color: black;
          padding: 8px 10px;
          text-align: center;
          display: inline-block;
          font-size: 16px;
          margin: 4px 2px;
          cursor: pointer;
        }
        #colors{
            border: 2px solid #ffffff;
            border-radius: 25px;
            padding: 25px 25px;
            text-align: center;
            display: inline-block;
            font-size: 16px;
            margin: 4px 2px;
            cursor: pointer;
        }
        #buttons:hover{
            background-color:#ffffff36;
            transition: 0.5s;
        }
        #colors:hover{
            opacity: 20%;
            transition: 0.21s;
        }
        #bg{
            background-image: url(https://cutewallpaper.org/21/white-gradient-backgr…tyle-rounded-area-with-a-gradient-background-.jpg);
        }
        .footer {
            display:block;
            font-size: 40px;
            font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
            margin: 0px 0px 0px 0px;
            padding-top: 10px;
            color: #000000;
        }
        #content{
            padding-left: 600px; 
            padding-top:10px ;
            padding-bottom: 15px;
        }
        .text{
            text-align: center;
            padding-top: 10px;
            padding-bottom: 10px;
            font-size: 60px;
            color: rgb(0, 0, 0);
            font-family: 'Times New Roman', Times, serif;
        }
        </style>
  </head>
  <body id="bg">
    <div class="text">HTML CANVAS</div>
    <center>
        <button onclick="shape=1" id="buttons" >S-Circle</button>
        <button onclick="shape=2" id="buttons">Circle</button>
        <button onclick="shape=3" id="buttons">S-Square</button>
        <button onclick="shape=4" id="buttons">Square</button>
        <button onclick="shape=5" id="buttons">S-Triangle</button>
        <button onclick="shape=6" id="buttons">Triangle</button>
        <br>
        <button onclick="size()" id="buttons" >Size Changer</button></center>
   
        <div id="content">
      <canvas id="Canvas" width="700" height="700" onclick="showCoords(event)"></canvas></div>
      
      <center>
      <button onclick="change_color(this)" id="colors" style="background: white;"></button>
      <button onclick="change_color(this)" id="colors" style="background: rgb(255, 72, 72);"></button>
      <button onclick="change_color(this)" id="colors" style="background: rgb(255, 115, 1);"></button>
      <button onclick="change_color(this)" id="colors" style="background: rgb(252, 255, 60);"></button>
      <button onclick="change_color(this)" id="colors" style="background: rgb(94, 255, 45);"></button>
      <button onclick="change_color(this)" id="colors" style="background: rgb(7, 184, 1);"></button>
      <button onclick="change_color(this)" id="colors" style="background: rgb(49, 231, 255);"></button>
      <button onclick="change_color(this)" id="colors" style="background: rgb(46, 112, 255);"></button>
      <button onclick="change_color(this)" id="colors" style="background: rgb(213, 76, 255);"></button>
      <button onclick="change_color(this)" id="colors" style="background: rgb(153, 0, 255);"></button>
      <button onclick="change_color(this)" id="colors" style="background: rgb(54, 0, 124);"></button>
      <button onclick="change_color(this)" id="colors" style="background: rgb(0, 0, 0);"></button>
      </center>

      <script>


        const canvas = document.getElementById("Canvas");
        const ctx = canvas.getContext("2d");
        ctx.fillStyle = "#FF0000";
        canvas.height = canvas.width;
        ctx.transform(1, 0, 0, -1, 0, canvas.height);
        let xMax = canvas.height;
        let yMax = canvas.width;
        let csize= 20;
        let sqsize= 50;
        let tsize=50;
        let tata="black";
        function size(){   
          if (shape==1 ||shape==2){
            let c= prompt("Please enter size of circle", "ex:100,50");
            csize=c;
          } 
          if (shape==3 ||shape==4){
            let s = prompt("Please enter size of square", "ex:100,20");
            sqsize=s;
          }
          if (shape==5 || shape==6){
            let t= prompt("Please enter size of triangle","ex:50,84");
            tsize=t;
          }
        }
        function change_color(element){
          tata=element.style.background;
        }
        function showCoords(event)
        {
          var x = event.clientX-545;
          var y = yMax-event.clientY;
          var coords = "X coords: " + x + ", Y coords: " + y;
          document.getElementById("demo").innerHTML = coords;
    
          if (shape==1){
            ctx.beginPath();
            ctx.arc(x, y, csize, 0, 2 * Math.PI);
            ctx.fillStyle=tata;
            ctx.fill();
          }
          if (shape==2){
            ctx.beginPath();
            ctx.arc(x, y, csize, 0, 2 * Math.PI);
            ctx.strokeStyle=tata;
            ctx.stroke();
          }
          if (shape==3){
            ctx.beginPath();
            ctx.rect(x-(sqsize/2),y-(sqsize/2), sqsize,sqsize);
            ctx.fillStyle=tata;
            ctx.fill();
          }
          if (shape==4){
            ctx.beginPath();
            ctx.rect(x-(sqsize/2),y-(sqsize/2), sqsize,sqsize);
            ctx.strokeStyle=tata;
            ctx.stroke();
          }
          if (shape==6){
            ctx.beginPath();
            ctx.moveTo(x, y);
            ctx.lineTo(x-(tsize/2),y-(tsize*0.86602));
            ctx.lineTo(x+(tsize/2),y-(tsize*0.86602));
            ctx.lineTo(x,y)
            ctx.strokeStyle=tata;
            ctx.stroke();
          }
          if (shape==5){
            ctx.beginPath();
            ctx.moveTo(x, y);
            ctx.lineTo(x-(tsize/2),y-(tsize*0.86602));
            ctx.lineTo(x+(tsize/2),y-(tsize*0.86602));
            ctx.fillStyle=tata;
            ctx.fill();
          }    
        }
      </script>
    <center><p id="demo" style="color: white;"></p></center>
       <div class="footer"><center>Developed by Shankar.S.S</center></div>
  </body>
</html>
~~~

## OUTPUT:

### Before Painting:

![output](before.png)

### After Painting:

![output](after.png)


## Result:

Thus a website is designed and validated for paint application using HTML5 canvas.
