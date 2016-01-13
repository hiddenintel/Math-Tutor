# Math-Tutor
This is the Math Tutor 5000! This program will request the user to enter the number of questions they would like to receive, then can choose the type of math problem they would like to receive. The users number of correct/wrong answers will be tracked to provide the user with an overall tally of their marks upon choosing to exit.


// Author: Roel Cuellar
// File Name: TT10_L3_Cuellar.cpp 

#include <iostream>
#include <iomanip>
#include <stdlib.h>
#include <time.h>

using namespace std;

//Function which allows me to request the menu to be displayed during cases 
int display_menu(){
	int choice = 0;       
	cout << "1. For Addition" << endl;
	cout << "2. For Subtraction" << endl;
	cout << "3. For Multiplication" << endl;
	cout << "4. For Division" << endl;
	cout << "5. Quit Program From Menu\n" << endl; 
	cout << "Choose an option from the menu above: ";
	cin >> choice;
	return choice;
	
}

//Had to set these up outside the main, as I call them later on once all cases
//have completed running!

//Setting value holders for overall number of right and wrong answers
double overall_addright=0, overall_addwrong=0, overall_addquest=0;
//Setting counters for number of right and wrong answers
double overall_subright=0, overall_subwrong=0, overall_subquest=0;
//Setting counters for number of right and wrong answers
double overall_multright=0, overall_multwrong=0, overall_multquest=0;
//Setting counters for number of right and wrong answers
double overall_divright=0, overall_divwrong=0, overall_divquest=0;

int main(){
    //Some snarky commentary to the user
    cout << "Welcome to the Math Tutor 5000!" << endl;
    cout << "I am glad that you are working on your math skills!" << endl;
    cout << "The Math Tutor 5000 is much better than your previous feeble "\
    "attempts to \nincrease your proficiency in math!\n" << endl;
    cout << "\nShould your capabilities fail you and you need to quit \n"\
    "during a round of questions, just enter in any negative answer\n" \
    "and you shall be released!\n" << endl;
    cout << "Now quit lollygagging and lets get this show on the road...\n" << endl;
    
    //Initializing and setting choice to 0, while user makes their decision from the menu.
    int choice = 0;

    //This do while loop controls the number of times the program is run
    do{
        //Calls the function display_menu to display options
		choice = display_menu(); 
        
		// This is when choice = 5 from the menu, verifying request to quit
		if (choice == 5){		
                       
			//Ask user if they are sure they would like to quit the program
			char quitter = ' ';
			cout << "\nThe Math Tutor 5000 does not like quitters. But I am feeling " \
			"merciful today. \nAre you sure you would like to stick with your " \
			"currently deficient math \nskills?? Y/N?" << endl;
			cin >> quitter;
			
            // If statement for quitting the program
            if ((quitter == 'y') || (quitter == 'Y')){
                cout << "Fine, then off you go!" << endl;
				choice = 5;
                break;  	 
            }
             
            //This else statement works if the user hits n, allows the user
            //to continue should they change their mind. 
            else{
				choice = display_menu();
            }
		}
		
		//Switch setup for user selection from the menu
		switch (choice){
            case 1:{
                // Ask the number of questions
                double add_questions=1;
    	        cout << "Addition it is! How many problems would you " \
    	        "like? \n";
    	        cin >> add_questions;
    		
                //Quick output advising user to answer with the sum
                cout << "\nSimply type in your guess for the sum when prompted "\
                "with two digits below. \n\n";
                  
                //Counter to run addition questions till reaching # of questions user requested
                int add_counter = 1;
                double add_right=0, add_wrong=0;
                while( add_counter <= add_questions){
                            
                    //Generating random numbers 
                    srand (time(NULL));  
                    int rand_num = 0, rand_num2 = 0;
                    rand_num = rand() % 50 + 1;
                    rand_num2 = rand() % 50 + 1; 
                    
                    //Display the problem
                    int add_answer= 0;
                    cout << rand_num << " + " << rand_num2 << " = ";
                    cin >> add_answer;
                     
                    //Finding out the correct answer
                    int outcome=0;
                    outcome = rand_num + rand_num2;
                     
                    //If statement to count when a user lands a correct answer
                    if (add_answer == outcome){       
                        add_right++;
                    }
                     
                    //If the user enters a negative answer, ask to quit!
                    if (add_answer < 0){
                                    		
                        //Ask user if they are sure they would like to quit the program
     		            char insta_quitter = ' ';
                        cout << "\nThe Math Tutor 5000 does not like quitters. But I am feeling " \
     		            "merciful today. Are you sure you would like to stick with your " \
     		            "currently deficient \nmath skills?? Y/N";
     		            cin >> insta_quitter;
        		         
                        //User verifying they would like to quit 
                        if ((insta_quitter == 'y') || (insta_quitter == 'Y')){
                	
                            cout << "\nMath Tutor 5000 believes you need more work... "\
                            "\nThankfully for you im trapped in this box!! Off you go then! " << endl;
                            choice = 5;
                            break;  
                        }
                          
                        //This else statement works if the user hits n, allows the user
                        //to continue should they change their mind. 
                        else{
                             
                            choice = display_menu();
                        }
                    }
                //While loop run counter          
                add_counter ++; 
                }
            //Display the number of questions that were answered correctly and incorrectly    	
            add_wrong = add_questions - add_right;
            cout << "\nFor this go around you got " << add_right << \
            " question(s) right and " << add_wrong << " question(s) wrong.\n" << endl;
            
            //Each variable below has the users right/wrong questions
            //stored and added to it, to keep count of user's overall questions
            //right, wrong, and percentile score.
            overall_addright += add_right;
            overall_addwrong += add_wrong;
            overall_addquest += add_questions;
            break;
            }
            
            //Subtraction problems 
            case 2:{
                //Values for Subtractions problems
                int sub_counter = 1, sub_answer= 0, sub_outcome=0;
                double sub_questions=1, sub_percentage=0, sub_right=0, sub_wrong=0;
                 
                //Output/input for number of questions to ask user
                cout << "\nSubtraction it is! \n" << "How many problems would you " \
                "like?" << endl;
                cin >> sub_questions;
                
                //Quick output advising user to answer with the difference
                cout << "\nSimply type in your guess for the difference, \nwhen prompted "\
                "with two digits below. \n\n";
                 
                //While loop for subtraction questions
                while( sub_counter <= sub_questions){
                        
                    //Generating random numbers 
                    srand (time(NULL));  
                    int rand_num = 0, rand_num2 = 0;
                    rand_num = 2 + rand() % 50 + 1;
                    rand_num2 = 2 + rand() % 50 + 1;
                    
                    //This if statement will check to see if rand_num2 is greater
                    //than rand_num. This will help avoid a negative answer
                    if(rand_num2 > rand_num){
                        sub_outcome = rand_num2 - rand_num;
                        
                        //If statement making sure the difference is not less than 2
                        if (sub_outcome > 2){
                            rand_num2 = 2 + rand() % 50 + 1;
                        } 
                        cout << rand_num2 << " - " << rand_num << " = ";
                        cin >> sub_answer;
                    }
                    else{
                        sub_outcome = rand_num - rand_num2;
                        cout << rand_num << " - " << rand_num2 << " = ";
                        cin >> sub_answer;
                    }
                 
                    //If statement to count when a user lands a correct answer
                    if (sub_answer == sub_outcome){            
                        sub_right++;
                    }
                     
                    //If the user enters a negative answer, ask to quit!
                    if (sub_answer < 0){
                                    		
                        //Ask user if they are sure they would like to quit the program
                        char insta_quitter = ' ';
                        cout << "\nThe Math Tutor 5000 does not like quitters. But I am feeling " \
                        "merciful today. Are you sure you would like to stick with your " \
                        "currently deficient \nmath skills?? Y/N";
                        cin >> insta_quitter;
    			         
                        //User verifying they would like to quit 
                        if ((insta_quitter == 'y') || (insta_quitter == 'Y')){
                	
                            cout << "\nMath Tutor 5000 believes you need more work... "\
                            "\nThankfully for you im trapped in this box!! Off you go then! " << endl;
                            choice = 5;
                            break;  
                        }
                          
                        //This else statement works if the user hits n, allows the user
                        //to continue should they change their mind. 
                        else{
                             
                            choice = display_menu();
                        }
                    }
                    //While loop run counter          
                    sub_counter ++; 
                }
            //This section displays the users performance for this trip through the loop    
            sub_wrong = sub_questions - sub_right;
            cout << "\nFor this go around you got " << sub_right << \
            " question(s) right and " << sub_wrong << " question(s) wrong.\n" << endl;
                 
            //Each variable below has the users right/wrong questions
            //stored and added to it, to keep count of user's overall questions
            //right, wrong, and percentile score.
            overall_subright += sub_right;
            overall_subwrong += sub_wrong;
            overall_subquest += sub_questions;
            break;     
            }
            
            //MULTIPLICATION PROBLEMS!!
            case 3:{
                //Values for multiplication problems
                int mult_counter = 1, mult_answer= 0;
                double mult_questions=1, mult_percentage=0, mult_right=0, mult_wrong=0;
                 
                //Output/input for number of questions to ask user
                cout << "\nHere we go with some Multiplication problems!\n" << "How " \
                "many problems would you like?" << endl;
                cin >> mult_questions;
                
                //Quick output advising user to answer with the product
                cout << "\nSimply type in your guess for the product, \nwhen prompted "\
                "with two digits below. \n\n";
                 
                //While loop for multiplication questions
                while( mult_counter <= mult_questions){ 
                    
                    //Generating random numbers 
                    srand (time(NULL));  
                    int rand_num = 0, rand_num2 = 0;
                    rand_num = 2 + rand() % 10 + 1;
                    rand_num2 = 2 + rand() % 6; //Keeps ans below 100!
                    
                    //Display current problem
                    cout << rand_num << " * " << rand_num2 << " = ";
                    cin >> mult_answer;
                     
                    //Finding out if the user's answer is correct
                    int mult_outcome=0;
                    mult_outcome = rand_num * rand_num2;
                     
                    //If statement to count when a user lands a correct answer
                    if (mult_answer == mult_outcome){           
                        mult_right++;
                    }
                     
                    //If the user enters a negative answer, ask to quit!
                    if (mult_answer < 0){
                                    		
                        //Ask user if they are sure they would like to quit the program
     		            char insta_quitter = ' ';
                        cout << "\nThe Math Tutor 5000 does not like quitters. But I am feeling " \
     		            "merciful today. Are you sure you would like to stick with your " \
     		            "currently deficient \nmath skills?? Y/N";
     		            cin >> insta_quitter;
        		         
                        //User verifying they would like to quit 
                        if ((insta_quitter == 'y') || (insta_quitter == 'Y')){
                	
                            cout << "\nMath Tutor 5000 believes you need more work... "\
                            "\nThankfully for you im trapped in this box!! Off you go then! " << endl;
                            choice = 5;
                            break;  
        			 
                        }
                          
                        //This else statement works if the user hits n, allows the user
                        //to continue should they change their mind. 
                        else{
                            choice = display_menu();
                        }
                    }
                //Counter for while loop controlling num of questions
                mult_counter++;
                }
            //Displays number of right answers for current trip through mult choice question loop    
            mult_wrong = mult_questions - mult_right;
            cout << "\nFor this go around you got " << mult_right << \
            " question(s) right and " << mult_wrong << " question(s) wrong.\n" << endl;
        
            //Each variable below has the users right/wrong questions
            //stored and added to it, to keep count of user's overall questions
            //right, wrong, and percentile score.
            overall_multright += mult_right;
            overall_multwrong += mult_wrong;
            overall_multquest += mult_questions;
            break;
            }
            case 4:{
                //Values for Subtractions problems
                int div_counter = 1, div_answer= 0;
                double div_questions=1, div_percentage=0, div_right=0, div_wrong=0;
                 
                //Output/input for number of questions to ask user
                cout << "\nHere we go with some Division problems!\n" << "How " \
                "many problems would you like?" << endl;
                cin >> div_questions;
                
                //Quick output advising user to answer with the quotient
                cout << "\nSimply type in your guess for the quotient, \nwhen prompted "\
                "with two digits below. \n\n";
                 
                //While loop for division questions
                while( div_counter <= div_questions){ 
                    
                    //Generating random numbers 
                    srand (time(NULL));  
                    int rand_num = 0, rand_num2 = 0;
                    rand_num = 2* rand() % 40 + 50; //2*rand()%b allows for even numbers only
                    rand_num2 = 2* rand() % 10 + 2; 
                    
                    //This while loop advises to get another number while rand_num and num2 have a remainder
                    while(rand_num % rand_num2 != 0){
                        rand_num2 = 2* rand() % 10 + 2;
                    }
                    
                    //Verify proper answer to problem  
                    int div_outcome = 0;
                    div_outcome = rand_num / rand_num2;
                    
                    //Display division problem to user
                    cout << rand_num << " / " << rand_num2 << " = ";
                    cin >> div_answer;
                    
                    //If statement to count when a user lands a correct answer
                    if (div_answer == div_outcome){       
                        div_right++;
                    }
                     
                    //If the user enters a negative answer, ask to quit!
                    if (div_answer < 0){
                        //Ask user if they are sure they would like to quit the program
     		            char insta_quitter = ' ';
                        cout << "/nThe Math Tutor 5000 does not like quitters. But I am feeling " \
     		            "merciful today. Are you sure you would like to stick with your " \
     		            "currently deficient \nmath skills?? Y/N";
     		            cin >> insta_quitter;
        		         
                        //User verifying they would like to quit 
                        if ((insta_quitter == 'y') || (insta_quitter == 'Y')){
                	
                            cout << "\nMath Tutor 5000 believes you need more work... "\
                            "\nThankfully for you im trapped in this box!! Off you go then! " << endl;
                            choice = 5;
                            break;  
                        }
                          
                        //This else statement works if the user hits n, allows the user
                        //to continue should they change their mind. 
                        else{    
        			         choice = display_menu();
                        }
                    }
                //Counter for while loop controlling division questions
                div_counter++;
                }
                
            //Display the user's current progress through the division loop
            div_wrong = div_questions - div_right;
            cout << "\nFor this go around you got " << div_right << \
            " question(s) right and " << div_wrong << " question(s) wrong.\n" << endl;
            
            //Each variable below has the users right/wrong questions
            //stored and added to it, to keep count of user's overall questions
            //right, wrong, and percentile score.           
            overall_divright += div_right;
            overall_divwrong += div_wrong;
            overall_divquest += div_questions;
            break;
            }
        }
    	
    }while (choice != 5);
    
//Diplaying the user's overall performance through the Math Tutor 5000    
cout << "\nBefore you go, here are your overall marks.\n";
cout << "\nAddition questions correct: " << overall_addright << " Incorrect: " \
<< overall_addwrong << "\n";  
cout << "Subtractions questions correct: " << overall_subright << " Incorrect: " \
<< overall_subwrong << "\n";  
cout << "Multiplication questions correct: " << overall_multright << " Incorrect: " \
<< overall_multwrong << "\n";   
cout << "Division questions correct: " << overall_divright << " Incorrect: " \
<< overall_divwrong << "\n";

double overall_numquestions=0, overal_correct=0, overall_percent=0;
overall_numquestions = overall_addquest + overall_subquest + overall_multquest + overall_divquest;
overal_correct = overall_addright + overall_subright + overall_multright + overall_divright;

//Displays users overalll grade
overall_percent = (overal_correct/overall_numquestions * 100);
cout << "Giving you a score of " << std::fixed << std::setprecision(0) << overall_percent << "%!\n" <<endl;
  
system("pause");
return 0;

}

/*
For this go around you got 2 question(s) right and 1 question(s) wrong.

1. For Addition
2. For Subtraction
3. For Multiplication
4. For Division
5. Quit Program From Menu

Choose an option from the menu above: 1
Addition it is! How many problems would you like?
1

Simply type in your guess for the sum when prompted with two digits below.

16 + 12 = 28

For this go around you got 1 question(s) right and 0 question(s) wrong.

1. For Addition
2. For Subtraction
3. For Multiplication
4. For Division
5. Quit Program From Menu

Choose an option from the menu above: 3

Here we go with some Multiplication problems!
How many problems would you like?
2

Simply type in your guess for the product,
when prompted with two digits below.

10 * 5 = 50
6 * 4 = 24

For this go around you got 2 question(s) right and 0 question(s) wrong.

1. For Addition
2. For Subtraction
3. For Multiplication
4. For Division
5. Quit Program From Menu

Choose an option from the menu above: 4

Here we go with some Division problems!
How many problems would you like?
4

Simply type in your guess for the quotient,
when prompted with two digits below.

74 / 2 = 67
52 / 4 = 13
78 / 6 = 3
66 / 2 = 33

For this go around you got 2 question(s) right and 2 question(s) wrong.

1. For Addition
2. For Subtraction
3. For Multiplication
4. For Division
5. Quit Program From Menu

Choose an option from the menu above: 5

The Math Tutor 5000 does not like quitters. But I am feeling merciful today.
Are you sure you would like to stick with your currently deficient math
skills?? Y/N?
y
Fine, then off you go!

Before you go, here are your overall marks.

Addition questions correct: 3 Incorrect: 1
Subtractions questions correct: 1 Incorrect: 1
Multiplication questions correct: 2 Incorrect: 0
Division questions correct: 2 Incorrect: 2
Giving you a score of 67%!

Press any key to continue . . .


-------------------HERE IS THE USER IMMEDIATELY BREAKING OUT OF THE PROGRAM!!!!


Welcome to the Math Tutor 5000!
I am glad that you are working on your math skills!
The Math Tutor 5000 is much better than your previous feeble attempts to
increase your proficiency in math!


Should your capabilities fail you and you need to quit
during a round of questions, just enter in any negative answer
and you shall be released!

Now quit lollygagging and lets get this show on the road...

1. For Addition
2. For Subtraction
3. For Multiplication
4. For Division
5. Quit Program From Menu

Choose an option from the menu above: 4

Here we go with some Division problems!
How many problems would you like?
2

Simply type in your guess for the quotient,
when prompted with two digits below.

78 / 6 = 4
50 / 2 = 25

For this go around you got 1 question(s) right and 1 question(s) wrong.

1. For Addition
2. For Subtraction
3. For Multiplication
4. For Division
5. Quit Program From Menu

Choose an option from the menu above: 1
Addition it is! How many problems would you like?
45

Simply type in your guess for the sum when prompted with two digits below.

34 + 43 = -2

The Math Tutor 5000 does not like quitters. But I am feeling merciful today. Are
 you sure you would like to stick with your currently deficient
math skills?? Y/Ny

Math Tutor 5000 believes you need more work...
Thankfully for you im trapped in this box!! Off you go then!

For this go around you got 0 question(s) right and 45 question(s) wrong.


Before you go, here are your overall marks.

Addition questions correct: 0 Incorrect: 45
Subtractions questions correct: 0 Incorrect: 0
Multiplication questions correct: 0 Incorrect: 0
Division questions correct: 1 Incorrect: 1
Giving you a score of 2%!

Press any key to continue . . .

*/
