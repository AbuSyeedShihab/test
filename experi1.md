# Experiment No: 01
## Experiment Name:: Implementation of kNN algorithm to find the class of a given point

**Theory:**
A basic machine learning approach called k-Nearest Neighbors (kNN) is used to categorization problems. It works on the basis of the proximity principle, which states that an unknown data point's class may be inferred from the classes of its k closest neighbors. The straight-line distance between each point in the dataset and the supplied point is determined using kNN using the Euclidean distance as the distance metric. The method then chooses the k data points that have the least distances between them, and based on the majority class among these neighbors, it assigns the class label to the supplied point. Because kNN can generate predictions without explicit training, it is a simple and flexible solution for various classification issues.

**Code:**
```cpp
#include<bits/stdc++.h>
using namespace std;

struct points {

 int x,y,cls;

};

struct dist {

 double D;
 int cls;

};



int distance(int x1,int y1,int x2,int y2){
    return sqrt((x1-x2)*(x1-x2)-(y1-y2)*(y1-y2));
}

int main(){
    int sza,szb,sz;
    cout<<"Enter number of points in class A:   ";
    cin>>sza;
    cout<<"Enter number of points in class B:   ";
    cin>>szb;
    sz=sza+szb;
    vector<points> List(sz);
    cout<<"Enter The Co-ordinates of class A: \n";
    for(int i=0;i<sza;i++){
        cin>>List[i].x>>List[i].y;
        List[i].cls=0;
    }
    cout<<"Enter The Co-ordinates of class B: \n";
    for(int i=sza;i<sz;i++){
        cin>>List[i].x>>List[i].y;
        List[i].cls=1;
    }
    cout<<"Enter target Co-ordinate:\n";
    pair<int,int> tar;
    cin>>tar.first>>tar.second;

    vector<dist> List2(sz);
    for(int i=0;i<sz;i++){
        List2[i].D = distance(tar.first,tar.second,List[i].x,List[i].y);
        List2[i].cls = List[i].cls;
    }

    for(int i=0;i<sz;i++){
        for(int j=0;j+1<sz;j++){
            if(List2[j].D>List2[j+1].D){
                swap(List2[j].D,List2[j+1].D);
                swap(List2[j].cls,List2[j+1].cls);
            }
        }
    }
    cout<<"Enter value of K:\n";
    int k,cls0=0,cls1=0;
    cin>>k;
    for(int i=0;i<k;i++){
        if(List2[i].cls==0){
            cls0++;
        }
        else cls1++;
    }
    cout<<"The target point belongs to class ";
    if(cls1>cls0){
        cout<<"B\n";
    }
    else cout<<"A\n";
}
```
**Output:**
```
Enter number of points in class A:   3
Enter number of points in class B:   4
Enter The Co-ordinates of class A:
1 2
3 4
0 3
Enter The Co-ordinates of class B:
6 7
5 5
8 9
10 12
Enter target Co-ordinate:
6 6
Enter value of K:
5
The target point belongs to class B
```

**Discussion:**
In this experiment, we created two clusters of two classes and used kNN to find the class of the target point. The structure was used to create points, which had the coordinates and class of the point, and distances from the target point along with the corresponding class. Then bubble sort was used to sort the distances along with classes, and then the number of closest points from all the points were counted. So the larger number of the count points to the class of the target point.

**Conclusion::**
All the codes associated with the experiment ran without any issues and we were able to find the class accurately.

