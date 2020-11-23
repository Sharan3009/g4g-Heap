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
}
```
