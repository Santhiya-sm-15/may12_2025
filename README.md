# may12_2025
The problem that i solved today in leetcode

1.You are given an integer array digits, where each element is a digit. The array may contain duplicates.

You need to find all the unique integers that follow the given requirements:

The integer consists of the concatenation of three elements from digits in any arbitrary order.
The integer does not have leading zeros.
The integer is even.
For example, if the given digits were [1, 2, 3], integers 132 and 312 follow the requirements.

Return a sorted array of the unique integers.

Code:
class Solution {
    public int[] findEvenNumbers(int[] digits) {
        Set<Integer> l=new TreeSet<>();
        Arrays.sort(digits);
        int n=digits.length;
        for(int i=0;i<n;i++)
        {
            if(digits[i]==0) continue;
            int num=digits[i];
            for(int j=0;j<n;j++)
            {
                if(j==i) continue;
                int x=num*10+digits[j];
                for(int k=0;k<n;k++)
                {
                    if(k==i || k==j || digits[k]%2==1) continue;
                    l.add(x*10+digits[k]);
                }
            }
        }
        int[] res=new int[l.size()];
        int i=0;
        for(int x:l)
            res[i++]=x;
        return res;
    }
}
