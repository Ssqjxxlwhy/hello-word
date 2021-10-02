#include<iostream>
using namespace std;
class FenShu {
private:
	int zi;
	int mu;
public:
	FenShu(int = 1, int = 1);
	void display();
	FenShu reduction();
	FenShu add(FenShu B);
	FenShu sub(FenShu B);
	FenShu mul(FenShu B);
	FenShu div(FenShu B);
};

FenShu::FenShu(int x, int y) {
	zi = x;
	mu = y;
}

void FenShu::display() {
	if (zi == 1 && mu == 1)
		cout << 1 <<endl;
	else if (zi == 0)
		cout << 0 <<endl;
	else
		cout << zi << '/' << mu << endl;
}

FenShu FenShu::reduction() {
	FenShu temp;
	int i = zi, j = mu, k;
	while (j != 0) {
		k = i % j; 
		i = j;
		j = k;
	}
	temp.zi = zi / i;
	temp.mu = mu / i;
	return temp;
}


FenShu FenShu::add(FenShu B) {
	FenShu temp;
	temp.mu = this->mu * B.mu;
	temp.zi = this->zi * B.mu + this->mu * B.zi;
	return temp;
}

FenShu FenShu::sub(FenShu B) {
	FenShu temp;
	temp.mu = this->mu * B.mu;
    temp.zi = this->zi * B.mu - this->mu * B.zi;
	return temp;
}

FenShu FenShu::mul(FenShu B) {
	FenShu temp;
	temp.mu = this->mu * B.mu;
	temp.zi = this->zi * B.zi;
	return temp;
}

FenShu FenShu::div(FenShu B) {
	FenShu temp;
	temp.mu = this->mu * B.zi;
	temp.zi = this->zi * B.mu;
	return temp;
}

int main() {
	FenShu p1(2,12),p2(56,84),p3;
	p3 = p1.add(p2); p3 = p3.reduction(); p3.display();
	p3 = p1.sub(p2); p3 = p3.reduction(); p3.display();
	p3 = p1.mul(p2); p3 = p3.reduction(); p3.display();
	p3 = p1.div(p2); p3 = p3.reduction(); p3.display();
	return 0;
}
