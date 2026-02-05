#include <iostream>
#include <vector>
#include <string>
using namespace std;

// --- 1. THE BOOK ---
struct Book {
    string title;
    book available = true;
};

// --- 2. THE USER ---
struct User {
    string name;
};

// --- 3. THE LIBRARY (The Logic) ---
class Library {
public:
    vector<Book> books;
 void addBook(string t) 
 {
        books.push_back({t, true});
        cout << "Added: " << t << endl;
    }
  void borrowBook(string t) 
  {
        for (auto &b : books) {
            if (b.title == t) {
                if (b.available) {
                    b.available = false;
                    cout << "Success: You borrowed " << t << endl;
                }
                else {
                    cout << "Error: " << t << " is already out." << endl;
                }
                return;
            }
        }
        cout << "Error: Book not found." << endl;
    }
};

// --- 4. THE TEST (How you run it) ---
int main() {
    Library myLib;

  // Add books
    myLib.addBook("C++ Guide");
    
  // Test 1: Borrowing (Positive)
    myLib.borrowBook("C++ Guide");

   // Test 2: Borrowing same book (Negative/Failure)
    myLib.borrowBook("C++ Guide");

  return 0;
}
