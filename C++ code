#include <iostream>
#include <string>
#include <cctype>
using namespace std;

string encryptMessage(const string& message, const string& key) 
{
  string encryptedMessage = "";
     int keyLength = key.length();

  for (int i = 0; i < message.length(); i++)
    {
      char currentChar = toupper(message[i]);
      char keyChar = toupper(key[i % keyLength]);

      if (isalpha(currentChar))
      {
        char base = 'A';
        char encryptedChar = ((currentChar - base) + (keyChar - base)) % 26 + base;
        encryptedMessage += encryptedChar;
      }
    }
  return encryptedMessage;
}

string decryptMessage(const string& encryptedMessage, const string& key)
{
  string decryptedMessage = "";
  int keyLength = key.length();

  for (int i = 0; i < encryptedMessage.length(); i++)
    {
      char currentChar = toupper(encryptedMessage[i]);
      char keyChar = toupper(key[i % keyLength]);

      if (isalpha(currentChar))
      {
        char base = 'A';
        char decryptedChar = ((currentChar - base) - (keyChar - base) + 26) % 26 + base;
        decryptedMessage += decryptedChar;
      }
    }
  return decryptedMessage;
}

int getMenuChoice() 
{
  int choice;

  cout << "\nChoose an option:\n"
       << "1. Encrypt message\n"
       << "2. Decrypt message\n"
       << "3. Exit\n"
       << "Enter your choice (1, 2, or 3): ";
  cin  >> choice;

  while (choice != 1 && choice != 2 && choice != 3)
    {
      cout << "Invalid choice! Please enter 1, 2, or 3: ";
      cin  >> choice;
    }
  return choice;      
}

bool getTryAgainChoice()
{
  char tryAgainChoice;
  cout << "\nDo you want to try again? (Y/N): ";
  cin  >> tryAgainChoice;

  while (tolower(tryAgainChoice) != 'y' && tolower(tryAgainChoice) != 'n')
    {
      cout << "Invalid choice! Please enter Y or N: ";
      cin  >> tryAgainChoice;
    }
  return (tolower(tryAgainChoice) == 'y');
}

bool validateMessage(const string& message)
{
  for (char c : message)
    {
      if (!isalpha(c))
        return false;
    }
  return true;
}

bool validateKey(const string& key, const string& message)
{
  return key.length() <= message.length();
}

int main() 
{
  cout << "*** Vigenere Cipher ***\n";

  bool tryAgain = true;

  while (tryAgain)
    {
      int choice = getMenuChoice();

      if (choice == 3)
      {
        cout << "Program exited. Goodbye!" << endl;
        return 0;
      }

      cin.ignore();

      string message;
      string key;

      cout << "Enter the message: ";
      getline(cin, message);

      while (!validateMessage(message))
        {
          cout << "Invalid Message! Please enter letters only: ";
          getline(cin, message);
        }

      cout << "Enter the key: ";
      getline(cin, key);

      while (!validateKey(key, message))
        {
          cout << "Invalid key! Key length can't exceed message length. Enter the key: ";
          getline(cin, key);
        }

      string result;

      if (choice == 1) 
        result = encryptMessage(message, key);
      else if (choice == 2)
        result = decryptMessage(message, key);

      cout << "Result: " << result << endl;

      tryAgain = getTryAgainChoice();
      cout << endl;
    }
  return 0;
}
