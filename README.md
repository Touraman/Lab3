# Lab3
#include <iostream>
#include <vector>
#include <cmath>
#include <algorithm>
#include <numeric>
#include <cstdlib>

using namespace std;

// ************** list03_rev.pdf **********

// PGCD et PPCM
int gcd(int a, int b) {
    return b == 0 ? a : gcd(b, a % b);
}

int lcm(int a, int b) {
    return (a * b) / gcd(a, b);
}

// Conversion de base
string convertToBase(int number, int base) {
    string result = "";
    while (number > 0) {
        result = to_string(number % base) + result;
        number /= base;
    }
    return result;
}

int convertFromBase(const string &number, int base) {
    int result = 0;
    for (char digit : number) {
        result = result * base + (digit - '0');
    }
    return result;
}

// Vérification STARKX
bool isStarkx(const vector<int> &vec) {
    for (size_t i = 0; i < vec.size(); i += 2) {
        for (size_t j = 1; j < vec.size(); j += 2) {
            if (vec[i] <= vec[j]) return false;
        }
    }
    return true;
}

// Extraction des plus grandes chiffres
string extractLargestDigits(const vector<int> &vec) {
    string result = "";
    for (int num : vec) {
        int largestDigit = 0;
        while (num > 0) {
            largestDigit = max(largestDigit, num % 10);
            num /= 10;
        }
        result += to_string(largestDigit);
    }
    return result;
}
