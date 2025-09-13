
![[Pasted image 20250813193641.png|500]]

```java
class Solution {

    public List<String> generateParenthesis(int n) {

        List<String> res=new ArrayList<>();

        bt(res,0, 0, "",n);

        return res;

    }

    public static void bt(List<String> res,int open, int close, String params,int n){

  

        if(params.length() == 2 * n){

            res.add(params);

            return;

        }

  

        if(open < n){

            bt(res,open+1, close, params+"(",n);

        }

  

        if(close < open){

            bt(res,open, close+1, params+")",n);

        }

    }

}
```