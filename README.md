# program-for-library-management-system
To develop a Library Management System that efficiently manages books, members, and borrowing records using structured or object-oriented programming.

#include <iostream>
using namespace std;

struct Book {
    int id;
    string title, author;
    bool issued = false;
};

int main() {
    Book b[10];
    int n = 0, choice, id;
    string s;

    do {
        cout << "\n--- Library Management System ---\n";
        cout << "1.Add  2.Issue  3.Return  4.Search  5.Exit\n";
        cin >> choice;

        if (choice == 1) {
            cout << "ID Title Author: ";
            cin >> b[n].id >> b[n].title >> b[n].author;
            n++;
            cout << "Book Added\n";
        }

        else if (choice == 2 || choice == 3) {
            cout << "Book ID: ";
            cin >> id;
            for (int i = 0; i < n; i++)
                if (b[i].id == id) {
                    b[i].issued = (choice == 2);
                    cout << (choice == 2 ? "Book Issued\n" : "Book Returned\n");
                }
        }

        else if (choice == 4) {
            cout << "Enter title/author: ";
            cin >> s;
            for (int i = 0; i < n; i++)
                if (b[i].title == s || b[i].author == s)
                    cout << b[i].id << " " << b[i].title << " "
                         << b[i].author << " "
                         << (b[i].issued ? "Issued" : "Available") << endl;
        }

    } while (choice != 5);

    return 0;
}