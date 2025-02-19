# Leetcode----1415
The K-th Lexicographical String of All Happy Strings of Length n
//code in java 
import java.util.ArrayList;
import java.util.List;

class Solution {
    private List<String> happyStrings = new ArrayList<>();
    
    public String getHappyString(int n, int k) {
        generateHappyStrings(n, "", ' ');
        return k <= happyStrings.size() ? happyStrings.get(k - 1) : "";
    }
    
    private void generateHappyStrings(int n, String current, char lastChar) {
        if (current.length() == n) {
            happyStrings.add(current);
            return;
        }
        
        for (char c : new char[]{'a', 'b', 'c'}) {
            if (c != lastChar) {
                generateHappyStrings(n, current + c, c);
            }
        }
    }
    
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.getHappyString(3, 9)); // Example test case
    }
}
