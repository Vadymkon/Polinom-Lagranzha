#include <iostream>
#include <vector>
#include <iomanip> // std::setprecision
#include <cmath> //exp i sin
using namespace std;
vector<float> x = { 2.51, 2.62, 2.7, 2.81, 2.91, 2.959, 3.0, 3.01, 3.04, 3.05, 3.07, 3.08
};
vector<float> y = {
-1.2932, -10.4527, 11.0147, -3.2493, -8.6484, 13.4931, 19.2093, 17.1088, 3.74,
-2.0721, -13.2096, -17.6195
};
vector <float> xsavearr = x, ysavearr = y;
vector<float> t;
vector<float> xnew, ynew; //донорские массивы с нужными нам точками
интерполейшина
float a = 2.5, asave = a, b = 3, h = 0.01;
void genT() {
for (a = 2.5; a <= b; a += h) {
t.push_back(a);
}
a = asave;
}
//polinya находит значение х-а благодаря данным х и у
float polinya(vector<float> x, vector<float> y, float tt) {
float polinomius = 0; // переменная под сумму полиномов
float polinomstarter=0;
for (int j = 0; j < y.size(); j++) { //мб будут проблемы с нулём, попроьуй сменить
на 1 j //+ один фор для (у) игрика
float chisl = 1, znam = 1, l; //единицы потому что умножаем же, камон)
for (int i = 0; i < x.size(); i++) { //второй фор для (х) икса
if (i != j) { //для знам'а, шоб на ноль не делить, а то будет грусть
chisl *= (tt - x[i]);
znam *= (x[j] - x[i]); //обрати внимание что тут есть *=, так что это не
один слогаемое
l = chisl / znam; //увесь той страшный доданок
}
}
polinomstarter = l * y[j]; //одна из многих частей полинома, которые потом
будут суммой
polinomius += polinomstarter;
}
return polinomius;
}
float funcmywe(float x) {
return exp(x) * sin(pow(x, 3));
}
void generate_dots(vector<float> x, vector<float> y, float x_custom)
{//поиск точек с минимальной разницей
for (int k = 0; k < 4; k++) //повтор 4 раза, для поиска ЧЕТЫРЁХ ТОЧЕК
{
float min = x[0];
int indexfor_y = 0;
for (int i = 0; i < x.size()-1; i++)
//перебор элементов для создания min
{
if (abs(x_custom - x[i]) > abs(x_custom - x[i + 1])) //проверка разницы
между элементами с нужным числом
{
min = x[i + 1]; //новый минимум
indexfor_y = i + 1;
}
}
xnew.push_back(min); //иксы есть
ynew.push_back(y[indexfor_y]);
//cout << "x= " << min << " y=" << y[indexfor_y] << endl; //проверка
x.erase(x.begin() + indexfor_y);
y.erase(y.begin() + indexfor_y);
}
}
float diff(float x_cust)
{
float fdef;
x = xsavearr;
y = ysavearr;
//polinya находит значение х-а благодаря данным х и у
fdef = (polinya(x, y, x_cust +h) - polinya(x, y, x_cust)) / h;
return fdef;
}
float ddiff(float x_cust)
{
float fdef;
x = xsavearr;
y = ysavearr;
//polinya находит значение х-а благодаря данным х и у
fdef = (diff(x_cust+h) - diff(x_cust)) / h;
return fdef;
}
float diffreal(float x)
{
return 3 * pow(x, 2) * pow(exp(1), x) * cos(pow(x, 3)) + pow(exp(1),x) * sin(pow(x,
3));
}
float ddiffreal(float x)
{
return -9 * pow(x, 4) * pow(exp(1), x) * sin(pow(x, 3)) + 6 * pow(x, 2) * pow(exp(1),
x) * cos(pow(x, 3)) + 6 * x * pow(exp(1), x) *
cos(pow(x, 3)) + pow(exp(1), x) * sin(pow(x, 3));
}
int main()
{
genT(); //ф-я что формулирует область значений
/*
проверка ГенТА
int i = 0;
while (true) {
i++;
cout << t[i] << endl;
}
cout << "The end.";
*/
//cout.precision(10);
for (int k = 0; k < t.size(); k++) {
cout << k+1 << ") " << "x = " << t[k] << "\t that is = " << polinya(x, y, t[k]) << "\t
like this = " << funcmywe(t[k]) << endl;
}
/////////////////////// B
float x_custom; //просит х, для кубической интерполяции
cout << "\n" << "Enter your x in [a;b]: ";
cin >> x_custom;
//проверка на границы
if (a-h>= x_custom || x_custom>=b+h || !cin)
{
cout << "Input n0t [a;b] ERROR" << " a: " << a << " b: " << b;
exit(0);
}
//кубическая будет заключатся в том, что мы найдём нужные точки,
//составим из них массивы, и будем юзать просто "полиня" уже без лишних
значений
//итак для куба нам надо 4 точки интерполяции
generate_dots(x, y, x_custom);
cout << "\nDOTS ARE:" << endl;
for (int i = 0; i < xnew.size(); i++)
{
cout << "\n" << xnew[i] << " --- xnew elem\t" << ynew[i] << " --- ynew elem";
}
cout << "\n\nx = " << x_custom << "\t that is = " << polinya(xnew, ynew,
x_custom)
<< "\t like this = " << funcmywe(x_custom) << endl;
//////////////////////////////////////////////////// C
vector <float> diff_real_first;
for (int k = 0; k < t.size(); k++) {
float diffur = diffreal(t[k]);
diff_real_first.push_back(diffur);
}
vector <float> diff_real_second;
for (int k = 0; k < t.size(); k++) {
float diffur = ddiffreal(t[k]);
diff_real_second.push_back(diffur);
}
//для формулы числового диф-а - нужно использовать кусочную интерполяцию
для поиска х-а + h
vector<float> diff_arr_first;
for (int k = 0; k < t.size(); k++) {
float diffur = diff(t[k]);
diff_arr_first.push_back(diffur);
}
vector<float> diff_arr_second;
for (int k = 0; k < t.size(); k++) {
float diffur = ddiff(t[k]);
diff_arr_second.push_back(diffur);
}
cout << setprecision(3);
for (int k = 0; k < diff_real_first.size(); k++) {
cout << "\n\n" << k + 1 << ") " << t[k] << endl
<< "RealF: \t" << diff_real_first[k] << "\t"
<< "LagrF: \t" << diff_arr_first[k] << "\t"
<< "RealS: \t" << diff_real_second[k] << "\t"
<< "LagrS: \t" << diff_arr_second[k] << "\t";
}
}
