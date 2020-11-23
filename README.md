# Heap hands-on
```
import java.util.*;
class Heap {
  ArrayList<Integer> al = new ArrayList<>();
  
  public int size(){
    return al.size();
  }
  
  public int left(int i){
    int l = 2*i+1;
    return l;
  }
  
  public int right(int i){
    int r = 2*i+2;
    return r;
  }
  
  public int parent(int i){
    return (i-1)/2;
  }
  
  public void insert(int val){
    al.add(val);
    for(int i=size()-1;i!=0 && al.get(parent(i))>al.get(i);i=parent(i)){
      swap(i,parent(i));
    }
  }
  
  public void heapify(int i){
    int l = left(i);
    int r = right(i);
    int smallest = i;
    if(l<size() && al.get(l)<al.get(i)){
      smallest = l;
    }
    if(r<size() && al.get(r)<al.get(smallest)){
      smallest = r;
    }
    if(smallest!=i){
      swap(smallest,i);
      heapify(smallest);
    }
  }
  
  public int extractMin(){
    if(size()==0){
      return Integer.MAX_VALUE;
    }
    if(size()==1){
      return al.remove(0);
    }
    swap(0,size()-1);
    int extractedMin = al.remove(size()-1);
    heapify(0);
    return extractedMin;
  }
  
  public void decreaseKey(int i, int v){
    if(i>=size()){
      return;
    }
    al.set(i,v);
    while(i!=0 && al.get(parent(i)>al.get(i))){
      swap(i,parent(i));
      i = parent(i);
    }
  }
  
  public void deleteKey(int i){
    if(i>=size()) return;
    decreaseKey(i,Integer.MIN_VALUE);
    heapify(0);
  }
  
  public void buildHeap(){
    for(int i=parent(size()-1);i>=0;i--){
      heapify(i);
    }
  }
  
  private void swap(int index1, int index2){
    int temp = al.get(index1);
    al.set(index1,al.get(index2));
    al.set(index2,temp);
  }
}
```
