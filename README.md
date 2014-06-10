Ca-kowanie-numeryczne---Projekt-na-Systemy-Operacyjne
=====================================================
#include <iomanip>
#include <iostream>
#include <cstdlib>
#include<fstream>

using namespace std;

//*******************************
//** Tutaj definiujemy funkcję **
//*******************************

double wsp[2];

double f(double x)
{int i;
fstream plik;
plik.open("wsp.txt",std::ios::in | std::ios::out);
	if(plik.good()==true)
	{
		

		for(i=0;i<2;i++)
		{
			plik>>wsp[i];
		}
	}
  return(wsp[0]*x * x + wsp[1]*2 * x);
}


void metodaprostokatow(double N)
{double xp,xk,s,dx;
int i;
	 cout<<"metoda prostokatow"<<endl;
	  
		  cout << "Podaj poczatek przedzialu calkowania\n\n"
          "xp = ";

  cin >> xp;
  cout << "\nPodaj koniec przedzialu calkowania\n\n"
          "xk = ";
  cin >> xk;
  cout << endl;
  s  = 0;
  dx = (xk - xp) /N;
  for(i = 1; i <= N; i++) s += f(xp + i * dx);
  s *= dx;
  cout << "Wartosc calki wynosi : " << setw(8) << s
  << endl << endl;
}
