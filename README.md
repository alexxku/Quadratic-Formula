# Quadratic-Formula
Using C# console application, calculate the quadratic formula and quadratic equation.



using System;

namespace QuadraticEquation
{
    class Program
    {
        static void Main(string[] args)
        {
            //Use constructor to create an instance of class.
            Program function = new Program();
           
            //Variables.
            double a, b, c, addx, subx;
            bool answer1, answer2;

            //Ask for user's input.
            Console.WriteLine("Using the Quadratic Formula to get x.\nEnter the coefficients for the terms a, b, c to make ax^2 + bx + c = 0 TRUE.\n");
            Console.Write("a = ");
            //Convert user's first input string to integer.
            a = Convert.ToInt32(Console.ReadLine());           
            Console.Write("b = ");
            //Convert user's second input string to integer.
            b = Convert.ToInt32(Console.ReadLine());   
            Console.Write("c = ");
            //Convert user's third input string to integer.
            c = Convert.ToInt32(Console.ReadLine());
            //Space.
            Console.WriteLine();

            //Decision statement. If a is any number but 0. Execute block code.
            if (a != 0)
            {
                //Calculate the addition part of quadratic formula. Accessing function AddQuadraticFormula method.
                addx = function.AddQuadraticFormula(a, b, c);
                //Calculate the subtraction part of quadratic formula. Accessing function SubQuadraticFormula method.
                subx = function.SubQuadraticFormula(a, b, c);

                //Decision statement. If quadratic formula solutions are all real numbers. Execute block code.
                if (((addx <= 0) || (addx >= 0)) && (((subx <= 0) || (subx >= 0))))
                {
                    //Display quadratic formula solutions.
                    Console.Write("Quadratic Formula: ");
                    Console.Write($"x = {addx}; ");
                    Console.WriteLine($"x = {subx}");

                    //Calculate if quadratic equation is equal to 0 using the first quadratic formula solution.
                    //Accessing function QuadracticEquation method.  
                    answer1 = function.QuadracticEquation(addx, a, b, c);
                    //Display first quadratic equation with inputs and answers.
                    Console.WriteLine($"\nThis solution makes ax^2 + bx + c = 0 \n({a})({addx})^2 + ({b})({addx}) + {c} = 0 \n{answer1}\n");

                    //Calculate if quadratic equation is equal to 0 using the second quadratic formula solution.
                    //Accessing function QuadracticEquation method.
                    answer2 = function.QuadracticEquation(subx, a, b, c);
                    //Display second quadratic equation with inputs and answers.
                    Console.WriteLine($"This solution makes ax^2 + bx + c = 0 \n({a})({subx})^2 + ({b})({subx}) + {c} = 0 \n{answer1}\n");

                }

                //Quadratic formula solutions are not real numbers. Imaginaries.
                else
                {
                    Console.WriteLine("Invalid. Sqaure root of a negative number will give you an imaginary number.");
                }
            }

            //Cannot divide by 0.
            else
            {
                Console.WriteLine("ERROR. a cannot be 0 since denominator will be be 0. ");
            }

            //Prevents console from closing until user presses enter.
            Console.ReadLine();
        }

        //Quadratic formula method with parameters. Addition section of QF.
        double AddQuadraticFormula(double A, double B, double C)
        {
            //Variable
            double X;

            //Calculate for X.
            X = ((-B) + Math.Sqrt(Math.Pow(B, 2) - (4 * A * C))) / (2 * A);

            //Return value to the method.
            return X;
        }

        //Quadratic formula method. Subration section.
        double SubQuadraticFormula(double A, double B, double C)
        {
            //Variable.
            double X;

            //Calculate for X.
            X = ((-B) - Math.Sqrt(Math.Pow(B, 2) - (4 * A * C))) / (2 * A);

            //Return value to the method.
            return X;
        }

        //Quadratic equation method. True or false.
        bool QuadracticEquation(double X, double A, double B, double C)
        {
            //Assign variable by calculating the quadratic equation.
            double answer = ((A * Math.Pow(X, 2)) + (B * X) + C);

            //Decision statement. If answer is equal to 0. Execute block code.
            if ((answer < .001) || (answer > -.001))
            {
                //Return boolean true to method
                return true;
            }
            //If answer is not equal to 0. Execute block code.
            else
            {
                //Return boolean false to method.
                return false;
            }
        }
    }
}
