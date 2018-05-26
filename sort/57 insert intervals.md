# insert Intervals
**Solution:** update the newInterval with the intervals, and insert it into the output

**Time Complexity:** O(n)

**Space Complexity:** O(n)


```cpp
class Solution {
public:    
    vector<Interval> insert(vector<Interval>& intervals, Interval newInterval) {
        if(intervals.size()==0){
            intervals.push_back(newInterval);
            return intervals;
        }
        vector<Interval> output;
        int i;
        if(newInterval.start>intervals.back().end){
            intervals.push_back(newInterval);
            return intervals;
        }
        for(i=0;i<intervals.size();i++){
            if(newInterval.start > intervals[i].end){
                output.push_back(intervals[i]);
            }
            else if(newInterval.end < intervals[i].start){
                break;
            }
            else{
                newInterval.start = min(newInterval.start,intervals[i].start);
                newInterval.end = max(newInterval.end, intervals[i].end);
            }
        }
        output.push_back(newInterval);
        if(i == intervals.size()-1) {
            output.push_back(intervals[i]);
            return output;
        }
        for(i;i<intervals.size();i++){
            output.push_back(intervals[i]);
        }
        return output;
    }
};
```
