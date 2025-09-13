```java
class Solution {

    public List<String> letterCombinations(String digits) {

        List<String> res = new ArrayList<>();

        if (digits == null || digits.length() == 0) {

            return res;

        }

        Map<Character, String> map = new HashMap<>();

        map.put('2', "abc");

        map.put('3', "def");

        map.put('4', "ghi");

        map.put('5', "jkl");

        map.put('6', "mno");

        map.put('7', "pqrs");

        map.put('8', "tuv");

        map.put('9', "wxyz");

  

        bt(map, digits, res, new StringBuilder(), 0);

        return res;

    }

  

    public static void bt(Map<Character, String> map, String digits, List<String> res, StringBuilder sb, int idx) {

  

        if (digits.length() == sb.length()) {

            res.add(sb.toString());

            return;

        }

  

        String letters = map.get(digits.charAt(idx));

        for (char c : letters.toCharArray()) {

            sb.append(c);

            bt(map, digits, res, sb, idx + 1);

            sb.deleteCharAt(sb.length() - 1);

        }

    }

}
```