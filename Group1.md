# <center>TOPIC: Problem 2</center>

<br>

<center> May 25th, 2018 </center>

<center> **The course: Linear Programming and Integer Programming (1) (Dr. Dennis CHEUNG)**</center>

<br>

<br>

<br>

 <center>**Group number: Group 1** </center>

 <center>**Group members:**  </center>

<center>**何逸 1630005019** </center>

 <center>**高之凡**  **1630005014** </center>

 <center>**刘骏杰**  **1630005038** </center>

<center>**陈浩颖  1630005003**</center>

<center>**黄城昱**  **1630005023**</center>

<center>**李智超**  **1630005031**</center>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

## <center>Background Instruction</center> 

  There are many choices in our life that affect our interests. How to maximize the benefits and minimize the losses are the problems we often consider? In the face of many conditions and restrictions, many times we have to give up another discount if we choose this one. When we encounter this situation, we need to use $0-1$ **Variables to Handle Conditional Requirement.**

 

 

A firm has $800$ units of a new product to be sold in some of six different new market areas. To develop the $i$ th market for sales, there is an initial research and advertising cost of $d_i$ dollars. Once opened, the *i*th market can sell up to $u_i$ units at a profit of  $c_i$dollars/unit. The data are in the table below:

 

![img](file://localhost/Users/liujunjie/Library/Group%20Containers/UBF8T346G9.Office/msoclip1/01/clip_image002.png)

 

Because of financial limitations, at most $4$ market areas can be developed. It is known that if both Markets $1$ and $2$ are developed, the firm must pay an extra tax of$ 30,000$ dollars; but if both Markets $3 $and $4$ are developed, the firm receives tax credits of $20,000$ dollars. What areas should be developed and how many units should each of these areas receive so as to maximize total profit?

 

 

  In this problem we can easily see if income is the largest item in the Market of 1, we are considering in time should be as far as possible choose Market $1$, but at the same time to choose the Market $3$ and Market $4$ can get $20000$, this time is in a dilemma, we need to list the formula using lingo to work out the optimal solution.

<br>

## <center>Solution</center> 

  First we show the solution we got.

  At the beginning we solve this problem, we need to set some variables.

$X(i), i=1, 2…6$: the amount of units which (i)th market would like to sell. 

$Z(i), i=1, 2…6$: the $0-1$ variable, to choose whether the market open or not. 

 

 From the information of the question, we can list some constraints，

 We consider that $x_i$ should be integers, so we have:

```mathematica
@GIN(x1);
@GIN(x2);
@GIN(x3);
@GIN(x4);
@GIN(x5);
@GIN(x6); 
```

  Since the (i)th market can sell up to u(i) units at a profit of c(i), we can get the information from the table, and have following constraints:

```mathematica
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;
```

We need to choose whether the market open or not by the constraints of the problem. so we need to add 6 0-1 variables to switch.  

So, we let $z_i (i=1,2…6) $to be the $0-1$ variables, and we use following constraints to control:

```mathematica
9999*z1>=x1;
9999*z2>=x2;
9999*z3>=x3;
9999*z4>=x4;
9999*z5>=x5;
9999*z6>=x6;
```

  Since at most $4$ market areas can be developed, we can write:

````mathematica
z1+z2+z3+z4+z5+z6<=4; 
````

  And this firm only has $800$ units of a new product to be sold. So we can have following constraints:

```mathematica
x1+x2+x3+x4+x5+x6=800;
```

After writing the constraints of this problem, we consider about the profit. The profit of each unit times the amount of units of each market, we can get the profit that the firm sell the products.  Then we should minus the advertisement cost, minus or add the extra tax, then finally we can get the profit of this problem.  

In order to get the maximize profit, we have following constraints:

```mathematica
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000z1z2+20000z3z4-z121000-z224000-z318000-11000z4-16000z5-18000z6;
```

If both $1$ st market and $2$ nd market open, we need to pay extra $30000$ dollars, so we use `30000*z1*z2 ` to choose whether the firm need to pay the tax or not; if both $3$ rd market and $4$th market open, the government can pay us for the firm 20000 dollars' tax credits, so we use `z3*z4*20000` to choose whether the government should pay the tax credit to the firm. 

 In summary, we put all these constraints into lingo, and have following code:

```mathematica
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000z1z2+ 0000z3z4-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<=4;

x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;
9999*z1>=x1;
9999*z2>=x2;
9999*z3>=x3;
9999*z4>=x4;
9999*z5>=x5;
9999*z6>=x6;
x1+x2+x3+x4+x5+x6=800;

@GIN(x1);
@GIN(x2);
@GIN(x3);
@GIN(x4);
@GIN(x5);
@GIN(x6);
@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5);
@BIN(z6);
```

Then we can calculate the optimal solution: the maximize profit of this problem is $114000$ dollars, which $1$ st market has $300$ units, $ 3 $ rd market has $240$ units, 4th market has $40$ units, $6$ th market has $220$ units. 

![img](file://localhost/Users/liujunjie/Library/Group%20Containers/UBF8T346G9.Office/msoclip1/01/clip_image004.png)

 Second we considered about the textbook

In the process we try different ways to solve this problem, we find the Example $6.2.4$ and Example $6.2.5$ of chapter $6$ from our textbook; 

![img](file://localhost/Users/liujunjie/Library/Group%20Containers/UBF8T346G9.Office/msoclip1/01/clip_image006.png)

![img](file://localhost/Users/liujunjie/Library/Group%20Containers/UBF8T346G9.Office/msoclip1/01/clip_image008.png)

These examples show a different way to set the $0-1$ variables. 

And then, we try this way, set $2$ new $0-1$ variables $y_1$, $y_2$:

```mathematica
y1<(z1+z2)/2;
y2<(z3+z4)/2;
```

​            Then we use `30000*y1` to instead `30000*z1*z2`; use `20000*y2` to instead `30000*z3*z4`;

​            The maximize of profit is changed:

```mathematica
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000y1+20000y2-z121000-z224000-z318000-11000z4-16000z5-18000z6;
```

Then add new constraints in lingo:

```mathematica
y1<(z1+z2)/2;
y2<(z3+z4)/2;

@BIN(y1);
@BIN(y2);
```

  After the calculation, we can get a different answer:

![img](file://localhost/Users/liujunjie/Library/Group%20Containers/UBF8T346G9.Office/msoclip1/01/clip_image010.png)

  In this way, lingo gives us the answer that the maximize profit is $116600$ dollars, which open the $1$st, $2$ nd, $3$ rd, $4$ th markets, and the 1st market has $300$ units, $2$ nd market has $360$ units, $3$ rd has $140 $ units, $4$ th markets open the market, but has no units. 

Then we try to find why the solutions are different, from the details of this solution, we find some mistakes.  

  First, if both $3$ rd and $4$ th open, the firm can get extra $20000$ dollars’ tax credits from the government. So in this solution, the firm open the 4th market but does not sell any things just in order to get $20000$ dollars’ tax credits. Although this way is allowed in this problem, but this not an optimal way.  

  Second, we can find that the $0-1$ variable $z_1$ and $z_2$ are equal to $1$, but $y_1$ switch to $0$. In our problem, if $z_1$ and $z_2$ equal to $1$, which means that $1$ st and $2$ nd markets are open, the firm need to pay extra $30000 $dollars’ tax. but if we use the constraints:

```mathematica
y1<(z1+z2)/2;
y2<(z3+z4)/2;
```

$y_1$ would like to choose the variable which can provide more profit. It’s obvious if $y_1=0$ the firm does not need to pay the extra tax, and this way can benefit the firm to get more profit.  So $y_1$ choose the variable $0$, no matter what the value of $z_1$ and $z_2$. But this way is not allowed in the problem, and these constraints cannot constraint the $ 0-1$ variables range. So in this way, the actually profit need to minus $30000$ dollars of tax from the maximize profit $116600$ which calculates by lingo. So the actually profit of this solution is $86600$, and this is not the optimal solution of this problem. Because we need to calculate the maximize profit, for the method which the book provides us, it’s not suitable for this problem. 

  So after some other methods trying, we think that the optimal solution is: The maximize profit of this problem is $114000$ dollars, which $1$ st market has $300$ units, 3nd market has $240$ units, 4th market has $40$ units, $6$ th market has $220$ units.

# Discussion 

  In total we write $4 $ methods to solve the problem, except the method we mentioned above here are other $3$ methods.

1.

```mathematica
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000z1z2+20000z3z4-z121000-z224000-z318000-11000z4-16000z5-18000*z6;

z1+z2+z3+z4+z5+z6<=4;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;

x1+x2+x3+x4+x5+x6=800;

@GIN(x1);
@GIN(x2);
@GIN(x3);
@GIN(x4);
@GIN(x5);
@GIN(x6);
@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5);
@BIN(z6);
```

 2.

```mathematica
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000z1z2+20000z3z4-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<=4;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;
z1x1+z2x2+z3x3+z4x4+z5x5+z6x6=800;

@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5);
@BIN(z6);
```

 

3.

```mathematica
1. max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000z1z2+20000z3z4-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<4;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;
9999*x1>=z1;
9999*x2>=z2;
9999*x3>=z3;
9999*x4>=z4;
9999*x5>=z5;
9999*x6>=z6;
x1+x2+x3+x4+x5+x6=800;

@GIN(x1);
@GIN(x2);
@GIN(x3);
@GIN(x4);
@GIN(x5);
@GIN(x6);
@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5); 
@BIN(z6);
```

All this three above can get the solution $114000$ by this three methods. 

Then we change the $0-1$ variable from `-30000*z1*z2+20000*z3*z4` to `-30000*y1+20000*y2` as we do in the previous one.

1.

```mathematica
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000y1+20000y2-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<=4;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;
y1<=(z1+z2)/2;
y2<=(z3+z4)/2;
x1+x2+x3+x4+x5+x6=800;

@GIN(x1);
@GIN(x2);
@GIN(x3);
@GIN(x4);
@GIN(x5);
@GIN(x6);
@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5);
@BIN(z6);
@BIN(y1);
@BIN(y2);
```

2.

```mathematica
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000y1+20000y2-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<=4;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;
y1<=(z1+z2)/2;
y2<=(z3+z4)/2;
z1x1+z2x2+z3x3+z4x4+z5x5+z6x6=800;

@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5);
@BIN(z6); 
@BIN(y1);
@BIN(y2);
```

3.

```mathematica
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000y1+20000y2-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<4;

x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;
9999*x1>=z1;
9999*x2>=z2;
9999*x3>=z3;
9999*x4>=z4;
9999*x5>=z5;
9999*x6>=z6; 
y1<=(z1+z2)/2;
y2<=(z3+z4)/2;
x1+x2+x3+x4+x5+x6=800;

@GIN(x1);
@GIN(x2);
@GIN(x3);
@GIN(x4);
@GIN(x5);
@GIN(x6);
@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5); 
@BIN(z6); 
@BIN(y1);
@BIN(y2);
```

We can get solution like this:

1．

![img](file://localhost/Users/liujunjie/Library/Group%20Containers/UBF8T346G9.Office/msoclip1/01/clip_image012.png)

 

2．

![img](file://localhost/Users/liujunjie/Library/Group%20Containers/UBF8T346G9.Office/msoclip1/01/clip_image014.png)

3．

![img](file://localhost/Users/liujunjie/Library/Group%20Containers/UBF8T346G9.Office/msoclip1/01/clip_image016.png)

 

They all cannot get $114000$, and not all of them are $116600$, therefore, we think Lingo may have different priority in different case.

<br>

<br>

# <center>Conclusion</center>

  Through the time we were solving the problem, we also had an insight into Lingo. When we use Lingo we should not only consider about what we write into it, but also make double check.

  Finally, we get thee solution, the maximize profit of this problem is $114000$ dollars, which $1$st market has $300$ units, $3$ nd market has $240$ units, 4th market has $40$ units, $6$ th market has $220$ units.

<br>

<br>

# <center>Appendix (Lingo Code) </center>

```mathematica
(*begin--the lingo code*)

(* begin--method one*)
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000z1z2+ 0000z3z4-z121000-z224000-z318000-11000z4-16000z5-18000z6;
z1+z2+z3+z4+z5+z6<=4;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;

9999*z1>=x1;
9999*z2>=x2;
9999*z3>=x3;
9999*z4>=x4;
9999*z5>=x5;
9999*z6>=x6;
x1+x2+x3+x4+x5+x6=800;

@GIN(x1);
@GIN(x2);
@GIN(x3);
@GIN(x4);
@GIN(x5);
@GIN(x6);
@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5);
@BIN(z6);
(*end*)
 
(*begin--method two*)
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000z1z2+z3z420000-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<=4;
x1+x2+x3+x4+x5+x6<=800;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;

@GIN(x1);
@GIN(x2);
@GIN(x3);
@GIN(x4);
@GIN(x5);
@GIN(x6);
@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5);
@BIN(z6);
(*end*)
 
(*begin--method two*)
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000z1z2+z3z420000-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<=4;
z1x1+z2x2+z3x3+z4x4+z5x5+z6x6=800;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;

@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5);
@BIN(z6);
(*end*)
 
(*begin--method three*)
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000z1z2+20000z3z4-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<4;
x1+x2+x3+x4+x5+x6=800;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;
9999*x1>=z1;
9999*x2>=z2;
9999*x3>=z3;
9999*x4>=z4;
9999*x5>=z5;
9999*x6>=z6;

@GIN(x1);
@GIN(x2);
@GIN(x3);
@GIN(x4);
@GIN(x5);
@GIN(x6);
@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5);
@BIN(z6);
(*end*)
 
(*begin--method four*)
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000y1+20000y2-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<=4;
x1+x2+x3+x4+x5+x6=800;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;
y1<=(z1+z2)/2;
y2<=(z3+z4)/2;

@GIN(x1);
@GIN(x2);
@GIN(x3);
@GIN(x4);
@GIN(x5);
@GIN(x6);
@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5);
@BIN(z6);
@BIN(y1);
@BIN(y2);
(*end*)
 
(*begin--method five*)
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000y1+20000y2-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<=4;
z1x1+z2x2+z3x3+z4x4+z5x5+z6x6=800;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;
y1<=(z1+z2)/2;
y2<=(z3+z4)/2;

@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5);
@BIN(z6); 
@BIN(y1);
@BIN(y2);
(*end*)

(*begin--method five*)
max=240z1x1+200z2x2+190z3x3+120z4x4+170z5x5+180z6x6-30000y1+20000y2-z121000-z224000-z318000-11000z4-16000z5-18000z6;

z1+z2+z3+z4+z5+z6<4;
x1+x2+x3+x4+x5+x6=800;
x1<=300;
x2<=360;
x3<=240;
x4<=160;
x5<=200;
x6<=220;
9999*x1>=z1;
9999*x2>=z2;
9999*x3>=z3;
9999*x4>=z4;
9999*x5>=z5;
9999*x6>=z6; 
y1<=(z1+z2)/2;
y2<=(z3+z4)/2;

@GIN(x1);
@GIN(x2);
@GIN(x3);
@GIN(x4);
@GIN(x5);
@GIN(x6);
@BIN(z1);
@BIN(z2);
@BIN(z3);
@BIN(z4);
@BIN(z5); 
@BIN(z6); 
@BIN(y1);
@BIN(y2);
(*end*)

(*end of the code*)
```



 