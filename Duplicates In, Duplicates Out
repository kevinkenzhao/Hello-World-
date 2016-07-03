#include <iostream>
#include <vector>
#include <string>
#include <fstream>
#include <algorithm>
#include <iterator>
using namespace std;
class Name{
      public:
      Name(){}
      Name(string first, string middle, string last){ 
           firstname = first;
           middlename = middle;
           lastname = last;
      }
      string getFirst(){
           return firstname;
      }
      string getMiddle(){
           return middlename;
      }
      string getLast(){
           return lastname;
      }
      void printFullName(){
           cout << firstname << " " << middlename << " " << lastname << endl;
      }
      
      private:
      string firstname, middlename, lastname;
      };
void eraseSpaces(string& name);
void erasePunct(string& name);
void makeLower(string& name);
bool isNotN(char letter);
struct to_lower{
   int operator() (int ch)
      {
          return tolower (ch);
      }
};

int main()
{
    ofstream myfile;
    myfile.open("listofnames.txt"); //creates text file
    
    Name names;
    string firstname, middlename, lastname;
    char choice;
    vector<Name> listOfNames;
    do{
           cout << "Enter a first name: " << endl;
           cin >> firstname;
           eraseSpaces(firstname);
           erasePunct(firstname);
           makeLower(firstname);
           cout << "First name: " << firstname << endl; //echoes first name after removing spaces and punctuation, and making capital letters
                                                        //lowercase
           cout << "Enter a middle name: " << endl;
           cin >> middlename;
           eraseSpaces(middlename);
           erasePunct(middlename);
           makeLower(middlename);
           cout << "Middle name: " << middlename << endl; //echoes middle name
           
           cout << "Enter a last name: " << endl;
           cin >> lastname;           
           eraseSpaces(lastname);
           erasePunct(lastname);
           makeLower(lastname);
           cout << "Last name: " << lastname << endl; //echoes last name
           
           myfile << firstname << " " << middlename << " " << lastname << "\n";
           
           Name fullname(firstname, middlename, lastname);
           listOfNames.push_back(fullname);
           fullname.printFullName();
           cout << "Do you want to enter a new name?(y/n)" << endl;
           cin.clear(); //clears error flags
           cin >> choice;
           cin.ignore(256, '\n');
      }while(isNotN(choice));

      for(int j = 0; j < listOfNames.size()-1; ){
          for (int i = 1; i < listOfNames.size(); i++){
              if((listOfNames[j].getFirst() == listOfNames[i].getFirst()) && (listOfNames[j].getLast() == listOfNames[i].getLast())) 
              {
                   if(i == listOfNames.size()-1){
                        j++;
                   }
                   listOfNames.erase(listOfNames.begin() + i); //deletes duplicate          
              }
          }
      }
      
      cout << "The following is a list of names you have entered with duplicates removed: " << endl;
      for(int k = 0; k < listOfNames.size(); k++) //prints vector with duplicates removed
          {
                listOfNames[k].printFullName();
          }
      
      myfile.close();

return 0;
}
//function definitions
void eraseSpaces(string& name)//erases all spaces from a given string
{
    name.erase(remove (name.begin(), name.end(), ' '), name.end());
}

void erasePunct(string& name)//erases all punctuation from a given string
{
    for (int i = 0, len = name.size(); i < len; i++)
    {
        if (ispunct(name[i]))
        {
            name.erase(i--, 1);
            len = name.size();
        }
    }
}
void makeLower(string& name)//make all characters of a given string lowercase
{
    transform(name.begin(), name.end(), name.begin(), to_lower());
}

bool isNotN(char letter)
{
     if(letter != 'n' && letter != 'N')
     {
         return true;
     }
     return false;
}
