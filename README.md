
#include <iostream>
#include <string>

using namespace std;


class Account {
private:
    int accountNumber;
    string accountHolderName;
    string accountType;
    double balance;

public:
    
    Account(int accNumber, string accHolderName, string accType, double initialDeposit);

    
    void createAccount();
    void modifyAccountDetails();
    void deposit(double amount);
    void withdraw(double amount);
    void displayAccountInfo();
};


Account::Account(int accNumber, string accHolderName, string accType, double initialDeposit) {
    accountNumber = accNumber;
    accountHolderName = accHolderName;
    accountType = accType;
    balance = initialDeposit;
}


void Account::createAccount() {
    cout << "Enter account number: ";
    cin >> accountNumber;
    cout << "Enter account holder's name: ";
    cin.ignore();
    getline(cin, accountHolderName);
    cout << "Enter the account type (Savings or Current): ";
    cin >> accountType;
    cout << "Enter initial deposit amount: ";
    cin >> balance;
    cout << "Account created successfully." << endl;
}

// Function to modify account details
void Account::modifyAccountDetails() {
    cout << "Enter new account holder's name: ";
    cin.ignore();
    getline(cin, accountHolderName);
    cout << "Enter new account type (Savings or Current): ";
    cin >> accountType;
    cout << "Account details modified successfully." << endl;
}


void Account::deposit(double amount) {
    balance += amount;
    cout << "Deposit of R" << amount << " successful." << endl;
}


void Account::withdraw(double amount) {
    if (amount <= balance) {
        balance -= amount;
        cout << "Withdrawal of R" << amount << " successful." << endl;
    } else {
        cout << "NOT ENOUGH MONEY !!. Withdrawal failed." << endl;
    }
}

// Function to display account information
void Account::displayAccountInfo() {
    cout << "Account Number: " << accountNumber << endl;
    cout << "Account Holder's Name: " << accountHolderName << endl;
    cout << "Account Type: " << accountType << endl;
    cout << "Account Balance: R" << balance << endl;
}

int main() {
    // Test the Account class
    Account myAccount(0, "", "", 0.0);

    int choice;
    double amount;

    do {
        cout << "\n\n\tBANK FOR THE PEOPLE";
        cout << "\nBank Management System\n";
        cout << "1. Create an Account\n";
        cout << "2. Modify Account Details\n";
        cout << "3. Deposit Money\n";
        cout << "4. Withdraw Money\n";
        cout << "5. Display Account Information\n";
        cout << "6. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                myAccount.createAccount();
                break;
            case 2:
                myAccount.modifyAccountDetails();
                break;
            case 3:
                cout << "Enter deposit amount: ";
                cin >> amount;
                myAccount.deposit(amount);
                break;
            case 4:
                cout << "Enter withdrawal amount: ";
                cin >> amount;
                myAccount.withdraw(amount);
                break;
            case 5:
                myAccount.displayAccountInfo();
                break;
            case 6:
                cout << "Thank You Have a nice day...";
                break;
            default:
                cout << "Invalid choice. Please try again.";
        }
    } while (choice != 6);

    return 0;
}
