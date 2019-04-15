import java.util.HashSet;
import java.util.Set;

class Solution {

     public static void main(String[] args) {
        
        // int count = numJewelsInStones("aA","aAAbbbb");

        // System.out.println(count);

        // String out = removeParanthesis("()()");

        // System.out.println(out);

        String returnsString = toLowerCase("LOVELY");

        System.out.println(returnsString);
        
    }
    public static int numJewelsInStones(String J, String S) {

        
        Set<Character> rs = new HashSet<>();
        int count = 0;
        for(char c: J.toCharArray()){
            rs.add(c);
        }
        
        //rs.addAll(Arrays.asList(J.toCharArray()));
        
        for(char c: S.toCharArray()){
            boolean contains = rs.contains(c);
            if(contains){
                count ++;
            }
        }
        
        return count;
        
        
    }

    public static String removeParanthesis(String S){

        StringBuilder result = new StringBuilder("");
        // List<String> pairList = new ArrayList<>();
        //String returnSet = "";

        //String in = "(()())(())(()(()))";

        int open =0 , close = 0 , bIndex =0, eIndex = 0;

       // char[] carr = S.toCharArray();
        for(char c: S.toCharArray()){
            
            if(c == '(') open++;
            if(c == ')') close ++;
            if(open != close){
                eIndex++;
            } else {
                open = 0;
                close = 0;
                result.append(S.substring(bIndex+1, eIndex));
                System.out.println("inter => "+result.toString());
                eIndex++;
                bIndex = eIndex;
            }
        }

        return result.toString();


    }


    public static String toLowerCase(String str) {
        
        StringBuilder sb = new StringBuilder(str);
        char[] c = str.toCharArray();
        for(int i =0;i<c.length;i++){
            if(Character.isUpperCase(c[i])){
                char rc = Character.toLowerCase(c[i]);
                sb.replace(i,i+1,String.valueOf(rc));
            }
        }

        return sb.toString();
        
    }
}
