# newjsgame
let paddle_x, paddle_y, paddle_width, paddle_height, paddle_dx;
let ball_x, ball_y, ball_diameter, ball_dx, ball_dy;
let brick_x, brick_y, brick_width, brick_height;
function setup() {
  createCanvas(400, 400);
  background("black");
  paddle_width = 100;
  paddle_x = (width / 2) - (paddle_width / 2);
  paddle_y = height - 25;
  paddle_height = 15;
 
   ball_diameter = 20;
  ball_dx =1;
  ball_dy = 4;
  paddle_dx = 3;
  ball_x = (width / 2) - (ball_diameter / 2);
  ball_y = (height / 2) - (ball_diameter / 2);
  
  brick_width = 80;
  brick_x = 0;
  brick_y = 0;
  brick_height = 20;
  
 
}
 
function draw () {
  background("black");
  if((ball_x<brick_x+brick_width) && 
    (ball_x>brick_x) && 
    (ball_y<brick_height)){
   ball_dy=-ball_dy;
    brick_width=0;
    brick_height=0;
 }
 
  if(ball_x + (ball_diameter / 2) > width) {
    ball_dx = -ball_dx;
  }
 
  if(ball_x - (ball_diameter / 2) < 0) {
    ball_dx = -ball_dx;
  }
 
  if(ball_y + (ball_diameter / 2) > height) {
    ball_dy = -ball_dy;
    
  }
   if(ball_y - (ball_diameter / 2) < 0) {
    ball_dy = -ball_dy;
  }
 
  ball_x = ball_x + ball_dx;
  ball_y = ball_y + ball_dy;
 
  if (keyIsDown(LEFT_ARROW)) {
    paddle_x = paddle_x - paddle_dx;
  }
    if (keyIsDown(RIGHT_ARROW)) {
    paddle_x = paddle_x + paddle_dx;
  }
 if((ball_x<paddle_x+paddle_width) && 
    (ball_x>paddle_x) && 
    (ball_y>paddle_y-(paddle_height / 2))){
   ball_dy=-ball_dy;
 }
 
 
  circle(ball_x, ball_y, ball_diameter);
  rect(paddle_x, paddle_y, paddle_width, paddle_height);
  rect(brick_x,brick_y,brick_width,brick_height);
}
