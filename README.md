# Final-from-2016
Application to observe voltages across resistors in series
#include <iostream>
using namespace std;

//Define functions
double current_through();
double power_dissipated_across();
double voltage_drops();
//Main Program
int main()
{
	double resistor = 0;
	double Watts = 0;
	double voltage_drop = 0;
	double resistors = 0;
	double voltage = 0;
	double current = 0;
	double Total_Arrayed[50] = { 0 };
	int I = 0;
	double Total = 0;
	char response;
	

	cout << "------------------------------------------------------------ \n";
	cout << "|Enter A for Total Resistance                              | \n";
	cout << "|Enter B for all resistor in circuit                       | \n";
	cout << "|Enter C for Circuit current                               | \n";
	cout << "|Enter D for total power disipated in circuit              | \n";
	cout << "|Enter E for voltage drop on each resistor                 | \n";
	cout << "|Enter F for summation of circuit with power dissapation   | \n";
	cout << "|Enter H for Exit to program                               | \n";
	cout << "------------------------------------------------------------ \n";

	cin >> response;
	response = toupper(response);
	while (response == 'A')
	{
		//Entering array parameters
		cout << "\n Enter maximum number of measurements in the List \t";
		cin >> resistors;

		//Entering numbers into array
		for (I = 0; I < resistors; ++I)
		{
			cout << "\n Enter Resistor # \t" << I + 1 << "  ";
			cin >> resistor;
			Total_Arrayed[I] = resistor;

		}
		for (I = 0; I < resistors; ++I)
		{
			Total += Total_Arrayed[I];
		}
		cout << "\n Total Resistance   " << Total << endl;
		cout << '\n';
		cout << " Would you like to see this again? press A";
		cin >> response;
	}
	while (response == 'B')
	{	
		//Entering array parameters
		cout << "\n Enter maximum number of measurements in the List \t";
		cin >> resistors;
		
		//Entering numbers into array
		for (I = 0; I < resistors; ++I)
		{
			cout << "\n Enter Resistor # \t" << I + 1 << "  ";
			cin >> resistor;
			Total_Arrayed[I] = resistor;

		}
		for (I = 0; I < resistors; ++I)
		{
			cout << "Display Resistors  [" << I << "] " << Total_Arrayed[I] << endl;
		}
		cout << '\n';
		cout << "Would you like to see this again? press B";
		cin >> response;
	}
	while (response == 'C')
	{
		current = current_through();
		cout << "Would you like to do this again press C";
		cin >> response;
	}
	while (response == 'D')
	{
		Watts = power_dissipated_across();
		cout << "Would you like to do this again press D";
		cin >> response;
	}
	while (response == 'E')
	{
		voltage_drop = voltage_drops();
		cout << "Would you like to do this again press E";
		cin >> response;
	}
	while (response == 'F')
	{
		cout << resistors << voltage_drop << Watts;
	}
	while (response == 'H')
	{
		cout << "Goodbye";
		return 0;
	}
}

//Function Current through the circuit
double current_through()
{
	double voltage;
	double current;
	double resistor;
	double resistors;
	int I;
	double Total = 0;
	double Total_Arrayed[50];
	cout << "\n Enter Voltage the circuit will be running at";
	cin >> voltage;

	//Entering array parameters
	cout << "\n Enter maximum number of measurements in the List \t";
	cin >> resistors;

	//Entering numbers into array
	for (I = 0; I < resistors; ++I)
	{
		cout << "\n Enter Resistor # \t" << I + 1 << "  ";
		cin >> resistor;
		Total_Arrayed[I] = resistor;

	}
	
	for (I = 0; I < resistors; ++I)
	{
		Total += Total_Arrayed[I];
	}
	current = voltage / Total;
	cout << "Current through Circuit   " << current << endl;

	return current;
}

//Function Power dissipated across circuit
double power_dissipated_across()
{
	double voltage;
	double Watts;
	double current;
	double resistor;
	double resistors;
	int I;
	double Total = 0;
	double Total_Arrayed[50];
	cout << "\n Enter Voltage the circuit will be running at";
	cin >> voltage;
	//Entering array parameters
	cout << "\n Enter maximum number of measurements in the List \t";
	cin >> resistors;
	//Entering numbers into array
	for (I = 0; I < resistors; ++I)
	{
		cout << "\n Enter Resistor # \t" << I + 1 << "  ";
		cin >> resistor;
		Total_Arrayed[I] = resistor;

	}

	for (I = 0; I < resistors; ++I)
	{
		Total += Total_Arrayed[I];
	}
	current = voltage / Total;
	Watts = voltage * current;
	cout << "Power Disipated over circuit   " << Watts << endl;

	return Watts;
}

//Function Voltage dropped across circuit
double voltage_drops()
{
	double voltage;
	double voltage_drop;
	double resistor = 0;
	double resistors;
	int I;
	double Total = 0;
	double Total_Arrayed[50];
	cout << "\n Enter Voltage the circuit will be running at";
	cin >> voltage;

	//Entering array parameters
	cout << "\n Enter maximum number of measurements in the List \t";
	cin >> resistors;

	//Entering numbers into array
	for (I = 0; I < resistors; ++I)
	{
		cout << "\n Enter Resistor # \t" << I + 1 << "  ";
		cin >> resistor;
		Total_Arrayed[I] = resistor;
		Total += Total_Arrayed[I];
		voltage_drop = voltage*Total / Total_Arrayed[I];
		cout << "Voltage Drop across resistors   " << voltage_drop << endl;

	}
	
	return voltage_drop;
}
