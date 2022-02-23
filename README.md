 var backgroundImage,ground; 
 var balloonRed,balloonImageRed;
 var ballonGreen, ballonImageGreen;
 var ballonBlue, ballonImageBlue;
 var ballonPink, ballonImagePink;
 var bowImage,bow;
var arrow,arrowImage;
var red_balloon,blue_balloon,pink_balloon,green_balloon,arrowGroup;
var balloon_selection;
var score;

function preload(){
  bowImage= loadImage("bow0.png");
   backgroundImage = loadImage("background0.png");
  balloonImageRed = loadImage("red_balloon0.png");        balloonImageGreen = loadImage("green_balloon0.png");
  balloonImageBlue = loadImage("blue_balloon0.png");
  balloonImagePink = loadImage("pink_balloon0.png");
  arrowImage = loadImage("arrow0.png")
  }
 function setup(){
   //creating the canvas
   createCanvas(400,400);
   
   red_balloon = createGroup();
   green_balloon = createGroup();
   blue_balloon = createGroup();
   pink_balloon = createGroup();
   arrowGroup = createGroup();
   
   ground = createSprite(0,0,400,400);
   ground.addImage("ground",backgroundImage);
  // ground.x = ground.width/2;
   ground.scale = 2.3;
   
   bow = createSprite(380,200,50,50);
   bow.addImage("bow",bowImage);
   score = 0;
}
 function draw(){
   //background(backgroundImage);
   ground.velocityX = -4;
   if(ground.x < 0){
   ground.x = ground.width/2;
   }
  bow.y = mouseY;
   if (keyWentDown("space")){
     createarrow()
     arrow.y = bow.y;
   }
   var balloon_selection = Math.round(random(1,4));
   //console.log(balloon_selection);
   //console.warn(frameCount);
   if (World.frameCount% 80 === 0){
   if(balloon_selection === 1){
     redBalloon()
   }else if (balloon_selection === 2){
     greenBalloon();
   }else if (balloon_selection == 3){
     blueBalloon();
   } else {
     pinkBalloon();
    }
   }
   if (arrowGroup.isTouching(pink_balloon)){
     pink_balloon.destroyEach();
     arrowGroup.destroyEach();
     score = score +1;
   }
   if (arrowGroup.isTouching(blue_balloon)){
     blue_balloon.destroyEach();
     arrowGroup.destroyEach();
     score = score +1;
   }
   if (arrowGroup.isTouching(green_balloon)){
     green_balloon.destroyEach();
     arrowGroup.destroyEach();
     score = score +1;
   }  
   if (arrowGroup.isTouching(red_balloon)){
     red_balloon.destroyEach();
     arrowGroup.destroyEach();
     score = score +1;
   }   
   drawSprites();
   textSize(32);
   fill("black");
   text("score: " + score, 250,30);
  }
function createarrow(){
  arrow = createSprite(400,200,10,20);
  arrow.scale = 0.3;
  arrow.velocityX = -4;
  arrow.addImage("arrow",arrowImage);
  arrowGroup.add(arrow);
  
}
function redBalloon(){
  balloonRed = createSprite(0,Math.round(random(10,390)),1,1);
  balloonRed.addImage("balloonRed",balloonImageRed);
  balloonRed.scale = 0.1;
  balloonRed.velocityX = 3;
  balloonRed.lifetime = 100;
  red_balloon.add(balloonRed);
}
function greenBalloon(){
  balloonGreen = createSprite(0,Math.round(random(10,390)),1,1);
  balloonGreen.addImage("balloonGreen",balloonImageGreen);
  balloonGreen.scale = 0.1;
  balloonGreen.velocityX = 3;
  balloonGreen.lifetime = 100;
  green_balloon.add(balloonGreen)
}
function blueBalloon(){
  balloonBlue = createSprite(0,Math.round(random(10,390)),1,1);
  balloonBlue.addImage("balloonBlue",balloonImageBlue);
  balloonBlue.scale = 0.1;
  balloonBlue.velocityX = 3;
  balloonBlue.lifetime = 100;
  blue_balloon.add(balloonBlue)
} 
function pinkBalloon(){
  balloonpink = createSprite(0,Math.round(random(10,390)),1,1);
  balloonpink.addImage("ballonPink",balloonImagePink);
  balloonpink.scale = 1.09;
  balloonpink.velocityX = 3;
  balloonpink.lifetime = 100;
  pink_balloon.add(balloonpink);
}
