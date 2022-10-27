#include<bits/stdc++.h>

int sum(vector<int>&arr){
    
    int s=0;
    for(auto &x: arr)
        s += x;
    return s;
}

void solve(const vector<int>&arr, int index, vector<int>&sub, vector<vector<int>>&ans, int target)
{
    if(index == arr.size()){
        if(sum(sub)==target)
            ans.push_back(sub);
        return;
    }
    
    // pick
    sub.push_back(arr[index]);
    solve(arr, index+1, sub, ans, target);
    sub.pop_back();
    
    // don't pick
    solve(arr, index+1, sub, ans, target);
}

vector<vector<int>> findSubsetsThatSumToK(vector<int> arr, int n, int target)
{
    vector<vector<int>>ans;
    vector<int>sub;
    solve(arr, 0, sub, ans, target);
    return ans;
}