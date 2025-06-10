#include <iostream>
#include <vector>

std::vector<int> foldStrip(int k) {
    int length = 1 << k; // 2^k
    std::vector<int> strip(length);

    // Инициализация вектора номерами клеток
    for (int i = 0; i < length; ++i) {
        strip[i] = i + 1;
    }

    // Сгибание полоски
    for (int i = 0; i < k; ++i) {
        int mid = length >> (i + 1); // Середина полоски после i-го сгиба
        for (int j = 0; j < mid; ++j) {
            // Перестановка элементов так, чтобы после сгибания они были в правильном порядке
            std::swap(strip[j], strip[length - 1 - j]);
        }
    }

    return strip;
}

int main() {
    int k;
    std::cout << "Введите k: ";
    std::cin >> k;

    std::vector<int> result = foldStrip(k);
    std::cout << "Номера клеток после сгибания: ";
    for (int num : result) {
        std::cout << num << " ";
    }
    std::cout << std::endl;

    return 0;
}
