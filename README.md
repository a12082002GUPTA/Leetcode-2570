# Leetcode-2570

# C++

class Solution {
public:
    vector<vector<int>> mergeArrays(vector<vector<int>>& nums1, vector<vector<int>>& nums2) {
        int m=nums1.size();
        int n=nums2.size();
        vector<vector<int>>v;
        int i=0,j=0;
        while(i<m&&j<n)
        {
            if(nums1[i][0]==nums2[j][0])
            {
                v.push_back({nums1[i][0],nums1[i][1]+nums2[j][1]});
                i++;
                j++;
            }
             else if(nums1[i][0]<nums2[j][0])
            {
                v.push_back({nums1[i][0],nums1[i][1]});
                i++;
            }
            else
             {
                v.push_back({nums2[j][0],nums2[j][1]});
                j++;
            }
        }
        while(i<m)
        {
             v.push_back({nums1[i][0],nums1[i][1]});
             i++;
        }
        while(j<n)
        {
             v.push_back({nums2[j][0],nums2[j][1]});
             j++;
        }
        return v;
    }
};

# Java

import java.util.*;

class Solution {
    public int[][] mergeArrays(int[][] nums1, int[][] nums2) {
        int m = nums1.length, n = nums2.length;
        List<int[]> result = new ArrayList<>();
        int i = 0, j = 0;

        while (i < m && j < n) {
            if (nums1[i][0] == nums2[j][0]) {
                result.add(new int[]{nums1[i][0], nums1[i][1] + nums2[j][1]});
                i++;
                j++;
            } else if (nums1[i][0] < nums2[j][0]) {
                result.add(new int[]{nums1[i][0], nums1[i][1]});
                i++;
            } else {
                result.add(new int[]{nums2[j][0], nums2[j][1]});
                j++;
            }
        }

        while (i < m) {
            result.add(new int[]{nums1[i][0], nums1[i][1]});
            i++;
        }

        while (j < n) {
            result.add(new int[]{nums2[j][0], nums2[j][1]});
            j++;
        }

        // Convert List<int[]> to int[][]
        return result.toArray(new int[result.size()][]);
    }
}

# Python

from typing import List

class Solution:
    def mergeArrays(self, nums1: List[List[int]], nums2: List[List[int]]) -> List[List[int]]:
        m, n = len(nums1), len(nums2)
        result = []
        i, j = 0, 0

        while i < m and j < n:
            if nums1[i][0] == nums2[j][0]:
                result.append([nums1[i][0], nums1[i][1] + nums2[j][1]])
                i += 1
                j += 1
            elif nums1[i][0] < nums2[j][0]:
                result.append([nums1[i][0], nums1[i][1]])
                i += 1
            else:
                result.append([nums2[j][0], nums2[j][1]])
                j += 1

        while i < m:
            result.append([nums1[i][0], nums1[i][1]])
            i += 1

        while j < n:
            result.append([nums2[j][0], nums2[j][1]])
            j += 1

        return result
