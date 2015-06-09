# Clock
Analog clock.
// change r value to adjust radius
int r = 100;
int x;
int y;
float hourX = hour() + (minute()/60);
float hour = radians((hourX*30) - 90);
float minuteX = minute() + (second()/60);
float minute = radians((minuteX*6) - 90);
float second = radians((second()*6) - 90);
void setup() {
  size(230, 230);
  // change x and y values to translate clock
  x = width/2;
  y = height/2;
}
void draw() {
  background(255);
  stroke(100);
  // outer part
  if (r > 20) {
    strokeWeight(r/20);
  } else {
    strokeWeight(1);
  }
  noFill();
  ellipse(x, y, (r*2) + 1, (r*2) + 1);
  // hour
  hourX = hour() + (minute()*0.016666666666666);
  hour = radians((hourX*30) - 90);
  line(x, y, cos(hour)*(0.6*r) + x, sin(hour)*(0.6*r) + y);
  // minute
  minuteX = minute() + (second()*0.016666666666666);
  minute = radians((minuteX*6) - 90);
  line(x, y, cos(minute)*(0.9*r) + x, sin(minute)*(0.9*r) + y);
  // second
  if (r > 33) {
    strokeWeight(r/33);
  } else {
    strokeWeight(1);
  }
  second = radians((second()*6) - 90);
  line(x, y, cos(second)*r + x, sin(second)*r + y);
  // ticks
  for (int i = 0; i < 13; i++) {
    line(cos(i*PI/6)*(0.9*r) + x, sin(i*PI/6)*(0.9*r) + y, cos(i*PI/6)*r + x, sin(i*PI/6)*r + y);
  }
}
