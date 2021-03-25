//В контейнере отсортировать числа до максимального значения
#include <iostream>
#include <vector>     // vector
#include <algorithm>  // sort
#include <bitset>
#include <random>
using namespace std;
bool BitComp(bitset<32>& l, bitset<32>& r)
{
    return int(l.to_ulong()) < int(r.to_ulong());
}
int main() {
    setlocale(0, "");
    vector<bitset<32> > vec;
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());
    
    for (int i = 0; i < 5; i++) {
        vec.push_back(gen());
    }
    cout << "последовательность до: ";
    for (auto  element : vec)
        cout << (int)element.to_ulong() <<  endl;
    
    auto maxIt = max_element(vec.begin(), vec.end(), BitComp);
    cout << endl << "максимум: index:" << distance(vec.begin(), maxIt) << " Значение максимума: " << (int)(*maxIt).to_ulong() << endl;
    
    sort(vec.begin(), maxIt, BitComp);
    cout << "последовательность после: ";
    for (auto element : vec)
        cout << (int)element.to_ulong() << endl;
    system("pause");
    return 0;
}
