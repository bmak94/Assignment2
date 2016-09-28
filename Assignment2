import controlP5.*;
ControlP5 cp5;
ControlTimer c;
Textlabel t;
Textarea myTextarea;
int size; 
String textValue = "";
int mx, my;
float[] x=new float[100];
float[] y=new float[100];
float[] easing=new float[100];

void setup() {
  size(1920, 1080); 
  noStroke();


  cp5 = new ControlP5(this);
  ButtonBar b = cp5.addButtonBar("bar")
    .setPosition(0, 1050)
      .setSize(400, 20)
        .addItems(split("a b c d e f g h i j", " "))
          ;
  println(b.getItem("a"));
  b.changeItem("a", "text", "first");
  b.changeItem("b", "text", "second");
  b.changeItem("c", "text", "third");
  b.onMove(new CallbackListener() {
    public void controlEvent(CallbackEvent ev) {
      ButtonBar bar = (ButtonBar)ev.getController();
      println("hello ", bar.hover());
    }
  }
  );
  c = new ControlTimer();
  t = new Textlabel(cp5, "--", 100, 100);
  c.setSpeedOfTime(1);

  myTextarea= cp5.addTextarea("txt")
    .setPosition(40, 690)
      .setSize(200, 200)
        .setFont(createFont("aria", 15))
          .setLineHeight(14)
            .setColor(color(128))
              .setColorBackground(color(255, 100))
                .setColorForeground(color(255, 100));
  ;
  myTextarea.setText("Instruction :"
    +"Press Arrow Keys to move the Balls"
    );
  cp5.addTextfield("name")
    .setPosition(40, 300)
      .setSize(200, 40)
        .setFont(createFont("arial", 20))
          .setFocus(true)
            .setColor(color(150))
              ;
}





void draw() {

  if (mousePressed) {
    for (int i = 0; i<100; i++) {
      easing[i]=(i+2)*0.01;
    }
  } else {
    for (int i = 0; i<100; i++) {
      easing[i]=(i+2)*0.005;
    }
  }


  background (0);

    text("Hello, "+ cp5.get(Textfield.class, "name").getText() + ". Have a nice day.", 40, 400);
    println(cp5.get(Textfield.class, "name").getText());
  text(textValue, 100, 400);
    if (cp5.get(Textfield.class, "name").getText() == "") {
    fill(0);
    rect (40,400,100,100);
    println(0);
  }

  for (int i = 0; i<100; i++) {
    float targetX = mx;
    float dx = targetX - x[i];
    x[i] += dx * easing[i];

    float targetY = my;
    float dy = targetY - y[i];
    y[i] += dy * easing[i];

    ellipse(x[i], y[i], 100/(i+1), 100/(i+1));
  }

  fill (255);
} 


void keyPressed() {
  if ( key == CODED ) {
    if (keyCode == UP ) {
      my-=20;
    } 
    if ( keyCode == DOWN ) {
      my+=20;
    } 
    if ( keyCode == RIGHT) {
      mx+=20;
    } 
    if (keyCode == LEFT) { 
      mx-=20;
    }
  }
}
