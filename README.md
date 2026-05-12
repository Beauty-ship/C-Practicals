# C-Practicals
1. Program to Compute Sum of First n Terms of a Series
   #include <iostream>
#include <cstdlib>
using namespace std;

int main(int argc, char *argv[])
{
    int n;

    // Check command line argument
    if (argc > 1)
    {
        n = atoi(argv[1]);
    }
    else
    {
        cout << "Enter value of n: ";
        cin >> n;
    }

    double sum = 0;

    for (int i = 1; i <= n; i++)
    {
        sum = sum + (1.0 / i);
    }

    cout << "Sum of series = " << sum;

    return 0;
}
2. Program to Remove Duplicates from an Array
 #include <iostream>
using namespace std;

int main()
{
    int arr[100], n;

    cout << "Enter number of elements: ";
    cin >> n;

    cout << "Enter array elements: ";

    for (int i = 0; i < n; i++)
    {
        cin >> arr[i];
    }

    cout << "Array after removing duplicates: ";

    for (int i = 0; i < n; i++)
    {
        bool duplicate = false;

        for (int j = 0; j < i; j++)
        {
            if (arr[i] == arr[j])
            {
                duplicate = true;
                break;
            }
        }

        if (!duplicate)
        {
            cout << arr[i] << " ";
        }
    }

    return 0;
}
3. Program to Count Occurrences of Alphabets
  #include <iostream>
#include <cstring>
using namespace std;

int main(int argc, char *argv[])
{
    int count[26] = {0};

    for (int i = 1; i < argc; i++)
    {
        for (int j = 0; argv[i][j] != '\0'; j++)
        {
            char ch = argv[i][j];

            if (ch >= 'A' && ch <= 'Z')
            {
                ch = ch + 32;
            }

            if (ch >= 'a' && ch <= 'z')
            {
                count[ch - 'a']++;
            }
        }
    }

    cout << "Alphabet Occurrences:\n";

    for (int i = 0; i < 26; i++)
    {
        cout << char(i + 'a') << " : " << count[i] << endl;
    }

    return 0;
}
4. Menu Driven String Manipulation Program
  #include <iostream>
using namespace std;

// Function to find length
int length(char str[])
{
    int len = 0;

    while (str[len] != '\0')
    {
        len++;
    }

    return len;
}

// Concatenate
void concatenate(char s1[], char s2[])
{
    int i = length(s1);
    int j = 0;

    while (s2[j] != '\0')
    {
        s1[i] = s2[j];
        i++;
        j++;
    }

    s1[i] = '\0';

    cout << "Concatenated String: " << s1 << endl;
}

// Compare
void compare(char s1[], char s2[])
{
    int i = 0;

    while (s1[i] == s2[i] && s1[i] != '\0' && s2[i] != '\0')
    {
        i++;
    }

    if (s1[i] == s2[i])
        cout << "Strings are Equal\n";
    else
        cout << "Strings are Not Equal\n";
}

// Uppercase
void uppercase(char str[])
{
    for (int i = 0; str[i] != '\0'; i++)
    {
        if (str[i] >= 'a' && str[i] <= 'z')
        {
            str[i] = str[i] - 32;
        }
    }

    cout << "Uppercase String: " << str << endl;
}

// Reverse
void reverse(char str[])
{
    int len = length(str);

    for (int i = len - 1; i >= 0; i--)
    {
        cout << str[i];
    }

    cout << endl;
}

// Insert String
void insertString(char mainStr[], char subStr[], int pos)
{
    char result[200];

    int i = 0, j = 0, k = 0;

    while (i < pos)
    {
        result[k++] = mainStr[i++];
    }

    while (subStr[j] != '\0')
    {
        result[k++] = subStr[j++];
    }

    while (mainStr[i] != '\0')
    {
        result[k++] = mainStr[i++];
    }

    result[k] = '\0';

    cout << "Result String: " << result << endl;
}

int main()
{
    char str1[100], str2[100];
    int choice;

    cout << "Enter first string: ";
    cin >> str1;

    cout << "Enter second string: ";
    cin >> str2;

    do
    {
        cout << "\nMENU\n";
        cout << "1. Show address of each character\n";
        cout << "2. Concatenate strings\n";
        cout << "3. Compare strings\n";
        cout << "4. Calculate length\n";
        cout << "5. Convert lowercase to uppercase\n";
        cout << "6. Reverse string\n";
        cout << "7. Insert string\n";
        cout << "8. Exit\n";

        cout << "Enter choice: ";
        cin >> choice;

        switch (choice)
        {
        case 1:
            for (int i = 0; str1[i] != '\0'; i++)
            {
                cout << str1[i] << " : " << (void*)&str1[i] << endl;
            }
            break;

        case 2:
            concatenate(str1, str2);
            break;

        case 3:
            compare(str1, str2);
            break;

        case 4:
            cout << "Length = " << length(str1) << endl;
            break;

        case 5:
            uppercase(str1);
            break;

        case 6:
            reverse(str1);
            break;

        case 7:
        {
            int pos;
            cout << "Enter position: ";
            cin >> pos;

            insertString(str1, str2, pos);
            break;
        }

        case 8:
            cout << "Exiting...\n";
            break;

        default:
            cout << "Invalid Choice\n";
        }

    } while (choice != 8);

    return 0;
}
5. Program to Merge Two Ordered Arrays
  #include <iostream>
using namespace std;

int main()
{
    int a[50], b[50], c[100];
    int n1, n2;

    cout << "Enter size of first array: ";
    cin >> n1;

    cout << "Enter elements in sorted order:\n";
    for (int i = 0; i < n1; i++)
    {
        cin >> a[i];
    }

    cout << "Enter size of second array: ";
    cin >> n2;

    cout << "Enter elements in sorted order:\n";
    for (int i = 0; i < n2; i++)
    {
        cin >> b[i];
    }

    int i = 0, j = 0, k = 0;

    while (i < n1 && j < n2)
    {
        if (a[i] < b[j])
        {
            c[k++] = a[i++];
        }
        else
        {
            c[k++] = b[j++];
        }
    }

    while (i < n1)
    {
        c[k++] = a[i++];
    }

    while (j < n2)
    {
        c[k++] = b[j++];
    }

    cout << "Merged Array:\n";

    for (int i = 0; i < k; i++)
    {
        cout << c[i] << " ";
    }

    return 0;
}
6. Binary Search Program
(a) Binary Search Using Recursion
 #include <iostream>
using namespace std;

int binarySearch(int arr[], int low, int high, int key)
{
    if (low > high)
    {
        return -1;
    }

    int mid = (low + high) / 2;

    if (arr[mid] == key)
    {
        return mid;
    }
    else if (key < arr[mid])
    {
        return binarySearch(arr, low, mid - 1, key);
    }
    else
    {
        return binarySearch(arr, mid + 1, high, key);
    }
}

int main()
{
    int n, key;

    cout << "Enter number of elements: ";
    cin >> n;

    int arr[n];

    cout << "Enter sorted elements:\n";

    for (int i = 0; i < n; i++)
    {
        cin >> arr[i];
    }

    cout << "Enter element to search: ";
    cin >> key;

    int result = binarySearch(arr, 0, n - 1, key);

    if (result != -1)
    {
        cout << "Element found at position " << result + 1;
    }
    else
    {
        cout << "Element not found";
    }

    return 0;
}
b) Binary Search Without Recursion
  #include <iostream>
using namespace std;

int main()
{
    int n, key;

    cout << "Enter number of elements: ";
    cin >> n;

    int arr[n];

    cout << "Enter sorted elements:\n";

    for (int i = 0; i < n; i++)
    {
        cin >> arr[i];
    }

    cout << "Enter element to search: ";
    cin >> key;

    int low = 0, high = n - 1;
    int found = -1;

    while (low <= high)
    {
        int mid = (low + high) / 2;

        if (arr[mid] == key)
        {
            found = mid;
            break;
        }
        else if (key < arr[mid])
        {
            high = mid - 1;
        }
        else
        {
            low = mid + 1;
        }
    }

    if (found != -1)
    {
        cout << "Element found at position " << found + 1;
    }
    else
    {
        cout << "Element not found";
    }

    return 0;
}
7. Program to Calculate GCD
(a) GCD Using Recursion
  #include <iostream>
using namespace std;

int gcd(int a, int b)
{
    if (b == 0)
    {
        return a;
    }

    return gcd(b, a % b);
}

int main()
{
    int a, b;

    cout << "Enter two numbers: ";
    cin >> a >> b;

    cout << "GCD = " << gcd(a, b);

    return 0;
}
b) GCD Without Recursion
  #include <iostream>
using namespace std;

int main()
{
    int a, b;

    cout << "Enter two numbers: ";
    cin >> a >> b;

    while (b != 0)
    {
        int temp = b;
        b = a % b;
        a = temp;
    }

    cout << "GCD = " << a;

    return 0;
}
8. Matrix Class Program
  #include <iostream>
using namespace std;

class Matrix
{
    int rows, cols;
    int mat[10][10];

public:
    void input()
    {
        cout << "Enter rows and columns: ";
        cin >> rows >> cols;

        cout << "Enter matrix elements:\n";

        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                cin >> mat[i][j];
            }
        }
    }

    void display()
    {
        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                cout << mat[i][j] << " ";
            }
            cout << endl;
        }
    }

    Matrix add(Matrix m)
    {
        if (rows != m.rows || cols != m.cols)
        {
            throw "Addition not possible";
        }

        Matrix temp;
        temp.rows = rows;
        temp.cols = cols;

        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                temp.mat[i][j] = mat[i][j] + m.mat[i][j];
            }
        }

        return temp;
    }

    Matrix multiply(Matrix m)
    {
        if (cols != m.rows)
        {
            throw "Multiplication not possible";
        }

        Matrix temp;
        temp.rows = rows;
        temp.cols = m.cols;

        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < m.cols; j++)
            {
                temp.mat[i][j] = 0;

                for (int k = 0; k < cols; k++)
                {
                    temp.mat[i][j] += mat[i][k] * m.mat[k][j];
                }
            }
        }

        return temp;
    }

    Matrix transpose()
    {
        Matrix temp;
        temp.rows = cols;
        temp.cols = rows;

        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                temp.mat[j][i] = mat[i][j];
            }
        }

        return temp;
    }
};

int main()
{
    Matrix m1, m2, result;
    int choice;

    m1.input();
    m2.input();

    cout << "\n1. Sum\n2. Product\n3. Transpose\n";
    cout << "Enter choice: ";
    cin >> choice;

    try
    {
        switch (choice)
        {
        case 1:
            result = m1.add(m2);
            result.display();
            break;

        case 2:
            result = m1.multiply(m2);
            result.display();
            break;

        case 3:
            result = m1.transpose();
            result.display();
            break;

        default:
            cout << "Invalid Choice";
        }
    }
    catch (const char *msg)
    {
        cout << "Exception: " << msg;
    }

    return 0;
}
9. Runtime Polymorphism Example
  #include <iostream>
using namespace std;

class Person
{
protected:
    string name;

public:
    virtual void display()
    {
        cout << "Name: " << name << endl;
    }
};

class Student : public Person
{
    string course;
    int marks, year;

public:
    Student(string n, string c, int m, int y)
    {
        name = n;
        course = c;
        marks = m;
        year = y;
    }

    void display()
    {
        cout << "\nStudent Details\n";
        cout << "Name: " << name << endl;
        cout << "Course: " << course << endl;
        cout << "Marks: " << marks << endl;
        cout << "Year: " << year << endl;
    }
};

class Employee : public Person
{
    string department;
    float salary;

public:
    Employee(string n, string d, float s)
    {
        name = n;
        department = d;
        salary = s;
    }

    void display()
    {
        cout << "\nEmployee Details\n";
        cout << "Name: " << name << endl;
        cout << "Department: " << department << endl;
        cout << "Salary: " << salary << endl;
    }
};

int main()
{
    Person *p;

    Student s("Rahul", "BCA", 85, 2);
    Employee e("Amit", "HR", 50000);

    p = &s;
    p->display();

    p = &e;
    p->display();

    return 0;
}
10. Triangle Class with Exception Handling
  #include <iostream>
#include <cmath>
using namespace std;

class Triangle
{
    float a, b, c;

public:
    Triangle(float x, float y, float z)
    {
        if (x <= 0 || y <= 0 || z <= 0)
        {
            throw "Sides must be greater than 0";
        }

        if ((x + y <= z) || (y + z <= x) || (x + z <= y))
        {
            throw "Invalid Triangle";
        }

        a = x;
        b = y;
        c = z;
    }

    float area(float base, float height)
    {
        return 0.5 * base * height;
    }

    float area()
    {
        float s = (a + b + c) / 2;
        return sqrt(s * (s - a) * (s - b) * (s - c));
    }
};

int main()
{
    try
    {
        Triangle t(3, 4, 5);

        cout << "Area using Heron's Formula = " << t.area() << endl;

        cout << "Area of Right Triangle = " << t.area(3, 4);
    }
    catch (const char *msg)
    {
        cout << "Exception: " << msg;
    }

    return 0;
}
11. Store and Retrieve Student Records from File
  #include <iostream>
#include <fstream>
using namespace std;

class Student
{
    int rollNo;
    char name[50];
    char sclass[20];
    int year;
    float marks;

public:
    void input()
    {
        cout << "Enter Roll No: ";
        cin >> rollNo;

        cout << "Enter Name: ";
        cin >> name;

        cout << "Enter Class: ";
        cin >> sclass;

        cout << "Enter Year: ";
        cin >> year;

        cout << "Enter Total Marks: ";
        cin >> marks;
    }

    void display()
    {
        cout << "\nRoll No: " << rollNo;
        cout << "\nName: " << name;
        cout << "\nClass: " << sclass;
        cout << "\nYear: " << year;
        cout << "\nMarks: " << marks << endl;
    }
};

int main()
{
    Student s[5];

    ofstream fout("student.dat", ios::binary);

    for (int i = 0; i < 5; i++)
    {
        s[i].input();
        fout.write((char*)&s[i], sizeof(s[i]));
    }

    fout.close();

    ifstream fin("student.dat", ios::binary);

    cout << "\nStudent Records:\n";

    for (int i = 0; i < 5; i++)
    {
        fin.read((char*)&s[i], sizeof(s[i]));
        s[i].display();
    }

    fin.close();

    return 0;
}
12. Copy File Contents After Removing Whitespaces
  #include <iostream>
#include <fstream>
using namespace std;

int main()
{
    ifstream fin("input.txt");
    ofstream fout("output.txt");

    char ch;

    while (fin.get(ch))
    {
        if (ch != ' ' && ch != '\n' && ch != '\t')
        {
            fout.put(ch);
        }
    }

    cout << "File copied successfully without whitespaces.";

    fin.close();
    fout.close();

    return 0;
}
  
