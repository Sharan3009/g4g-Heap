# Heap hands-on
```
class Heap {
  ArrayList<Integer> al = new ArrayList<>();
  
  public int size(){
    return al.size();
  }
  
  public int left(int i){
    int l = 2*i+1;
    if(l>size()){
      return -1;
    }
    return l;
  }
  
  public int right(int i){
    int r = 2*i+2;
    if(r>size()){
      return -1;
    }
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
  
  private void swap(int index1, int index2){
    int temp = al.get(index1);
    al.set(index1,al.get(index2));
    al.set(index2,temp);
  }
}
```
