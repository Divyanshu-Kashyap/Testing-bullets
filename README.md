//To create the global variables or the game objects
var bullet,thickness;
var wall,speed,weight;

function setup() {
  //To create the canvas or the play area
  createCanvas(1600,400);


  thickness=random(22,83);

  //The random speed of the bullet
  speed=random(223,321);
    

  weight=random(30,52);

  //to create the bullet
  bullet=createSprite(50,200,50, 5);
  bullet.shapeColor="white";
  bullet.velocityX=speed;
    
  //To create the wall
  wall=createSprite(1300,200,thickness,height/2);
}

function draw() {
  //The clear the play area or background color
  background(0);  
  
  //The wall color will change according to the damage of the bullet
  if (hasCollided(bullet,wall)){
      bullet.velocityX=0
      
      var damage=0.5*weight*speed*speed/(thickness*thickness*thickness);
     
    if(damage>10){
      wall.shapeColor="green";
    }
     
    else if(damage<10) {
      wall.shapeColor="red";
    }
      
  }

  if(bullet.x<wall.x){
    wall.shapeColor="green";
  }

 if(bullet.x>wall.x){
   wall.shapeColor="red";
 }

//To display the game objects
drawSprites();
}

//To declare the right edge of the bullet so that the color will change according to it
function hasCollided(bullet,wall){
  
    bulletRightEdge=bullet.x+bullet.width;
    wallLeftEdge=wall.x;

  if(bulletRightEdge>=wallLeftEdge){
     return true;
  }
     else {
     return false;
  }
}
