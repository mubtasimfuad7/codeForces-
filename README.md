// codeForces-
//codeForces solutions 
//1305B-KuroniAndSimpleStrings.cpp



#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::ios_base::sync_with_stdio(false);
    std::cin.tie(nullptr);

    std::string s;
    std::cin >> s;

    std::vector<long> positions;
    long right = s.size() - 1;

    for (long left = 0; left < s.size(); ++left) {
        if (s[left] != '(') continue;

        while (right > left) {
            if (s[right] == ')') {
                positions.push_back(left + 1);  // 1-based index
                positions.push_back(right + 1); // 1-based index
                --right;
                break;
            }
            --right;
        }
    }

    std::sort(positions.begin(), positions.end());

    if (positions.empty()) {
        std::cout << "0\n";
    } else {
        std::cout << "1\n" << positions.size() << "\n";
        for (long pos : positions) {
            std::cout << pos << " ";
        }
        std::cout << "\n";
    }

    return 0;
}
