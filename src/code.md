```cpp
#include<iostream>
#include<cstdlib>
#include <ctime>
using namespace std;

string a[3][3] = {{" ", " ", " "}, {" ", " ", " "}, {" ", " ", " "}};

// variable for 1 1

int Ocount = 0, spaceCount = 0, Xcount = 0,flag=0,flagToGame1=0,flagOfLastCase=0,flagTo1stGame=0,secondI=0,secondJ=0;

// variable for ODD case

int firstI=0,firstJ=0,gameIn3RdCase=0;

//variable for Even case

int defendCount=0,variableForReplaceX=0;


long int random(){
     srand(time(0));

    int variableForLimit =rand()%100, finalRandomNumber=0;

           for (int i = 0; i < variableForLimit; i++)
            {

                int randomNumber=(rand()%(100-30+1)+30);
                  if(i==variableForLimit/2)
                    {
                        finalRandomNumber=randomNumber;
                    }
            }

       return  finalRandomNumber;
  }

bool isEven(int i, int j) {
    if ((i == 1 && j == 1) || (i == 0 && j == 1) || (i == 2 && j == 1) || (i == 1 && j == 0) || (i == 1 && j == 2))
        return true;
    else
        return false;
}

int isMainDiagonalOne(){
    spaceCount = 0;
    Xcount = 0;  // Ensure Xcount is reset
    for (int i = 0; i < 3; i++) {

        if (a[i][i] == " ") {
            spaceCount++;
        }
        if (a[i][i] == "X") {
            Xcount++;
        }
    }
    if (Xcount == 1 && spaceCount == 2) {
        for (int i = 0; i < 3; i++) {
            if (a[i][i] == " ") {
                a[i][i] = "X";
                flag=1;
                flagToGame1=1;

                return 0;
                break;  // Add return after placing 'X'
            }

        }
    }
    return 0;
}

int isAntiDiagonalOne(){
    spaceCount = 0;
    Xcount = 0;  // Ensure Xcount is reset
    for (int i = 0; i < 3; i++) {

        if (a[i][2 - i] == " ") {
            spaceCount++;
        }
        if (a[i][2 - i] == "X") {
            Xcount++;
        }
    }
    if (Xcount == 1 && spaceCount == 2) {
        for (int i = 0; i < 3; i++) {
            if (a[i][2 - i] == " ") {
                a[i][2 - i] = "X";
                flag=1;
                flagToGame1=1;
                return 0;
                 break; // Add return after placing 'X'
            }
        }
    }
    return 0;
}

int isRowDefend() {
    // row
    for (int i = 0; i < 3; i++) {
        Ocount = 0;
        spaceCount = 0;
        Xcount = 0;  // Ensure Xcount is reset
        for (int j = 0; j < 3; j++) {
            if (a[i][j] == "O") {
                Ocount++;
            }
            if (a[i][j] == " ") {
                spaceCount++;
            }

        }

        if (Ocount == 2 && spaceCount == 1) {
            for (int j = 0; j < 3; j++) {
                if (a[i][j] == " ") {
                    if(variableForReplaceX==0)
                    {
                        a[i][j] = "X";
                        secondI=i,secondJ=j;
                    }
                    flagOfLastCase=1;
                    defendCount++;
                    return 0;  // Add return after placing 'X'
                }
            }
        }
    }
    return 0;
}

int isRowGame() {
    // row
    for (int i = 0; i < 3; i++) {
        Ocount = 0;
        spaceCount = 0;
        Xcount = 0;  // Ensure Xcount is reset
        for (int j = 0; j < 3; j++) {

            if (a[i][j] == " ") {
                spaceCount++;
            }
            if (a[i][j] == "X") {
                Xcount++;
            }
        }
        if (Xcount == 2 && spaceCount == 1) {
            for (int j = 0; j < 3; j++) {
                if (a[i][j] == " ") {
                    a[i][j] = "X";
                    flag=1;
                    flagToGame1=1;
                    return 0;  // Add return after placing 'X'
                }
            }
        }

        }
        return 0;
        }

int isColumnDefend() {
    // column
    for (int i = 0; i < 3; i++) {
        Ocount = 0;
        spaceCount = 0;
        Xcount = 0;  // Ensure Xcount is reset
        for (int j = 0; j < 3; j++) {
            if (a[j][i] == "O") {
                Ocount++;
            }
            if (a[j][i] == " ") {
                spaceCount++;
            }

        }

         if (Ocount == 2 && spaceCount == 1) {
            for (int j = 0; j < 3; j++) {
                if (a[j][i] == " ") {
                   if(variableForReplaceX==0)
                    {
                        a[j][i] = "X";
                        secondI=j,secondJ=i;
                    }
                    flagOfLastCase=1;
                    defendCount++;
                    return 0;  // Add return after placing 'X'
                }
            }
        }
    }
    return 0;
}

int isColumnGame() {
    // column
    for (int i = 0; i < 3; i++) {
        Ocount = 0;
        spaceCount = 0;
        Xcount = 0;  // Ensure Xcount is reset
        for (int j = 0; j < 3; j++) {

            if (a[j][i] == " ") {
                spaceCount++;
            }
            if (a[j][i] == "X") {
                Xcount++;
            }
        }
        if (Xcount == 2 && spaceCount == 1) {
            for (int j = 0; j < 3; j++) {
                if (a[j][i] == " ") {
                    a[j][i] = "X";
                    flag=1;
                    flagToGame1=1;
                    return 0;  // Add return after placing 'X'
                }
            }
        }}
        return 0;}

int isMainDiagonalDefend(){
    Ocount = 0;
    spaceCount = 0;
    Xcount = 0;  // Ensure Xcount is reset
    for (int i = 0; i < 3; i++) {
        if (a[i][i] == "O") {
            Ocount++;
        }
        if (a[i][i] == " ") {
            spaceCount++;
        }

    }

    if (Ocount == 2 && spaceCount == 1) {
        for (int i = 0; i < 3; i++) {
            if (a[i][i] == " ") {
                if(variableForReplaceX==0)
                    {
                        a[i][i] = "X";
                    }
                flagOfLastCase=1;
                defendCount++;
                return 0;  // Add return after placing 'X'
            }
        }
    }
    return 0;
}

int isMainDiagonalGame() {
    Ocount = 0;
    spaceCount = 0;
    Xcount = 0;  // Ensure Xcount is reset
    for (int i = 0; i < 3; i++) {

        if (a[i][i] == " ") {
            spaceCount++;
        }
        if (a[i][i] == "X") {
            Xcount++;
        }
    }
    if (Xcount == 2 && spaceCount == 1) {
        for (int i = 0; i < 3; i++) {
            if (a[i][i] == " ") {
                a[i][i] = "X";
                flag=1;
                flagToGame1=1;
                return 0;  // Add return after placing 'X'
            }
        }
    }
    return 0;
    }

int isAntiDiagonalDefend() {
    Ocount = 0;
    spaceCount = 0;
    Xcount = 0;  // Ensure Xcount is reset
    for (int i = 0; i < 3; i++) {
        if (a[i][2 - i] == "O") {
            Ocount++;
        }
        if (a[i][2 - i] == " ") {
            spaceCount++;
        }

    }

    if (Ocount == 2 && spaceCount == 1) {
        for (int i = 0; i < 3; i++) {
            if (a[i][2 - i] == " ") {
                if(variableForReplaceX==0)
                    {
                        a[i][2 - i] = "X";
                    }
                flagOfLastCase=1;
                defendCount++;
                return 0;  // Add return after placing 'X'
            }
        }
    }
    return 0;
}

int isAntiDiagonalGame() {
    Ocount = 0;
    spaceCount = 0;
    Xcount = 0;  // Ensure Xcount is reset
    for (int i = 0; i < 3; i++) {

        if (a[i][2 - i] == " ") {
            spaceCount++;
        }
        if (a[i][2 - i] == "X") {
            Xcount++;
        }
    }
    if (Xcount == 2 && spaceCount == 1) {
        for (int i = 0; i < 3; i++) {
            if (a[i][2 - i] == " ") {
                a[i][2 - i] = "X";
                flag=1;
                flagToGame1=1;
                return 0;  // Add return after placing 'X'
            }
        }
    }
    return 0;
    }

void print() {
//    cout << "\t\t\t\t\t\t __________________________" << endl;
//    cout << "\t\t\t\t\t\t|        |        |        |" << endl;
//    cout << "\t\t\t\t\t\t|        |        |        |" << endl;
//    cout << "\t\t\t\t\t\t|    " << a[0][0] << "   |    " << a[0][1] << "   |   " << a[0][2] << "    |" << endl;
//    cout << "\t\t\t\t\t\t|        |        |        |" << endl;
//    cout << "\t\t\t\t\t\t|________|________|________|" << endl;
//    cout << "\t\t\t\t\t\t|        |        |        |" << endl;
//    cout << "\t\t\t\t\t\t|        |        |        |" << endl;
//    cout << "\t\t\t\t\t\t|    " << a[1][0] << "   |    " << a[1][1] << "   |   " << a[1][2] << "    |" << endl;
//    cout << "\t\t\t\t\t\t|        |        |        |" << endl;
//    cout << "\t\t\t\t\t\t|________|________|________|" << endl;
//    cout << "\t\t\t\t\t\t|        |        |        |" << endl;
//    cout << "\t\t\t\t\t\t|        |        |        |" << endl;
//    cout << "\t\t\t\t\t\t|    " << a[2][0] << "   |    " << a[2][1] << "   |   " << a[2][2] << "    |" << endl;
//    cout << "\t\t\t\t\t\t|        |        |        |" << endl;
//    cout << "\t\t\t\t\t\t|________|________|________|" << endl;
//
        cout << "\t\t\t\t\t\t __________________________" <<"\t __________________________" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|    " << a[0][0] << "   |    " << a[0][1] << "   |   " << a[0][2] << "    |" <<"\t|  " << " 0 0 "<< " |  " <<" 0 1 "<< " |  " <<" 0 2 "<< " |" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|________|________|________|" <<"\t|________|________|________|" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|    " << a[1][0] << "   |    " << a[1][1] << "   |   " << a[1][2] << "    |" << "\t|  " << " 1 0"<< "  |  " <<" 1 1"<< "  |  " <<" 1 2"<< "  |"<<  endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|________|________|________|" <<"\t|________|________|________|" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|    " << a[2][0] << "   |    " << a[2][1] << "   |   " << a[2][2] << "    |" <<"\t|  " << " 2 0"<< "  |  " <<" 2 1"<< "  |  " <<" 2 2"<< "  |"<< endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|________|________|________|" <<"\t|________|________|________|" << endl;

}

int main() {


    cout << "\t\t\t\t\t\t __________________________" <<"\t __________________________" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|    " << a[0][0] << "   |    " << a[0][1] << "   |   " << a[0][2] << "    |" <<"\t|  " << " 0 0 "<< " |  " <<" 0 1 "<< " |  " <<" 0 2 "<< " |" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|________|________|________|" <<"\t|________|________|________|" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|    " << a[1][0] << "   |    " << a[1][1] << "   |   " << a[1][2] << "    |" << "\t|  " << " 1 0"<< "  |  " <<" 1 1"<< "  |  " <<" 1 2"<< "  |"<<  endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|________|________|________|" <<"\t|________|________|________|" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|    " << a[2][0] << "   |    " << a[2][1] << "   |   " << a[2][2] << "    |" <<"\t|  " << " 2 0"<< "  |  " <<" 2 1"<< "  |  " <<" 2 2"<< "  |"<< endl;
    cout << "\t\t\t\t\t\t|        |        |        |" <<"\t|        |        |        |" << endl;
    cout << "\t\t\t\t\t\t|________|________|________|" <<"\t|________|________|________|" << endl;


   // 1st move

    cout << " \a Enter your 1st move (row and column):\t"  ;
    int i, j;
    cin >> i >> j;
    firstI=i,firstJ=j;
    a[i][j] = "O";
    print();

    // if 1 1  (center)

    if ((i == 1 && j == 1) && (isEven(i, j))) {

       if(random()%3==0)
       {
            a[2][2] = "X";
       }
       else if(random()%3==1)
       {
            a[2][0] = "X";
       }
       else if(random()%3==2)
       {
            a[0][2] = "X";
       }
       else if(random()%3==3)
       {
            a[0][0] = "X";
       }

// clear the screen and buffer

       system("cls");
       fflush(stdout);

        print();

        //  2nd move

   cout << " \a Enter your 2nd move (row and column):\t"  ;
        cin >> i >> j;

        a[i][j] = "O";
// clear the screen and buffer

       system("cls");
       fflush(stdout);

        print();

          variableForReplaceX=0;
             flagOfLastCase=0;
             secondI=0,secondJ=0;
        isRowDefend();if(flagOfLastCase==0) isColumnDefend();if(flagOfLastCase==0) isMainDiagonalDefend(); if(flagOfLastCase==0) isAntiDiagonalDefend();


           if(flagOfLastCase==0)
           {
               for (int i = 0; i < 3; i+=2)
               {
                 if (a[i][i] == " " )
                  {
                      a[i][i] = "X";
                      break;
                  }
               }
               for (int i = 0; i < 3; i+=2)
               {
                 if (a[i][2 - i] == " ")
                  {
                      a[i][2 - i] =  "X";
                      break;
                  }

               }

           }

 // clear the screen and buffer

       system("cls");
       fflush(stdout);

            print();


        //  3rd move

        cout << "\a Enter your 3rd move (row and column):\t" ;
        cin >> i >> j;
        a[i][j] = "O";
// clear the screen and buffer

       system("cls");
       fflush(stdout);

        print();

        flagToGame1==0;
        isRowGame(); if(flagToGame1==0) isColumnGame();if(flagToGame1==1) isMainDiagonalGame();if(flagToGame1==1) isAntiDiagonalGame();
        if(flag==1){
// clear the screen and buffer

       system("cls");
       fflush(stdout);

        print();
        flagTo1stGame=1;
        cout << "\n\n\t\t\t\t\t\t\a   Logic (X) Wins The Game\n\n" << endl;

        }
        else{

        variableForReplaceX=0;
        flagOfLastCase=0;

        isRowDefend();if(flagOfLastCase==0) isColumnDefend();if(flagOfLastCase==0) isMainDiagonalDefend(); if(flagOfLastCase==0) isAntiDiagonalDefend();

        if(flagOfLastCase==0)
        {

            if(i==secondI)
            {
                for(int k=0 ;k<3 ; k++)
                {
                    if(a[i][k]==" ")
                    {
                        a[i][k]= "X";
                    }
                }
            }
            else if(j==secondJ)
            {
                for(int k=0 ;k<3 ; k++)
                {
                    if(a[k][j]==" ")
                    {
                        a[k][j]= "X";
                    }
                }
            }
        }
// clear the screen and buffer

       system("cls");
       fflush(stdout);

         print();
        }


        if(flagTo1stGame==0){

        //  4th move

        cout << " \a Enter your 4th move (row and column):\t" ;
        cin >> i >> j;
        a[i][j] = "O";
// clear the screen and buffer

       system("cls");
       fflush(stdout);

        print();

        isRowGame(); if(flagToGame1==0) isColumnGame();if(flagToGame1==1) isMainDiagonalGame();if(flagToGame1==1) isAntiDiagonalGame();
        if (flag==1){
// clear the screen and buffer

       system("cls");
       fflush(stdout);

        print();
        cout << "\n\n\t\t\t\t\t\t \a  Logic (X) Wins The Game\n\n" << endl;
        }
        else{

        if(flag==0){

       variableForReplaceX=0;
        flagOfLastCase=0;

        isRowDefend();if(flagOfLastCase==0) isColumnDefend();if(flagOfLastCase==0) isMainDiagonalDefend(); if(flagOfLastCase==0) isAntiDiagonalDefend();

         if(flagOfLastCase==1){
// clear the screen and buffer

       system("cls");
       fflush(stdout);

          print();

        cout << "\n\n\t\t\t\t\t\t\a   Game Over\tMatch Draw" << endl;
        }
        }
        if(flag==0 && flagOfLastCase==0) {

        for (int i = 0; i < 3; i++) {
        int inerFlag=0;
        for (int j = 0; j < 3; j++) {
            if (a[i][j] == " ") {
            a[i][j]="X";
            inerFlag=1;
            break;
            }
            }
            if(inerFlag==1){
            break;}
            }
// clear the screen and buffer

       system("cls");
       fflush(stdout);

            print();
             cout << "\n\n\t\t\t\t\t\t \a  Game Over\tMatch Draw\n\n" << endl;
            }
         }
        }
        }

    // if ODD

 else if ((i !=1 && j != 1) && (!isEven(i, j)))
      {
           a[1][1]="X";

// clear the screen and buffer

       system("cls");
       fflush(stdout);

        print();


    // 2nd move for ODD case

      cout << "\a Enter your 2nd move (row and column):\t";
    cin >> i >> j;
    int inputI=i,inputJ=j;
    a[i][j] = "O";

// clear the screen and buffer

       system("cls");
       fflush(stdout);

    print();

flagOfLastCase=0;
isRowDefend(); isColumnDefend(); isMainDiagonalDefend();  isAntiDiagonalDefend();

        if(flagOfLastCase==0 && (firstI+firstJ+i+j)==4)
        {
            if(random()%4==0)
            {
                a[0][1]="X";
            }
             if(random()%4==1)
            {
                a[1][0]="X";
            }
             if(random()%4==2)
            {
                a[2][1]="X";
            }
             if(random()%4==3)
            {
                a[1][2]="X";
            }
        }
        else if(flagOfLastCase==0)
        {
            spaceCount = 0;
            Xcount = 0;

    for (int i = 0; i < 3; i++) {

        if (a[i][i] == " ") {
            spaceCount++;
        }
        if (a[i][i] == "X") {
            Xcount++;
        }
    }
    if (Xcount == 1 && spaceCount == 2) {
        for (int i = 0; i < 3; i++) {
            if (a[i][i] == " " && (inputI==i || inputJ==i)) {
                a[i][i] = "X";
            }
        }
    }

     spaceCount = 0;
    Xcount = 0;

     for (int i = 0; i < 3; i++) {

        if (a[i][2 - i] == " ") {
            spaceCount++;
        }
        if (a[i][2 - i] == "X") {
            Xcount++;
        }
    }
    if (Xcount == 1 && spaceCount == 2) {
        for (int i = 0; i < 3; i++) {
            if (a[i][2 - i] == " " && (inputI==i || inputJ==i)) {
                a[i][2 - i] = "X";
            }
        }
    }
}
// clear the screen and buffer

       system("cls");
       fflush(stdout);

            print();


    // 3rd move for ODD case

      cout << " \a Enter your 3rd move (row and column):\t" ;
    cin >> i >> j;
    a[i][j] = "O";

// clear the screen and buffer

       system("cls");
       fflush(stdout);

    print();

    flagToGame1=0;
    flag=0;
             isRowGame(); if(flagToGame1==0) isColumnGame();if(flagToGame1==0) isMainDiagonalGame();if(flagToGame1==0) isAntiDiagonalGame();

    if(flag==1){
// clear the screen and buffer

       system("cls");
       fflush(stdout);

        print();
        gameIn3RdCase=1;
        cout << "\n\n\t\t\t\t\t\t \a  Logic (X) Wins The Game\n\n" << endl;
            }
            if(gameIn3RdCase==0){

             flagOfLastCase=0;
        isRowDefend();if(flagOfLastCase==0) isColumnDefend();if(flagOfLastCase==0) isMainDiagonalDefend(); if(flagOfLastCase==0) isAntiDiagonalDefend();

    if(flagOfLastCase==0)
    {
          for (int i = 0; i < 3; i++) {
        int inerFlag=0;
        for (int j = 0; j < 3; j++) {
            if (a[i][j] == " " && isEven(i,j)) {
            a[i][j]="X";
            inerFlag=1;
            break;
            }
            }
            if(inerFlag==1){
            break;}
            }
    }
// clear the screen and buffer

       system("cls");
       fflush(stdout);

    print();

   // 4th move for ODD case

        cout << " \a Enter your 4th move (row and column):\t " ;
    cin >> i >> j;
    a[i][j] = "O";
// clear the screen and buffer

       system("cls");
       fflush(stdout);

    print();


    flagToGame1=0;
    flag=0;
             isRowGame(); if(flagToGame1==0) isColumnGame();if(flagToGame1==0) isMainDiagonalGame();if(flagToGame1==0) isAntiDiagonalGame();

    if(flag==1){
// clear the screen and buffer

       system("cls");
       fflush(stdout);

        print();

        gameIn3RdCase=1;
        cout << "\n\n\t\t\t\t\t\t \a  Logic (X) Wins The Game\n\n" << endl;
            }

        if(gameIn3RdCase==0)
        {

         flagOfLastCase=0;
        isRowDefend();if(flagOfLastCase==0) isColumnDefend();if(flagOfLastCase==0) isMainDiagonalDefend(); if(flagOfLastCase==0) isAntiDiagonalDefend();

        if(flagOfLastCase==0)
        {
            for(int i=0;i<3;i++)
            {
                int inerFlag2=0;
                for(int j=0;j<3;j++)
                {
                    if(a[i][j]==" ")
                    {
                        a[i][j]="X";
                        inerFlag2=1;
                        break;
                    }
                }
                if(inerFlag2==1)
                {
                    break;
                }
            }
        }
// clear the screen and buffer

       system("cls");
       fflush(stdout);

         print();
        cout << "\n\n\t\t\t\t\t\t  \a Game Over\tMatch Draw" << endl;

        }
    }
    }

    // if Eeven

    else if( isEven(i, j))
    {
        a[1][1]="X";
// clear the screen and buffer

       system("cls");
       fflush(stdout);

          print();
 firstI=0,firstJ=0;

      // 2nd move of Even Case

    cout << " \a Enter your 2nd move (row and column):\t" ;
    cin >> i >> j;
    firstI=i,firstJ=j;
    a[i][j] = "O";
    // clear the screen and buffer

       system("cls");
       fflush(stdout);

    print();

        variableForReplaceX=0;
     isRowDefend();if(flagOfLastCase==0) isColumnDefend();if(flagOfLastCase==0) isMainDiagonalDefend(); if(flagOfLastCase==0) isAntiDiagonalDefend();

   if(flagOfLastCase==0 && isEven(i,j))
   {
        int inerVariable=0,inerVariable2=0;
         for (int i = 0; i < 3; i+=2)
        {
        a[i][i]="O";

        variableForReplaceX=1;

        isRowDefend(); isColumnDefend(); isMainDiagonalDefend();  isAntiDiagonalDefend();

        if(i==0 && defendCount==2 )
        {
            a[i+2][i]="X";
            a[i][i]=" ";
            inerVariable=1;
        }
        else if(i==2 && defendCount==2)
        {
            a[i-2][i]="X";
             a[i][i]=" ";
             inerVariable=1;
        }
        variableForReplaceX=0;
        a[i][i]=" ";
        defendCount=0;

        }

        if(inerVariable==0)
        {
         for (int i = 0; i < 3; i+=2)
        {
            a[i][2 - i] ="O";

          variableForReplaceX=1;

        isRowDefend(); isColumnDefend(); isMainDiagonalDefend();  isAntiDiagonalDefend();

        if(i==0 && defendCount==2 )
        {
            a[i+2][2-i]="X";
            a[i][2-i]=" ";
            inerVariable2=1;
        }
        else if(i==2 && defendCount==2)
        {
            a[i-2][2-i]="X";
             a[i][2-i]=" ";
             inerVariable2=1;
        }

        defendCount=0;
        variableForReplaceX=0;
        a[i][2 - i] =" ";
        }}


      if(inerVariable2==0 && inerVariable==0)
      {
          if(random()%3==0)
       {
           a[0][0]="X";
       }
       if(random()%3==1)
       {
           a[0][2]="X";
       }
       if(random()%3==2)
       {
           a[2][0]="X";
       }
       if(random()%3==3)
       {
           a[2][2]="X";
       }
      }

   }

   else if(flagOfLastCase==0 && !isEven(i,j))
   {
       int inerVariable=0;
       if(!(firstI==0 && firstJ==0) && !(firstI==2 && firstJ==2))
       {


         for (int i = 0; i < 3; i+=2)
        {
        a[i][i]="O";

        variableForReplaceX=1;
defendCount=0;
        isRowDefend(); isColumnDefend(); isMainDiagonalDefend();  isAntiDiagonalDefend();

        if( defendCount==2 )
        {
            a[i][i]="X";
            inerVariable=1;
            break;
        }
        variableForReplaceX=0;
        a[i][i]=" ";
        }
       }
        else if(!(firstI==0 && firstJ==2) && !(firstI==2 && firstJ==0))
       {
        if(inerVariable==0)
        {
        variableForReplaceX=0;
        defendCount=0;
         for (int i = 0; i < 3; i+=2)
        {
            a[i][2 - i] ="O";

          variableForReplaceX=1;

        isRowDefend(); isColumnDefend(); isMainDiagonalDefend();  isAntiDiagonalDefend();

        if( defendCount==2 )
        {
            a[i][2 - i] ="X";
            break;
        }
        defendCount=0;
        variableForReplaceX=0;
        a[i][2 - i] =" ";
        }}}

   }
   // clear the screen and buffer

       system("cls");
       fflush(stdout);

 print();

     // 3rd move of Even Case

     cout << " \a Enter your 3rd move (row and column):\t" ;
    cin >> i >> j;
    firstI=i,firstJ=j;
    a[i][j] = "O";
// clear the screen and buffer

       system("cls");
       fflush(stdout);

    print();

    gameIn3RdCase=0;
    flagToGame1=0;
    flag=0;
             isRowGame(); if(flagToGame1==0) isColumnGame();if(flagToGame1==0) isMainDiagonalGame();if(flagToGame1==0) isAntiDiagonalGame();

            if(flag==1){
// clear the screen and buffer

       system("cls");
       fflush(stdout);

        print();
        gameIn3RdCase=1;
        cout << "\n\n\t\t\t\t\t\t \a  Logic (X) Wins The Game\n\n" << endl;
            }
            if(gameIn3RdCase==0)
            {
                variableForReplaceX=0;
             flagOfLastCase=0;
        isRowDefend();if(flagOfLastCase==0) isColumnDefend();if(flagOfLastCase==0) isMainDiagonalDefend(); if(flagOfLastCase==0) isAntiDiagonalDefend();
// clear the screen and buffer

       system("cls");
       fflush(stdout);

            print();

            // 4th move for ODD case

        cout << "\a Enter your 4th move (row and column):\t " ;
    cin >> i >> j;
    a[i][j] = "O";
// clear the screen and buffer

       system("cls");
       fflush(stdout);

    print();

    gameIn3RdCase=0;
    flagToGame1=0;
    flag=0;
             isRowGame(); if(flagToGame1==0) isColumnGame();if(flagToGame1==0) isMainDiagonalGame();if(flagToGame1==0) isAntiDiagonalGame();

        if(flag==1){
// clear the screen and buffer

       system("cls");
       fflush(stdout);

        print();
        gameIn3RdCase=1;
        cout << "\n\n\t\t\t\t\t\t \a  Logic (X) Wins The Game\n\n" << endl;
            }
            if(gameIn3RdCase==0)
            {
             variableForReplaceX=0;
             flagOfLastCase=0;

        isRowDefend();if(flagOfLastCase==0) isColumnDefend();if(flagOfLastCase==0) isMainDiagonalDefend(); if(flagOfLastCase==0) isAntiDiagonalDefend();


         if(flagOfLastCase==0)
        {
            for(int i=0;i<3;i++)
            {
                int inerFlag3=0;
                for(int j=0;j<3;j++)
                {
                    if(a[i][j]==" ")
                    {
                        a[i][j]="X";
                        inerFlag3=1;
                        break;
                    }
                }
                if(inerFlag3==1)
                {
                    break;
                }
            }
        }
// clear the screen and buffer

       system("cls");
       fflush(stdout);

             print();
        cout << "\n\n\t\t\t\t\t\t\a   Game Over\tMatch Draw" << endl;
            }
            }
    }
    return 0;
}
```
