# Binary-Expo
Code for a basic Binary Exponentiation program
#include <iostream>
#include <vector>
using namespace std;

//This program will ask the user to input a base, an exponent and a modulo
//it will make use of binary representation and modular exponentiation
//The output should be the based (a) raised to the power (k) mod modulo(n)

//binary representation prototype
void biconversion(int k, vector<int> &bi);

//Modular Exponentiation prototype
int exponent(int a, int k, int n, vector<int>bi);

int main() {

	//main loop to prevent the program from closing instantly
	int exit = 1;
	while (exit != 0) 
	{
		//variable declaration
		//n is equal to 0 to prevent division by 0 in a later loop
		int k, a, n = 0, result;
		vector <int> bi;

		//intialization of k and a
		cout << "\nThis program will turn a power into binary and use modular expontiation" << endl
			<< "to raise a number to that power" << endl;
		
		cout << "\ninput your base (a): " << endl;
		cin >> a;

		cout << "\ninput your power (k): " << endl;
		cin >> k;

		//formal initialization of n and prevention of division by 0
		while (n == 0){

			cout << "\ninput the modulus (n): " << endl;
			cin >> n;
			if (n == 0)
				cout << "\nDivision by 0 is not allowed";

		}

		
		//binary representation
		biconversion(k, bi);
		//modular exponintiation
		result = exponent(a, k, n, bi);

		//output
		cout << "\n\n" << a << " to the power of " << k <<" mod "<< n << " is " << result << endl;

		//exit expression of main while loop 
		cout << "\n\nenter 0 if you wanna exit the program: ";
		cin >> exit;
	}

	return 0;
}


//binary representation function definition
void biconversion(int k, vector<int> &bi) {

	int i = 0;
	int temp = 0;

	while (k > 0) {

		temp = k % 2;
		bi.push_back(temp);
		k /= 2;
	}
}

//modular exponintiation function definition
int exponent(int a, int k, int n, vector<int>bi) {

	int b = 1;

	if (k == 0)
		return b;

	int A = a;

	if (bi[0] == 1)
		b = a;
	for (int i = 1; i < bi.size(); i++)
	{
		A = (A * A)%n;
		if (bi[i] == 1)
			b = (A * b)%n;
	}

	return b;
}
