# Hologram

import processing.video.*;
PImage hologram;
float x;
float y;
float a;
float b;

Capture video;

void setup(){
  fullScreen();
//size(1280,750);
video=new Capture(this, 640,400,100);
video.start();
hologram =loadImage("hologram_bg.jpg");
x=250;
y=250;
a=x/2;
b=y/2;
}

void draw(){
  video.read();
  background(0);
  //image(hologram,0,8,1280,720);
  rectMode(CENTER);
  //rect(width/2, height/2,200,200);
  //rect(width/2, height/2, height,height);
  //noFill();
  //stroke(250,250,250);
  

image(video, width/2-a, height/2-a-x-20,x,y);//top
pushMatrix();
translate(width/2,height/2);
scale(1,-1);
image(video, -125,-x-100-45,x,y);//  botton  left video, width/2-a-x-20, height/2-a,x,y
popMatrix();

pushMatrix();
translate(width/2, height/2);
scale(1,-1);
rotate(PI/2);
image(video, -125,-x-100-48,x,y);//right

popMatrix();


pushMatrix();
translate(width/2-150-250, height/2+125);
rotate(-PI/2);
image(video, 0,0,x,y);//left
popMatrix();




}
