
# Day 1 Log Entry: Variables & Data Tracking - 
I used variables for images I added to my code and for their respective movements and coordinate names. Some variables I have are:
loid - Character image, loidX - Character’s x-coordinate, loidY - Character’s y-coordinate, loidSpeed - Character’s speed

- Arrays (Int [ ]): Arrays are variables that store multiple values. I used arrays to make many enemy characters without using too many variables. I used a variable for an enemy’s x/y coordinate and x/y speeds because it was using the same image and functions but had different numerical values. Originally I did not know that an array only shows when called on. After multiple trials, I fixed this issue.
- Strings: Strings represent a sequence of characters. I used a String to print the title of the game on the introduction page. Instead of repeatedly writing the title, I called the variable “label” to make a shorter code.
- Int: Int variables are primitive data types that store whole numbers. I used this variable to organize values I will repeatedly use in the game. For example, I initialized my character’s original position to be (500, 300) so that the user can move from this position to wherever they want to. 
- Boolean: Booleans are variables that represent true or false based on their conditions. I used these boolean variables to move the main character when the user presses a key (true) and when the user stops pressing a key (false). These variables help process the singular input and provide a singular output, helping me efficiently finish the movements.
- PImage: This variable is used to generate images. This is very helpful because it is visually appealing to the viewer and helps me fix placements of certain characters. The variable names given to each picture is useful so that I will not have to recall the picture, but only the name of the picture.
- Global Variables: Global variables are variables defined outside of methods. This is extremely useful when a particular variable is used in many methods. I used many global variables such as score and life because they were used in a lot of my methods.
- Local Variables: Local variables are variables given for specific methods to use. A local variable I used was “i” to call values out of arrays. An issue I had with this was that I repeatedly forgot that local variables were only defined within their method. So when I tried to use the same variable in another method, it didn’t work, hence I used return type variables instead or I just created another one. 

  //Array Example
enemyX = new int []{20, 170, 300, 350, 200};
enemyY = new int[]{40, 290, 100, 350, 200};
enemySpeedX = new int[]{1, 3, 2, 3, 2};
enemySpeedY = new int[]{3, 1, 2, 4, 2};
//String Example
String label = "A Spy On A Mission";
//Int Example
int score = 0, loidX = 500, loidY = 300, loidSpeed = 10, screen = 0;
//Boolean Example
boolean left = false, right = false, up = false, down = false;
//PImage Example
PImage loid, enemy, gems, forest, Level2Element, longwall,
  greatwall;

  loid = loadImage("loid.png");
  forest = loadImage("forest.jpg");
  enemy = loadImage("ninja.png");
  gems = loadImage("gem.png");
  longwall = loadImage("GreatWall.png");
  greatwall = loadImage("Great Wall.png");
  Level2Element = loadImage("amazon.png");
//Local Variable Example ("i")
 for (int i = 0; i < lines.length; i++) {
      text(lines[i], 20, 30 + i * 20);
    }
//Global Variable Example
int score = 0;
int life = 10;

# Day 2 Log Entry: Selection Structure- 

I used a concept called selection structure in my code to create movement depending on a given input. Selection structures are decision making statements that execute code based on a true or false condition. In my game, I used it in the keyPressed, keyReleased, and draw methods to help my character move based on the user's input. I specifically used if and if-else statements. This is because an if statement only executes a particular block of code while an if-else statement executes an alternate block of code if the input does not meet the first condition.

//if & if-else Examples
void keyPressed(){
  if(keyCode == LEFT){
    left = true;//Character moves left while key is pressed
  }else if(keyCode == RIGHT){
    right = true;//Character moves right while key is pressed
  }else if(keyCode == UP){
    up = true;//Character moves up while key is pressed
  }else if(keyCode == DOWN){
    down = true;//Character moves down while key is pressed
  }if(loidX < 0){//Parameter to keep character within canvas
      loidX = 0;
    } else if(loidX > 1000){
      loidX = 1000;//Parameter to keep character within canvas
    }
}

void keyReleased(){
  if(keyCode == LEFT){
    left = false;
  }else if(keyCode == RIGHT){
    right = false;
  }else if(keyCode == UP){
    up = false;
  }else if(keyCode == DOWN){
    down = false;
  }
}

void draw(){
  if(left){
    loidX -= loidSpeed;
  }else if(right){
    loidX += loidSpeed;
  }else if(up){
    loidY -=loidSpeed;
  }else if(down){
    loidY +=loidSpeed;
  }
}

My code states if a certain key is pressed/released, its respective variable is true/false. If true, this output goes to my draw function and sets the speed for the specific coordinate. If false, the character does not move. For example, if the left key is pressed, "left" variable is true. In the draw function (in another selection statement), because left is true, the character's speed is subtracted from its x-coordinate. The other movements such as up, right, and down are done using an if-else statement. This is useful when the input doen not match the first condition, the code automatically executes the next condition met. The only drawback to using selection statements is that it requires multiple brackets. Due to this, it was difficult for me to accurately count the brackets for the statements apart from other methods and separate conditions. But after a while I discovered that in processing, when you hover over an open bracket, it shows the location of its closed bracket. This function greatly helps me now as I do not have to individually count the brackets. There are other types of selection statements but these are the most common function I use throughout my code. Using selection structures greatly helps simplify and organize my game. By using these functions, I can set my own organized conditions with minimal lines.

# Day 3 Log Entry: Repetition Structure - 
I used a for-loop to read each line of my text file. Repetition structures are blocks of code repeatedly executed until the condition becomes false. A for-loop is a type of repetition structure that is ideal when the number of iterations are known. In this loop, I wrote a condition using the variable "i". I initially wrote, "i" is equal to 0, and declared i is lesser than the length (number of lines in the text file). If this condition is true, starting with "i" equal to zero (first line of text file) is printed 20 pixels from the left and (starting initially with a height of 30 pixels) adds 20 pixels under every line above it (so the text will not overlap). Then, "i" is incremented and the process repeats until the last line of code is printed. I used a for-loop to access my text file because this repetition structure allows me to go through every iteration to print each line. An issue I faced was connecting my text file to my original code. I had my file ready, but it was difficult for me to use it in my code. Finally, I looked at how I called on the values of my array and realized that I could try to do the same (calling lines of my file). So, I used the same for-loop structure I used in an array and changed the output values. This was how I was able to fix this issue. In conclusion, repetition structures repeatedly execute blocks of code when a certain condition is met, helping coders efficiently write code without multiple lines.

//Loop Example
lines = loadStrings("chibiloidfile.txt");//In void setup

for (int i = 0; i < lines.length; i++) {//In void draw 
      text(lines[i], 20, 30 + i * 20);
    }

# Day 4 Log Entry: Arrays & Data Structures-

I used an array to make multiple enemy characters, without using many variables. Arrays are data structures that hold multiple values of one variable. They allow us to organize multiple data values without a lot of variables. In the void setup, I initialized three variables, enemyGemX, enemyGemY, and enemyGemSpeed. I gave multiple values to each variable within this method for the coordinates and speeds of the enemy characters. In a void nextLevel1, I wrote a for loop so the code accesses each value when it runs. In this for-loop I created a variable "i", and wrote the condition, "i" is lesser than the length (number of values) of enemyGemX. If the condition is true, the code generates a picture for this iteration, enemyGemX[i] ([i] is a certain value in the array) coordinate is then added to enemyGemSpeed[i], allowing it to move horizontally. Once this iteration is complete, the variable "i" goes through the loop repeatedly until no values are left in the array. Originally, I wrote the values of the array outside of the setup function which messed up my code. I believed that if I wrote the array in the setup method, the images would show up throughout the game (not at the exact place I wanted them to appear). After a couple of trials and errors, I realized that when you set the array inside of the setup function, the characters will not be visible to the viewer until the values are called on, hence the repetition structure. Overall, arrays are very helpful for me to make multiple characters without multiple pictures/lines of code. They make my code much more efficient and are easily accessible through for-loops.

//Array EnemyGem Positions Initialized
void setup() {
  pixelDensity(1);
  size(1000, 600);
  enemyGem = loadImage("ninjawithgem.png");
  enemyGemX = new int []{20, 170, 300, 350, 200};
  enemyGemY = new int[]{40, 290, 100, 350, 200};
  enemyGemSpeed = new int[]{1, 3, 6, 3, 6};
}
//Using for-loop to access an array
void nextLevel1(){
for (int i = 0; i< enemyGemX.length; i++) {
    image(enemyGem, enemyGemX[i], enemyGemY[i], 120, 120);
    enemyGemX[i] += enemyGemSpeed[i];
}

# Day 5 Log Entry: Custom Functions, Error Checking, And Restrictions - 
I used custom functions, error checking techniques, and restrictions to enhance my game and its main features. 

Custom functions are methods designed to perform a specific task. In my first example, I coded Level 2 (character position, enemies array loop, gems array loop) of my game in a separate method named "nextLevel2( )". I made a custom method so that the second game is played only when this method is called. By doing this, I am able to organize my code and efficiently run it without the conditions colliding with any other levels. When coding, it was difficult for me to organize the method itself. Originally, my methods had many unnecessary lines I turned into comments (so that I would not lose them and at the same time will not mess up test runs). This made my method harder to read with the distracting comments and extra spacing. To solve this, I immediately deleted any extra characters. This made it easier for me to code as I was only able to view the necessary lines instead. In my second example, I made a method called "updateScore( )", which increments the score value by one when isCollected( ) is true (either an enemy with a gem or a green gem collides with the character). Having this function as its own separate method became very useful as I had to call it in every nextLevel1/2/3/4/5 method. This makes it much more efficient because now I can just call the method's name when needed instead of rewriting the entire logic block.

Error checking detects issues that may arise during the game which is not specifically addressed in the main code. I used a method called try-catch in my isCollected(int i) method. The code runs normally, but if it discovers the program is trying to access an out-of-bounds array index value, it returns false. This is extremely helpful because if any error happens, I do not have to predict every possible index mistake. Instead, this function eliminates any index error when found. The challenging part was creating the try-catch function because I have never done it before. I used some online tutorials and finally got it to work. I am very glad I learned about this function so that in the future, I can implement it instead of predicting every possibility.

Restrictions are constraints or conditions that limit a code. Restrictions are extremely important so that the program may run smoothly with the user's input. A challenge I encountered in my game was that my character was able to move outside of the canvas. This was an issue because my viewer would not be able to play the game properly. To solve this, I put a restriction on the character's x-coordinate and y-coordinate so that it stayed within the screen when the code ran. By using if and if-else statements along with boolean expressions, it was pretty simple to do this because the only outputs were: true and false. So, if the character's x-coordinate is greater than the canvas size, it is equal to canvas size (this format is repeated for other directions too). 

To conclude, using custom methods, checking errors, and applying restrictions helped modify my game, preventing any unnecessary character inputs and issues from interrupting my game sequence.

//Custom Function Example 1
void nextLevel2() {
  image(forest, 0, 0, 1000, 600);
  image(loid, loidX, loidY, 120, 120);
  loidMoves();
  for (int i = 0; i < enemyX.length; i++) {
    image(enemy, enemyX[i], enemyY[i], 120, 120);
    life = updateLives(i, life);
    enemyX[i] += enemySpeedX[i];
    enemyY[i] += enemySpeedY[i];
    if (enemyX[i] + 100 > width || enemyX[i] < 0) {
      enemySpeedX[i] *= -1;
    } else if (enemyY[i] + 100 > height || enemyY[i] < 0) {
      enemySpeedY[i] *= -1;
    }
  }
  for (int i = 0; i < gemX.length; i++) {
    image(gems, gemX[i], gemY[i], 50, 50);
    score = updateScore(i, score);
  }
  if (life == 0) {
    resetGame = true;
  }
}

//Custom Function Example 2
int updateScore(int i, int score) {
  if (isCollected(i)) {
    score++;
    enemyGemY[i] = (int)random(height);
    enemyGemX[i] = -50;
    gemX[i] = (int)random(width);
    gemY[i] = (int)random(height);
  }
  return score;
}

//Error Checking Using Try-Catch
boolean isCollected(int i) {
  try {
    if ((screen == 3 || screen == 11) && loidX < enemyGemX[i] + 80 &&
      loidX + 100 > enemyGemX[i] && loidY < enemyGemY[i] + 80 &&
      loidY + 100 > enemyGemY[i]) {
      return true;
    }

    if ((screen == 5 || screen == 9)&& loidX < gemX[i] + 50 &&
      loidX + 100 > gemX[i] && loidY < gemY[i] + 50 && loidY + 100 > gemY[i]) {
      return true;
    }
  }
  /*occurs when program is trying to access an index of an array which is out of bounds
   index is considered illegal if it is negative or greater than or equal to the (length)
   of the array
   */
  catch (ArrayIndexOutOfBoundsException e) {
    return false;
  }

  return false;
}

//Restriction On Character's Movement
 if (loidX < 0) {//loid's parameter to keep loid within canvas
    loidX = 0;
  } else if (loidX > 1000) {
    loidX = 1000;//loid's parameter to keep loid within canvas
  } else if (loidY < 0) {//loid's parameter to keep loid within canvas
    loidY = 0;
  } else if (loidY > 600) {
    loidY = 600;//loid's parameter to keep loid within canvas
  }

  ## Overall, this was a very fun project to work on. I learned a lot from this course because of Ms. Kim's amazing teaching skills. I hope I can take this course next year with her :)
  
