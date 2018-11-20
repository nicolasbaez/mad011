# mad011
basic line weight loop

![mad011](https://github.com/nicolasbaez/mad011/blob/master/mad011.gif)

```processing
float dRot=1;
float dGlobal=2;
float tempRR=128;
float tempGG=128;
float tempBB=128;
float j=0;
void setup() {
  size(512, 256);
  background(255);
}
void draw() {
  background(255);
  translate(width/2, height/2);
  rotate(radians(dRot));
  pushMatrix();
  for (int i=-width; i<=width; i+=2) {
    stroke(tempRR, tempGG, tempBB);
    line(i, -height, i, height);
    tempRR=tempRR+random(-dGlobal, dGlobal);
    tempGG=tempGG+random(-dGlobal, dGlobal);
    tempBB=tempBB+random(-dGlobal, dGlobal);
  }
  popMatrix();
  noStroke();
  fill(255);
  ellipse(0, 0, map(cos(radians(j)), 1, -1, height*0.5, height*0.6), map(cos(radians(j)), 1, -1, height*0.5, height*0.6));
  noFill();
  stroke(255);
  for (float i=map(cos(radians(j)), 1, -1, height*0.55, height*0.7); i<=width*sqrt(2); i++) {
    ellipse(0, 0, i, i);
  }
  dRot++;
  j++;
  if (j>=360&&j<=360*2) {
    saveFrame("gif/mad011-######.png");
  }
}
```
