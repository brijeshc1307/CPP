Write a C++ program to store integers 1–10 in Arrray and remove element 5 from array and print the array, same as vector, map, list, set, queue, stack. usong cpp
---

## ✅ 1. `array` – Manual Removal of 5

```cpp
#include <iostream>
#include <array>
using namespace std;

int main() {
    array<int, 10> arr;
    cout << "Enter 10 integers: ";
    for (int i = 0; i < 10; ++i)
        cin >> arr[i];

    // Manual removal
    int newSize = 0;
    for (int i = 0; i < 10; ++i)
        if (arr[i] != 5)
            arr[newSize++] = arr[i];

    cout << "Array after removing 5: ";
    for (int i = 0; i < newSize; ++i)
        cout << arr[i] << " ";
    cout << "\n";
    return 0;
}
```
Or
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[10];
    int n = 10;

    // store numbers 1 to 10
    for(int i = 0; i < n; i++) {
        arr[i] = i + 1;
    }

    // manually remove element 5
    for(int i = 0; i < n; i++) {
        if(arr[i] == 5) {
            // shift elements left
            for(int j = i; j < n - 1; j++) {
                arr[j] = arr[j + 1];
            }
            n--; // reduce size after removal
            break; // stop after first removal
        }
    }

    // print array after removal
    cout << "Array after removing 5: ";
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```


---

## ✅ 2. `vector` – Manual Removal

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
   vector<int> vec(10);
    cout << "Enter 10 integers: ";
    for (int i = 0; i < 10; ++i)
        cin >> vec[i];

    // Manual removal
    int newSize = 0;
    for (int i = 0; i < vec.size(); ++i){
        if (vec[i] != 5){
            vec[newSize] = vec[i];
            newSize++;
            }
        }

    cout << "Vector after removing 5: ";
    for (int i = 0; i < newSize; ++i)
        cout << vec[i] << " ";
    cout << "\n";
    return 0;
}
```
Output
```
Input: 1 5 3 4 5 6 7 5 8 9
Output: 1, 3, 4, 6, 7, 8, 9

Input: 1 2 3 4 5 6 7 8 9 10 
Output: 1 2 3 4 6 7 8 9 10 
```

---

## ✅ 3. `map` – Manual Removal of value `5`

```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<int, int> mp;
    cout << "Enter 10 integers: ";
    for (int i = 0; i < 10; ++i) {
        int x; cin >> x;
        mp[i] = x;
    }

    // Manual removal: copy valid entries to new map
    map<int, int> newMap;
    int newKey = 0;
    for (int i = 0; i < 10; ++i)
        if (mp[i] != 5)
            newMap[newKey++] = mp[i];

    cout << "Map after removing value 5: ";
    for (int i = 0; i < newKey; ++i)
        cout << newMap[i] << " ";
    cout << "\n";
    return 0;
}
```

---

## ✅ 4. `list` – Manual Removal

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<int> lst;
    cout << "Enter 10 integers: ";
    for (int i = 0; i < 10; ++i) {
        int x; cin >> x;
        lst.push_back(x);
    }

    // Manual removal: recreate new list
    list<int> newList;
    for (auto it = lst.begin(); it != lst.end(); ++it)
        if (*it != 5)
            newList.push_back(*it);

    cout << "List after removing 5: ";
    for (auto it = newList.begin(); it != newList.end(); ++it)
        cout << *it << " ";
    cout << "\n";
    return 0;
}
```

---

## ✅ 5. `set` – Manual Removal

```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    set<int> st;
    cout << "Enter 10 integers: ";
    for (int i = 0; i < 10; ++i) {
        int x; cin >> x;
        st.insert(x);
    }

    // Manual rebuild
    set<int> newSet;
    for (auto it = st.begin(); it != st.end(); ++it)
        if (*it != 5)
            newSet.insert(*it);

    cout << "Set after removing 5: ";
    for (auto it = newSet.begin(); it != newSet.end(); ++it)
        cout << *it << " ";
    cout << "\n";
    return 0;
}
```

---

## ✅ 6. `queue` – Manual Removal

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<int> q;
    cout << "Enter 10 integers: ";
    for (int i = 0; i < 10; ++i) {
        int x; cin >> x;
        q.push(x);
    }

    // Manual filtering
    queue<int> filtered;
    while (!q.empty()) {
        int val = q.front(); q.pop();
        if (val != 5)
            filtered.push(val);
    }

    cout << "Queue after removing 5: ";
    while (!filtered.empty()) {
        cout << filtered.front() << " ";
        filtered.pop();
    }
    cout << "\n";
    return 0;
}
```

---

## ✅ 7. `stack` – Manual Removal

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<int> stk;
    cout << "Enter 10 integers: ";
    for (int i = 0; i < 10; ++i) {
        int x; cin >> x;
        stk.push(x);
    }

    // Manual filtering: remove 5
    stack<int> temp;
    while (!stk.empty()) {
        int val = stk.top(); stk.pop();
        if (val != 5)
            temp.push(val);
    }

    // Reverse again
    stack<int> finalStack;
    while (!temp.empty()) {
        finalStack.push(temp.top());
        temp.pop();
    }

    cout << "Stack after removing 5: ";
    while (!finalStack.empty()) {
        cout << finalStack.top() << " ";
        finalStack.pop();
    }
    cout << "\n";
    return 0;
}
```

---

## ✅ Summary

| Container | STL Used For | Removal Done By             |
| --------- | ------------ | --------------------------- |
| `array`   | Fixed-size   | Shifting elements manually  |
| `vector`  | Declaration  | Index overwrite manually    |
| `map`     | Declaration  | Rebuilding map manually     |
| `list`    | Declaration  | Rebuild using iterators     |
| `set`     | Declaration  | Rebuild into new set        |
| `queue`   | Declaration  | Rebuild queue manually      |
| `stack`   | Declaration  | Filter and reverse manually |

---

Let me know if you want this in one combined program or need the same logic for other data types!
