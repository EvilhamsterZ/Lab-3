# Lab-3
## Сабуров Сергей Фт-200008
## Лабораторная номер 3 Шифр Цезаря
### Описание программы
Программа принимает целочисленное значение шаг шифровки и строку для шифровки с пробелами, в результате получается зашифрованная строка на шаг алфавита заданный пользователем.
* программа принимает только строчные буквы.(могу допилить и заглавные но это усложнит код и мою жизнь :))
** сбоит при шифре на 33 шага...но это ведь исходный текст. скажем так шифровка возможна до 32 шагов по алфавиту(никто не придерётся ведь исходная цель была зашифровать а не выдать исходный текст( могу допилить:))).
### ПО Visual studio 2019
#### КОД
```
#include <iostream>
#include <Windows.h>//библиотека для русского ввода/вывода
#include <string> //стринговая библиотека
#include <sstream>

int main()
{
    SetConsoleCP(1251);//русский ввод
    SetConsoleOutputCP(1251);//вывод
    int p;
    int h = 0;//если не занулить не работает
    int n;
    int o;
    char c;//для символа строки
    std::string s = "Результат: ";
    std::string m;//сама строка
    std::string z;//сама строка
    std::string l = "абвгдеёжзийклмнопрстуфхцчшщъыьэюя";

    std::cout << "Введите шаг шифрования n= ";
    std::cin >> n;
    std::cout << "Введите строку для шифрования " << std::endl;
    std::cin >> z;// столкнулся с проблемой гетлайн пропускает первое слово. для этого использовал конструкцию конкатенации строк з и м где м считывает до пробела а м после.
    std::getline(std::cin, m);
    m = z + m;

    std::string::iterator end_pos = std::remove(m.begin(), m.end(), ' ');
    m.erase(end_pos, m.end());//чистим пробелы из строки
    std::cout << m << std::endl;//проверка чистки пробелов получается строка для шифровки не думаю что будет лишним показать что шифруется
    p = m.length();//для цикла, немного экономим память
    for (int i = 0; i < p; i++)
    {
        c = m[i];//берем итый символ
        h = l.find_first_of(c);//ищем символ в строке алфавита
        o = n + h;//добавляем шаг кодировки найденному номеру символа алфавита
        if (o > 33)//если символ превысит алфавит то начинаем с абв снова
        {
            o -= 33;
        }
        m[i] = l[o];//присваиваем итому значению новый символ
        h = 0;
    }
    std::cout << m << std::endl;
    return 0;
}
```
#### Скрины выполнения 
![image](https://user-images.githubusercontent.com/90544365/135290304-f1abb49c-4f23-4c4f-9d59-3922ee023bb8.png)
Наблюдается перевод строки в без пробельный могу это убрать но для отладки надо знать че происходит)
простейшее буква а меняется на 2 позиции а -> б -> в повторение замены говорит о работе проги.
![image](https://user-images.githubusercontent.com/90544365/135291712-83027b00-d506-401e-adf6-ac06026ec2de.png)
проверка шага 32. мне лень придумывать умные фразы просто какие то буквы.
