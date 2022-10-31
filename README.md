# bottle
可调参数的瓶子
import controlP5.*;
import peasy.*;
import nervoussystem.obj.*;
  
PeasyCam cam;
ControlP5 bar;

float Radius1;
float Radius2;
float Radius3;
float Radius4;
float Radius5;
float Radius6;
float Radius7;
float Radius8;
float Radius9;
float Radius10;
float tall;
int sides;
float R;
float G;
float B;
boolean displayMesh = false;
boolean record;


void setup() {
  size(2000, 1000, P3D);
  background(0);
  cam = new PeasyCam(this, 2000);
  UI();
}


void draw() {
  background(0);
  lights();
  fill(255);
  
    if (displayMesh) {
    stroke(0);
  }

  fill(R,G,B); 

  lightSettings(); 

  if (record) {
    beginRecord("nervoussystem.obj.OBJExport", "designWork/curvatureVase-####.obj");
  }

  drawCylinder();

  if (record) {
    endRecord();
    record = false;
  }

  UIShow();
  }
  
  
void drawCylinder() {
  float angle = 0;
  float angleIncrement = TWO_PI / sides;
  beginShape(QUAD_STRIP);
  for (int i = 0; i < sides + 1; i++) {
    vertex(Radius1 * cos(angle), 0, Radius1* sin(angle));
    vertex(Radius2 * cos(angle), tall, Radius2 * sin(angle));
    angle += angleIncrement;
  }
  endShape();
  
    beginShape(QUAD_STRIP);
  for (int i = 0; i < sides + 1; i++) {
    vertex(Radius2 * cos(angle), tall, Radius2* sin(angle));
    vertex(Radius3 * cos(angle), tall*2, Radius3 * sin(angle));
    angle += angleIncrement;
  }
  endShape();
  
    beginShape(QUAD_STRIP);
  for (int i = 0; i < sides + 1; i++) {
    vertex(Radius3 * cos(angle), tall*2, Radius3* sin(angle));
    vertex(Radius4 * cos(angle), tall*3, Radius4* sin(angle));
    angle += angleIncrement;
  }
  endShape();
  
    beginShape(QUAD_STRIP);
  for (int i = 0; i < sides + 1; i++) {
    vertex(Radius4 * cos(angle), tall*3, Radius4* sin(angle));
    vertex(Radius5 * cos(angle), tall*4, Radius5 * sin(angle));
    angle += angleIncrement;
  }
  endShape();
  
    beginShape(QUAD_STRIP);
  for (int i = 0; i < sides + 1; i++) {
    vertex(Radius5 * cos(angle), tall*4, Radius5* sin(angle));
    vertex(Radius6 * cos(angle), tall*5, Radius6 * sin(angle));
    angle += angleIncrement;
  }
  endShape();
  
    beginShape(QUAD_STRIP);
  for (int i = 0; i < sides + 1; i++) {
    vertex(Radius6 * cos(angle), tall*5, Radius6* sin(angle));
    vertex(Radius7* cos(angle), tall*6, Radius7 * sin(angle));
    angle += angleIncrement;
  }
  endShape();
  
    beginShape(QUAD_STRIP);
  for (int i = 0; i < sides + 1; i++) {
    vertex(Radius7 * cos(angle), tall*6, Radius7* sin(angle));
    vertex(Radius8 * cos(angle), tall*7, Radius8* sin(angle));
    angle += angleIncrement;
  }
  endShape();
  
    beginShape(QUAD_STRIP);
  for (int i = 0; i < sides + 1; i++) {
    vertex(Radius8 * cos(angle), tall*7, Radius8* sin(angle));
    vertex(Radius9* cos(angle), tall*8, Radius9 * sin(angle));
    angle += angleIncrement;
  }
  endShape();
   beginShape(QUAD_STRIP);
  for (int i = 0; i < sides + 1; i++) {
    vertex(Radius9 * cos(angle), tall*8, Radius9* sin(angle));
    vertex(Radius10* cos(angle), tall*9, Radius10 * sin(angle));
    angle += angleIncrement;
  }
  endShape();
  
  if (Radius10 != 0) {
    angle = 0;
    beginShape(TRIANGLE_FAN);
    vertex(0, tall*9, 0);
    for (int i = 0; i < sides + 1; i++) {
      vertex(Radius10* cos(angle), tall*9, Radius10 * sin(angle));
      angle += angleIncrement;
    }
    endShape();
  }
}
void keyPressed() {
  if (key == 's') {
    record = true;
  }
}
