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
void metodatrapezow(double N)
{double xp,xk,s,dx;
	 int i;

  cout << setprecision(3)      // 3 cyfry po przecinku
       << fixed;               // format stałoprzecinkowy

  cout << "Podaj poczatek przedzialu calkowania\n\n"
          "xp = ";
  cin >> xp;
  cout << "\nPodaj koniec przedzialu calkowania\n\n"
          "xk = ";
  cin >> xk;
  cout << endl;
  s  = 0;
  dx = (xk - xp) / N;
  for(i = 1; i < N; i++) s += f(xp + i * dx);
  s = (s + (f(xp) + f(xk)) / 2) * dx;
  cout << "Wartosc calki wynosi : " << setw(8) << s
       << endl << endl;
}

void simpson(double N)
{int i;
double xp,xk,dx,s,st,x;
		  cout << setprecision(3)      // 3 cyfry po przecinku
       << fixed;               // format stałoprzecinkowy

  cout << "Podaj poczatek przedzialu calkowania\n\n"
          "xp = ";
  cin >> xp;
  cout << "\nPodaj koniec przedzialu calkowania\n\n"
          "xk = ";
  cin >> xk;
  cout << endl;
  s  = 0; st = 0;
  dx = (xk - xp) / N;
  for(i = 1; i <= N; i++)
  {
    x = xp + i * dx;
    st += f(x - dx / 2);
    if(i < N) s += f(x);
  }
  s = dx / 6 * (f(xp) + f(xk) + 2 * s + 4 * st);
  cout << "Wartosc calki wynosi : " << setw(8) << s<<endl<<endl;
}
//********************
//** Program główny **
//********************

int main()
{
  const int N = 1000; //liczba punktów/prostokątów podziałowych
  double xp,xk,s,dx,st,x;
  int i;
  int wybor;
  cout<<"wybierz metode"<<endl;
  cout<<"1.Metoda Prostokatow"<<endl;
  cout<<"2.Metoda trapezow"<<endl;
  cout<<"3.Metoda Simphsona"<<endl;
  cin>>wybor;

  switch(wybor)
  {
  case 1: cout<<"metoda prostokatow"<<endl;
	  {
		  metodaprostokatow(N);
	  }
	  break;

  case 2:cout<<"metoda trapezow"<<endl;
	  {
		  
 metodatrapezow(N);
	  }
	  break;

  case 3:
	  {
	
       simpson(N);
	  }
	  break;


  default:
	  break;
  }
  system("pause");
  return 0;
  
} 
