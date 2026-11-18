#include <iostream>
#include <algorithm>
#include <climits>
#include <chrono>
using namespace std;

const int N = 4;

int cost[N][N] = {
    {0, 10, 15, 20},
    {10, 0, 35, 25},
    {15, 35, 0, 30},
    {20, 25, 30, 0}
};

int dp[1 << N][N];

int tsp(int mask, int pos) {

    // All cities visited
    if (mask == (1 << N) - 1) {
        return cost[pos][0];
    }

    if (dp[mask][pos] != -1) {
        return dp[mask][pos];
    }

    int ans = INT_MAX;

    // Visit unvisited cities
    for (int city = 0; city < N; city++) {

        if ((mask & (1 << city)) == 0) {

            int newCost = cost[pos][city] +
                tsp(mask | (1 << city), city);

            ans = min(ans, newCost);
        }
    }

    return dp[mask][pos] = ans;
}

int main() {

    fill(&dp[0][0], &dp[0][0] + (1 << N) * N, -1);

    // Start timer
    auto start = chrono::high_resolution_clock::now();

    int minimumCost = tsp(1, 0);

    // Stop timer
    auto end = chrono::high_resolution_clock::now();

    // Calculate execution time
    chrono::duration<double, milli> executionTime = end - start;

    cout << "Minimum Travelling Cost: "
         << minimumCost << endl;

    cout << "Execution Time: "
         << executionTime.count()
         << " milliseconds" << endl;

    return 0;
}
