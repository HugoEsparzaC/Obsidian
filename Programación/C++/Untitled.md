```
#include <string>
usingnamespace std;
int main(){
	string a = "Hola";
	string b = "Bye";
	string c = a + " " + b;
	cout << c << "\n";
	if(a < c){
		cout << "Yes\n";
	}
	else{
		cout << "No\n";
	}
	a.append('!');
	cout << a << "\n";
}
```