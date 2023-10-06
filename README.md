#include<iostream>
#include<fstream>


using namespace std;

bool LoggingIn()
{
    string user, pass, username, password;

    system("cls");
    cout << "Enter Username: "; cin >> user;
    cout << "Enter Password: "; cin >> pass;

    ifstream read(user + ".txt");
    getline(read, username);
    getline(read, password);

    if (username == user && password == pass){
        system("cls");
        cout << "Login Successful!" << endl;
        cout << "Welcome " << user << "!" << endl;
        return true;



    }else{
        return false;
    }
}

int main()
{
    int choice, choice2;
    string user, pass;

    cout<< "Choose a Number: \n";
    cout<< "1. Register\n";
    cout<< "2. Login\n";
    cout<< "3. Exit\n\n";
    cout<< "Your Choice: "; cin >> choice;

    switch (choice){
        case 1:
            {


            system("cls");
            cout<< "Register\n\n";
            cout<< "Enter a Username: "; cin>> user;
            cout<< "Enter a Password: "; cin>> pass;

            ofstream file;
            file.open(user + ".txt");
            file << user << endl << pass;
            file.close();
            system("cls");
            cout << "Welcome " << user << "!" << endl;
            cout << endl;

            cout << "Choose a number\n";
            cout << "1. Sign out and exit\n";
            cout << "2. Sign out and Back to Main Menu\n\n";

            cout << "Your Choice: "; cin >> choice2;

            switch (choice2){
            case 1:
                {
                    return 0;

                }

            case 2:
                {
                    system("cls");
                    main();
                }

            }


            }
        case 2:
            {
            bool status = LoggingIn();

            if (!status){
                system("cls");
                cout << "Incorrect Information, Try again!" << endl;
                cout << endl;

                return 0;

            }else{
                cout << endl;
                cout << "Choose an option\n";
                cout << "1. Sign out and exit\n";
                cout << "2. Sign out and Back to Main Menu\n\n";

                cout << "Your Choice: "; cin >> choice2;

            switch (choice2){
            case 1:
                {
                    system("cls");
                    cout << "Thank you for using!" << endl;
                    cout << endl;
                    break;

                }

            case 2:
                {
                    system("cls");
                    main();
                }

            }
            }
        }
        case 3:
            {
                system("cls");
                cout << "Thank you for using!";
                cout << endl;
                break;
            }
        default:
            {
            system("cls");
            cout << "Please select a valid option!\n\n";
            main();
            }
    }



    return 0;
}
