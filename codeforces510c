#include <bits/stdc++.h>
using namespace std;

vector<int> adj[26];
int indegree[26];

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int n;
    cin >> n;

    vector<string> s(n);

    for (int i = 0; i < n; i++)
        cin >> s[i];

    for (int i = 0; i < n - 1; i++) {

        string a = s[i];
        string b = s[i + 1];

        int len = min(a.size(), b.size());
        bool found = false;

        for (int j = 0; j < len; j++) {

            if (a[j] != b[j]) {

                adj[a[j] - 'a'].push_back(b[j] - 'a');
                found = true;
                break;
            }
        }

        if (!found && a.size() > b.size()) {
            cout << "Impossible\n";
            return 0;
        }
    }

    for (int i = 0; i < 26; i++) {

        sort(adj[i].begin(), adj[i].end());
        adj[i].erase(unique(adj[i].begin(), adj[i].end()), adj[i].end());

        for (int v : adj[i])
            indegree[v]++;
    }

    queue<int> q;

    for (int i = 0; i < 26; i++)
        if (indegree[i] == 0)
            q.push(i);

    string ans;

    while (!q.empty()) {

        int u = q.front();
        q.pop();

        ans += char(u + 'a');

        for (int v : adj[u]) {

            indegree[v]--;

            if (indegree[v] == 0)
                q.push(v);
        }
    }

    if (ans.size() != 26)
        cout << "Impossible\n";
    else
        cout << ans << "\n";

    return 0;
}
