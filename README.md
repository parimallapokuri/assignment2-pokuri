# assignment2-pokuri
# Parimalla Pokuri
###### Hyderabad is famous for my fav food which is Biryani
We have so many historical places in hyderabad. Charminar, Birla mandir, museums are located there and so many famous temples like Chilukuri **Balaji** temple, peddamma thalli gudi are located in **Hyderabad**.

---

##### Directions for going from Airport to Restaurant (Ordered List)
Rajiv Gandhi International Airport at shamshabad, hyderabad
1. From Airport there is busstop
2. Take a bus at airport
    1. Travel from shamshabad to Hi-tech City
    2. On the left side of busstop in Hi-tech City
    3. There is a metro Station, Take a ticket to falaknuma and travel in metro
    4. Come outside of the metro station at falakuma, Walk 2km straight along the main road
    5. There we can find shabad restaurant on the right side of the main road
5. There we can go and eat

##### UnOrdered List
I'll recommond these food items to others from my location
* Poori
* Idly
* Dosa
    * Onion Dosa
    * Masala Dosa
    * Ghee Dosa
    * Egg Dosa
* Semya upma
* Pongal
* Biryani
    * Prawns Biryani
    * Chicken Biryani
    * Mutton Biryani
    * Muglai Biryani
    * Veg Biryani
    
[Click here to know about me](https://github.com/parimallapokuri/assignment2-pokuri/blob/main/AboutMe.md)

---

# About Sports
I would like recommond the following sports which I like most are Badminton, Cricket, Football, valley Ball.
| Sport name |  Location  | Payable Amount |
| ---------- | ---------- | -------------- |
| Badminton  | Hyderabad  |   $10          |
| Cricket    | Guntur     |   $40          |
| Football   | Vijayawada |   $30          |
| valley Ball| Ongole     |   $20          |

---

# Pithy Quotes

> 1. Good, better, best. Never let it rest. 'Til your good is better and your better is best'.
Author: *St. Jerome*
> 2. Don't watch the clock; do what it does. Keep going.
Author: *Sam Levenson*

---

# Dynamic Programming
###### Dynamic Programming from other source 
>Dynamic Programming (commonly referred to as DP) is an algorithmic technique for solving a problem by recursively breaking it down into simpler subproblems and using the fact that the optimal solution to the overall problem depends upon the optimal solution to it’s individual subproblems.

Go to the source of Dynamic Programming -> <https://www.interviewbit.com/courses/programming/topics/dynamic-programming/#:~:text=Dynamic%20Programming%20(commonly%20referred%20to,solution%20to%20it's%20individual%20subproblems.>

###### Dynamic Programming from CP-Algorithms 
```
int m, n;
vector<long long> dp_before(n), dp_cur(n);

long long C(int i, int j);

// compute dp_cur[l], ... dp_cur[r] (inclusive)
void compute(int l, int r, int optl, int optr) {
    if (l > r)
        return;

    int mid = (l + r) >> 1;
    pair<long long, int> best = {LLONG_MAX, -1};

    for (int k = optl; k <= min(mid, optr); k++) {
        best = min(best, {(k ? dp_before[k - 1] : 0) + C(k, mid), k});
    }

    dp_cur[mid] = best.first;
    int opt = best.second;

    compute(l, mid - 1, optl, opt);
    compute(mid + 1, r, opt, optr);
}

int solve() {
    for (int i = 0; i < n; i++)
        dp_before[i] = C(0, i);

    for (int i = 1; i < m; i++) {
        compute(0, n - 1, 0, n - 1);
        dp_before = dp_cur;
    }

    return dp_before[n - 1];
}
```

Quick link for source code -> <https://cp-algorithms.com/dynamic_programming/divide-and-conquer-dp.html>