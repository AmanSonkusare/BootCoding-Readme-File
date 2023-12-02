# Assignment 5

In the last assignment you learned how to create your own simple objects. One of the advantages of building software 
using objects is that it makes it relatively easy to use software components that other people have built. In this assignment, 
you will use the Java's built-in graphics and containers, combined with a simple framework that we provide. 

## Requirement( in brief)
- Add three different shapes to the initial window we provide.
- Add three instances of the BouncingBox class to your window, moving in different directions. Use an ArrayList to hold them.

## Setup
1. (Optional) Create a new project in Eclipse, with whatever name you want. 

2. Create three classes: SimpleDraw, BouncingBox, and DrawGraphics. Copy and paste the code for these classes from below. 

3. Run the example program. If Eclipse gives you trouble, open SimpleDraw and run that, as it contains the main method for the program. You should see a window that looks like the following:

## Part One:Drawing Graphics
Open the DrawGraphics class. The draw method is what draws the contents of the window. Currently, there is a line and 
a square with a border around it. Feel free to remove these, if you want. Add at least three different shapes to the window. 
Read the API documentation for the java.awt.Graphics class to find what methods are provided. You can draw 
rectangles, arcs, lines, text, ovals, polygons, and, if you want to do some extra work, images. Be creative! 

Note: You should only modify the DrawGraphics class for this step. The other classes contain a bunch of code required to 
create a window in Java that you do not need to change or understand.

## Part Two:contains and Animation
The DrawGraphics class supports animation. The draw method gets called 20 times a second, in order to draw each 
individual frame. The BouncingBox class also includes animation support. To get the box to move, call 
setMovementVector method from the DrawGraphics constructor, providing an x and y offset. For example, the value (1, 
0) moves the box to the right slowly, while (0, -2) will move it up faster. You only need to call this method once to keep it 
moving in that direction. In other words, don't call setMovementVector from the draw method, call it from the 
constructor.

Add at least three boxes to your window, moving in different directions. To do this, put three BouncingBox instances in an 
ArrayList, as part of the DrawGraphics constructor. Then, call the draw method on each of the boxes from 
DrawGraphics.draw, using a loop. 

Optional: If you want to experiment, create your own animated object. Copy BouncingBox as a starting point, then edit 
the code in its draw method. You could create something with more complicated movement, and/or something that looks 
better than what I created in five minutes.

## Submission Instructions
Submit your DrawGraphics.java file via Stellar.

## SimpleDraw.java
__import__ java.awt.Color;

__import__ java.awt.Dimension;

__import__ java.awt.Graphics;

__import__ java.awt.Graphics2D;

__import__ java.awt.RenderingHints;

__import__ java.awt.event.
WindowAdapter;

__import__ java.awt.event.WindowEvent;

__import__ javax.swing.JFrame;

__import__ javax.swing.JPanel;

/** Displays a window and delegates drawing to DrawGraphics. */ 
__public class__ SimpleDraw __extends__ JPanel __implements__ Runnable {

__private static final long__ serialVersionUID = -7469734580960165754L;

__private boolean__ animate = true;

__private final int__ FRAME_DELAY = 50; // 50 ms = 20 FPS 

__public static final int__ WIDTH = 300;

__public static final int__ HEIGHT = 300;

__private__ DrawGraphics draw;

__public__ SimpleDraw

(DrawGraphics drawer) {
__this__.draw = drawer;
}

/** Paint callback from Swing. Draw graphics using g. */ 

__public void__ paintComponent(Graphics g) {
__super__.paintComponent(g);

// Enable anti-aliasing for better looking graphics
 Graphics2D g2 = (Graphics2D) g;
g2.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
draw.draw(g2);
}


/** Enables periodic repaint calls. */ 

__public synchronized void__ start() {
animate = true;
}

/** Pauses animation. */ 

__public synchronized void__ stop() {
animate = false;
}

__private synchronized boolean__ animationEnabled() {
return animate;
}

__public void__ run() {

__while__ (true) {

__if__ (animationEnabled()) {
repaint();
}

__try__ {
Thread.sleep(FRAME_DELAY);
} 

__catch__ (InterruptedException e) {
throw new RuntimeException(e);
}
}
}

__public static void__ main(String args[]) {

__final__ SimpleDraw content = __new__ SimpleDraw(__new__ DrawGraphics());

 JFrame frame = __new__ JFrame("Graphics!");

 Color bgColor = Color.white;
frame.setBackground(bgColor);
content.setBackground(bgColor);

// content.setSize(WIDTH, HEIGHT);

// content.setMinimumSize(new Dimension(WIDTH, HEIGHT)); 

content.setPreferredSize(new Dimension(WIDTH, HEIGHT));

// frame.setSize(WIDTH, HEIGHT); 
frame.setContentPane(content);

frame.setResizable(false);

frame.pack();

frame.addWindowListener(__new__ WindowAdapter() {

__public void__ windowClosing(WindowEvent e) { System.exit(0); }

__public void__ windowDeiconified(WindowEvent e) { content.start(); }

__public void__ windowIconified(WindowEvent e) { content.stop(); }
});

__new__ Thread(content).start();

frame.setVisible(true);
}
}

## BouncingBox.java

__import__ java.awt.BasicStroke;

__import__ java.awt.Color;

__import__ java.awt.Graphics;

__import__ java.awt.Graphics2D;

__public class__ BouncingBox {
    
__int__ x;

__int__ y;

 Color color;

__int__ xDirection = 0;

__int__ yDirection = 0;

__final int SIZE__ = 20;

/**
 * Initialize a new box with its center located at (startX, startY), filled
 * with startColor.
 */

__public__ BouncingBox(__int__ startX, __int__ startY, Color startColor) {

x = startX;

y = startY;

color = startColor;
}

/** Draws the box at its current position on to surface. */ 

__public void__ draw(Graphics surface) {

// Draw the object 

surface.setColor(color);

surface.fillRect(x - SIZE/2, y - SIZE/2, SIZE, SIZE);

surface.setColor(Color.BLACK);

((Graphics2D) surface).setStroke(__new__ BasicStroke(3.0f));

surface.drawRect(x - SIZE/2, y - SIZE/2, SIZE, SIZE);

// Move the center of the 
object each time we draw it 

x += xDirection;
y += yDirection;

// If we have hit the edge and are moving in the wrong direction, reverse direction

// We check the direction because if a box is placed near the wall, we would get "stuck"

// rather than moving in the right direction 

__if__ ((x - SIZE/2 __<= 0__ __&&__ xDirection __<__ 0) ||
(x __+__ SIZE/2 __>=__ SimpleDraw.WIDTH __&&__ xDirection __>__ 0)) {
xDirection = -xDirection;
}

__if__ ((y - SIZE/2 __<= 0__ __&&__yDirection __<__ 0) ||
(y + SIZE/2 __>=__ SimpleDraw.HEIGHT __&&__ yDirection __>__ 0)) {
yDirection = -yDirection;
}
}

__public void__ setMovementVector(__int__ xIncrement, __int__ yIncrement) {
xDirection = xIncrement;
yDirection = yIncrement;
}
}


## DrawGraphics.java 
__import__ java.awt.Color;

__import__ java.awt.Graphics;

__public class__ DrawGraphics {
BouncingBox box;

/** Initializes this class for drawing. */ 

__public__ DrawGraphics() {
box = __new__ BouncingBox(200, 50, Color.RED);
}

/** Draw the contents of the window on surface. Called 20 times per second. */ 

__public void__ draw(Graphics surface) {
surface.drawLine(50, 50, 250, 250);
box.draw(surface);
}
}


## Contributing

Contributions are always welcome!

See `contributing.md` for ways to get started.

Please adhere to this project's `code of conduct`.


## Acknowledgements

 - [Awesome Readme Templates](https://awesomeopensource.com/project/elangosundar/awesome-README-templates)
 - [Awesome README](https://github.com/matiassingers/awesome-readme)
 - [How to write a Good readme](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)

