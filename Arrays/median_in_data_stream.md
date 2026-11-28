# median in a data stream

[Problem Link](https://takeuforward.org/practice/dsa/find-median-from-data-stream)


```
class MedianFinder {
    List<Integer> li;
    public MedianFinder() {
    li=new ArrayList<>();
    }

    public void addNum(int num) {
      li.add(num);
      Collections.sort(li);
    }

    public double findMedian() {
     int mid=li.size()/2;
     if(li.size()%2==1){
        return li.get(mid);
     }
     int num1=li.get(mid);
     int num2=li.get(mid-1);
     double median=(double)(num1+num2)/2;
      return median;
    }

}
```
