# lab13_Hasan

#include <iostream>
#include <vector>
#include <string>
#include <sstream>
#include <list>
#include <list>
#include <forward_list>
#include <deque>
#include <cctype>
#include <queue>

using namespace std;

int countStudentsCanEat(vector<int>& students, vector<int>& sandwiches) {
    queue<int> studentQueue;


    for (int student : students) {
        studentQueue.push(student);
    }


    int sandwichIndex = 0;


    while (!studentQueue.empty()) {

        if (studentQueue.front() == sandwiches[sandwichIndex]) {
            studentQueue.pop();
            sandwichIndex++;
        }

        else {
            studentQueue.push(studentQueue.front());
            studentQueue.pop();
        }


        if (sandwichIndex == sandwiches.size()) {
            break;
        }
    }


    return studentQueue.size();
}

int removeAndCount(vector<int>& nums, int val) {
    int count = 0;
    int replaceValue = -1;

    for (int i = 0; i < nums.size(); ++i) {
        if (nums[i] == val) {
            nums[i] = replaceValue;
        } else {
            ++count;
        }
    }

    return count;
}

void cleanNumbers(vector<string>& vec) {
  vector<string> cleanedVec;
    for (const string& word : vec) {
        bool containsDigit = false;
        for (char ch : word) {
            if (isdigit(ch)) {
                containsDigit = true;
                break;
            }
        }
        if (!containsDigit) {
            cleanedVec.push_back(word);
        }
    }
    vec = cleanedVec;
}
//problem1

//problem3
int main(){
    vector<int> vec;


    vec.assign({1, 2, 3, 4, 5, 6, 7, 8});


    if (!vec.empty()) {

        cout << "Original vector: ";
        for (int num : vec) {
            cout << num << " ";
        }
        cout << endl;


        if (vec.size() >= 5) {
            vec.erase(vec.begin() + 4);
            cout << "Vector after removing element at position 4: ";
            for (int num : vec) {
                cout << num << " ";
            }
            cout << endl;
        } else {
            cout << "Cannot remove element at position 4. Vector size is less than 5." << endl;
        }


        if (vec.size() >= 3) {
            vec.erase(vec.begin() + 1, vec.begin() + 3);
            cout << "Vector after removing range from position 1 to 2: ";
            for (int num : vec) {
                cout << num << " ";
            }
            cout << endl;
        } else {
            cout << "Cannot remove range from position 1 to 2. Vector size is less than 3." <<endl;
        }
    } else {
        cout << "Vector is empty!" << endl;
    }

    return 0;
}


//problem4
int main() {
    int n;
    cout << "Enter the size of the matrix (n x n): ";
    cin >> n;


   vector<vector<double>> matrix(n, vector<double>(n, 0.0));


    cout << "Enter " << n * n << " elements for the matrix:" <<endl;
    for (auto row_it = matrix.begin(); row_it != matrix.end(); ++row_it) {
        for (auto col_it = row_it->begin(); col_it != row_it->end(); ++col_it) {
            cin >> *col_it;
        }
    }


   cout << "Output:" << endl;
    for (const auto& row : matrix) {
        for (const auto& elem : row) {
            cout << elem << " ";
        }
        cout << endl;
    }

    return 0;
}

//problem5
int main() {

    list<double> list1 = {3.3, 4.5, 6.7};
    list<int> list2 = {1, 2, 3};
    list<double> list3 = {8, 9.5, 10.3};


   list<double> mergedList;


    mergedList.splice(mergedList.end(), list3);


    mergedList.splice(mergedList.begin(), list1);


    mergedList.splice(mergedList.end(), list2);


    cout << "Merged list: ";
    for (const auto& elem : mergedList) {
        cout << elem << " ";
    }
    cout << endl;

    return 0;
}


//problem6
    int main () {

    forward_list<int> forwardList = {1, 2, 3, 4, 5};

    auto it = forwardList.before_begin();
    advance(it, 1);
    forwardList.erase_after(it);
   cout << "After deleting the second element: ";
    for (int x : forwardList)
        cout << x << " ";
    cout << endl;


    forwardList.push_front(10);
    cout << "After inserting a value using push_front(): ";
    for (int x : forwardList)
        cout << x << " ";
   cout << endl;


    forwardList.emplace_front(20);
    cout << "After inserting a value using emplace_front(): ";
    for (int x : forwardList)
        cout << x << " ";
    cout << endl;


    forwardList.pop_front();
    cout << "After deleting the first value using pop_front(): ";
    for (int x : forwardList)
        cout << x << " ";
      cout << endl;


    it = forwardList.before_begin();
    advance(it, 2);
    forwardList.insert_after(it, 15);
    cout << "After inserting a value using insert_after(): ";
    for (int x : forwardList)
        cout << x << " ";
    cout <<endl;


    it = forwardList.before_begin();
    advance(it, 3);
    forwardList.emplace_after(it, 25);
    cout << "After inserting a value using emplace_after(): ";
    for (int x : forwardList)
        cout << x << " ";
    cout << endl;

    return 0;
}

//problem7
int main() {

   deque<int> myDeque;


    myDeque.push_back(5);


    myDeque.push_front(7);


    myDeque.push_back(10);


    myDeque.push_front(20);


    cout << "Elements of deque after insertion: ";
    for (int num : myDeque) {
        cout << num << " ";
    }
   cout << endl;


    cout << "Size of deque: " << myDeque.size() << endl;


    if (myDeque.size() >= 3) {
        cout << "Third element of deque: " << myDeque[2] << endl;
    } else {
        cout << "Deque doesn't have a third element." << endl;
    }


   cout << "First element of deque: " << myDeque.front() << endl;
    cout << "Last element of deque: " << myDeque.back() << endl;


    myDeque.pop_front();
    myDeque.pop_back();
   cout << "Deque after deleting first and last elements: ";
    for (int num : myDeque) {
        cout << num << " ";
    }
    cout << endl;

    return 0;
}

//problem8
int main() {
   vector<int> students1 = {1, 1, 0, 0};
    vector<int> sandwiches1 = {0, 1, 0, 1};
    cout << "Output: " << countStudentsCanEat(students1, sandwiches1) << endl;

    vector<int> students2 = {1, 1, 1, 0, 0, 1};
   vector<int> sandwiches2 = {1, 0, 0, 0, 1, 1};
    cout << "Output: " << countStudentsCanEat(students2, sandwiches2) << endl;

    return 0;
}

//problem9
int main() {
    int n;
    cout << "Enter the number of elements: ";
    cin >> n;

    vector<int> nums(n);
    cout << "Enter the elements of the vector: ";
    for (int i = 0; i < n; ++i) {
        cin >> nums[i];
    }

    int val;
    cout << "Enter the value to remove: ";
    cin >> val;

    int remaining = removeAndCount(nums, val);

    cout << "Output: ";
    for (int num : nums) {
       cout << num << " ";
    }
   cout << endl;

    cout << "Number of elements remaining after removal: " << remaining << endl;

    return 0;
}

//problem10

int main() {
    int n;
    cout << "Enter the number of words: ";
    cin >> n;

    vector<string> words(n);
    cout << "Enter the words: ";
    for (int i = 0; i < n; ++i) {
        cin >> words[i];
    }

    cleanNumbers(words);

   cout << "Output:" <<endl;
    for (const string& word : words) {
        cout << word << " ";
    }
    cout << endl;

    return 0;
}
