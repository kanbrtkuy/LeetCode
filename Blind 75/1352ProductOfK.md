<h1>Solve</h1>

```java
class ProductOfNumbers {

    List<Integer> list;
    int pre;
    public ProductOfNumbers() {

        list = new ArrayList<>();
        pre = 1;
        
    }
    
    public void add(int num) {
        if(num <= 0) {
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
            return pre / list.get((list.size() - k));
        }
        
    }
}
```
