Although I don't have time to do this right now because I want to develop a game, ever since I started programming, it has been my dream to be able to work with polynomials. Something about storing 100s of polynomials, being able to add, subtract, multiply and divide, integrate and differentiate AND STORE them?? is extremely powerful (which I don't even think Desmos allows you to do that). I thought I could do it with strings quickly realized that a data structure was badly needed. But now it might actually be possible to implement this thanks to multiplication array. Basically it stores factors: M(x,x) = x*x. finding how to do the operations was a challenge but not impossible: 

Starting off with Polynomial Addition, through operator overloading, you can achieve this by adding the smaller size array to the last term of the bigger one and divide it by all the terms of the bigger array except the last one, ex: 
M(3x,x) + M(x) = M(3x, x +M(x)/M(3x))
// this equates to 3x(x+x/3x) => 3x(x+ 1/3)

Polynomial subtraction is also very simple, and can be achieved by operator overloading:
M(3x,x) - M(x) 
M(3x,x - M(x)/M(3x)) 
// which is = 3x(x-1/3)

Next is Multiplication which is so easy,
just addall() elements. 
Ex: 
var = M(x,3x,2).addall(M(2x,x,3x)
// polynomial term is now 36x^5 

Polynomial division, which is hardest because you can't divide by 0. So we'll need to do some exception handling here.

Which brings me to the next topic, most exciting and least developed feature so far: Generating piecewise functions to handle discontinuity so that we can differentiate & integrate on at least the parts where we care about. The algorithm used is areas and as of now does not work with coefficients in front of variables (Page 2)

Polynomial Differentiate: 
Var = M(3x,x,4x); 
//d/dx 12x^3 = 36x^2
DDX(Var,x) will return Var*len(Var)/M(x)

Polynomial Integration:
INT(var,x) will return (var.append(x))*len(var)
