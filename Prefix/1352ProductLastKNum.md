```java
class ProductOfNumbers {

    List<Integer> list;
    int pre;

    public ProductOfNumbers() {
        list = new ArrayList<>();
        pre = 1;
    }
    
    public void add(int num) {
        if(num == 0) {
            list = new ArrayList<>();
            pre = 1;
        } else {
            list.add(pre);
            pre *= num;
        }
        
    }
    
    public int getProduct(int k) {
        if(k > list.size()) {
            return 0;
        } else {
            return pre/list.get(list.size()-k);
        }
        
    }
}
```

```java
class ProductOfNumbers {

    private List<Integer> time;

    public ProductOfNumbers() {

        time = new ArrayList<>();
        
    }
    
    public void add(int num) {

        if(time.size() == 0) {
            time.add(num);
        } else {
            time.add(time.get(time.size()-1)*num);
        }

        if(num == 0) time.clear();
    }
    
    public int getProduct(int k) {

        if(k > time.size()) return 0;

        if(k == time.size()) return time.get(time.size() - 1);

        return time.get(time.size()-1)/time.get(time.size()-1-k);
        
    }
}
```
