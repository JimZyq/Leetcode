# Merege Intervals
**Solution:** 1) sort the vector using the start value 2) find the overlap one by one:if it's overlapped, update the interval; otherwise new an interval.

**Time Complexity:** O(nlogn)

**Space Complexity:** O(n)


```cpp
class Solution {
public:
    struct Compare{
        bool operator() (Interval a, Interval b) {
            return a.start<b.start;
        }
    }compare;
    vector<Interval> remove_overlap (vector<Interval>& intervals){
        vector<Interval> output;
        
        output.push_back(intervals[0]);
        
        for(int i=1;i<intervals.size();i++){
            if(output.back().end < intervals[i].start) {
                output.push_back(intervals[i]);
            }
            else {
                if(output.back().end < intervals[i].end){
                    Interval tmp(output.back().start,intervals[i].end);
                    output.pop_back();
                    output.push_back(tmp);
                }
            }
        }
        return output;
    }
    vector<Interval> merge(vector<Interval>& intervals) {
        if(intervals.size()<=1) return intervals;
        //sort the intervals using the end value
        sort(intervals.begin(),intervals.begin()+intervals.size(),compare);
        //find the overlap
        return remove_overlap(intervals);

    }
};
```