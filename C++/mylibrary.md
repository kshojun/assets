split
```c++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

vector<string> split(string str, char del) {
    int first = 0;
    int last = str.find_first_of(del, first);
    vector<string> result;

    while (first < str.size()) {
        string sub_str(str, first, last - first);
        result.push_back(sub_str);
        first = last + 1;
        last = str.find_first_of(del, first);
        if (last == string::npos) {
            last = str.size();
        }
    }

    return result;
}

int main() {
    string in = "a b c d";
    vector<string> v;
    v = split(in, ' ');
}
```
