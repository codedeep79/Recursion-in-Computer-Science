# Recursion in Computer Science
The Recursion mathematical problem from basic to advanced in programming computers. All data structure & algorithms in programme can be idealized implement by recursion 

- Conceptualisation of Recursive:
  + Whenever one function calls ITSELF directly or indirectly.
  + The recursion a method of solving a problem where the solution depends on solutions to smaller instances of the same problem (as opposed to iteration). The approach can be applied to many types of problems, and recursion is one of the central ideas of computer science.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f7/RecursiveTree.JPG/300px-RecursiveTree.JPG)

- Types of Recursion:
  + Linear Recursion (đệ quy tuyến tính)
  + Tails Recursion (đệ quy đuôi)
  + Binary Recursion (đệ quy nhị phân)
  + Mutual Recursion (đệ quy hỗ tương)
  + Exponential Recursion (Đệ quy mũ)
  + Nested Recursion (Đệ quy lồng)
  + Nonlinear Recursion (Đệ quy phi tuyến)

_Each branch can be seen as a smaller version of a tree._

## Level: Elementary  

### Presentation of Shapes in recursive:

Shape 1:
```
 *  *  *  *  *
 *  *  *  *
 *  *  *
 *  *
 *
```

```cpp
void printStar(int n)
{
	if (n == 0)
		return;
	for (int i = 0; i < n; ++i)
		cout << " * ";
	cout << "\n";


	printStar(n - 1);
}
```

Shape 2:
```
 *
 *  *
 *  *  *
 *  *  *  *
 *  *  *  *  *
```

```cpp
void printStar(int n, int i)
{
	if (n < 0)
		return;
	if (i > n)
		return;
	for (int index = 0; index < i; ++index)
		cout << " * ";
	cout << "\n";
	printStar(n, i + 1);
}
```

Shape 3:

```
* * * * *
 * * * *
  * * *
   * *
    *
```

```cpp
void triangle(int n, int i)
{
	int index;
	if (n < 0)
		return;
	for (index = 0; index < i; ++index)
		printf(" ");
	for (index = 0; index < n; ++index)
		printf("* ");
	printf("\n");
	triangle(n - 1, i + 1);
}
```

Shape 4:
```
    *
   * *
  * * *
 * * * *
* * * * *
```

```cpp
void triangle(int n, int i)
{
	if (n < 0)
		return;
	triangle(n - 1, i + 1);
	for (int index = 0; index < i; ++index)
		printf(" ");
	for (int index = 0; index < n; ++index)
		printf("* ");
		printf("\n");
}
```

_**References more:**_ 

[Recursion Graphics 1](http://www.cs.princeton.edu/courses/archive/fall09/cos126/assignments/sierpinski.html)

[Recursion Graphics 2](http://www.cs.princeton.edu/courses/archive/spring12/cos126/art/index.php)

Fractals Recursion:
https://www3.nd.edu/~dthain/courses/cse20211/fall2013/lab5/

[Display Snow Flake - Recursion](/SnowFlakeFractals/)

![](/images/SnowFlakeFractals.PNG)

### Tower of Hanoi

Tower of Hanoi is a mathematical puzzle where we have three rods and n disks. The objective of the puzzle is to move the entire stack to another rod, obeying the following simple rules:
1) Only one disk can be moved at a time.
2) Each move consists of taking the upper disk from one of the stacks and placing it on top of another stack i.e. a disk can only be moved if it is the uppermost disk on a stack.
3) No disk may be placed on top of a smaller disk.

```cpp
#include<iostream>
using namespace std;

void towerHaNoi1(int n, char A, char C, char B)
{
	if (n == 1)
		cout << "Move disk 1 from column " << A << " to column " << C << endl;
	else
	{
		towerHaNoi1(n - 1, A, B, C);
		cout << "Move disk " << n << " from column " << A << " to column " << C << endl;
		towerHaNoi1(n - 1, B, C, A);
	}
}

void towerHaNoi2(int n, char A, char B, char C)
{
	if (n == 1)
		cout << "Move disk 1 from column " << A << " to column " << C << endl;
	else
	{
		towerHaNoi2(n - 1, A, C, B);
		cout << "Move disk " << n << " from column " << A << " to column " << C << endl;
		towerHaNoi2(n - 1, B, A, C);
	}
}

void towerHaNoi3(int n, char C, char A, char B)
{
	if (n == 1)
		cout << "Move disk 1 from column " << A << " to column " << C << endl;
	else
	{
		towerHaNoi3(n - 1, B, A, C);
		cout << "Move disk " << n << " from column " << A << " to column " << C << endl;
		towerHaNoi3(n - 1, C, B, A);
	}
}

void towerHaNoi4(int n, char C, char B, char A)
{
	if (n == 1)
		cout << "Move disk 1 from column " << A << " to column " << C << endl;
	else
	{
		towerHaNoi4(n - 1, B, C, A);
		cout << "Move disk " << n << " from column " << A << " to column " << C << endl;
		towerHaNoi4(n - 1, C, A, B);
	}
}

void towerHaNoi5(int n, char B, char A, char C)
{
	if (n == 1)
		cout << "Move disk 1 from column " << A << " to column " << C << endl;
	else
	{
		towerHaNoi5(n - 1, C, A, B);
		cout << "Move disk " << n << " from column " << A << " to column " << C << endl;
		towerHaNoi5(n - 1, A, B, C);
	}
}

void towerHaNoi6(int n, char B, char C, char A)
{
	if (n == 1)
		cout << "Move disk 1 from column " << A << " to column " << C << endl;
	else
	{
		towerHaNoi6(n - 1, C, B, A);
		cout << "Move disk " << n << " from column " << A << " to column " << C << endl;
		towerHaNoi6(n - 1, A, C, B);
	}
}

int main() {
	int n;
	cin >> n;
	cout << "Tower of Hanoi 1: " << endl;
	towerHaNoi1(n, 'A', 'C', 'B');
	//cout << "Tower of Hanoi 2: " << endl;
	//towerHaNoi2(n, 'A', 'B', 'C');
	//cout << "Tower of Hanoi 3: " << endl;
	//towerHaNoi3(n, 'C', 'A', 'B');
	//cout << "Tower of Hanoi 4: " << endl;
	//towerHaNoi4(n, 'C', 'B', 'A');
	//cout << "Tower of Hanoi 5: " << endl;
	//towerHaNoi5(n, 'B', 'A', 'C');
	//cout << "Tower of Hanoi 6: " << endl;
	//towerHaNoi6(n, 'B', 'C', 'A');
	return 0;
}
```

## Level: Intermediate (Data structure & Algorithms) 
- Array
- Linked List
- Stack
- Queue
- Binary Tree
- Binary Search Tree
- Heap
- Hashing
- Graph
- Matrix
- Misc
- Advanced Data Structure
## Level: Advanced Recursion (Recursion Algorithms) 

_Notebook_ 

![](https://avatars0.githubusercontent.com/u/21261394?s=400&v=4)
