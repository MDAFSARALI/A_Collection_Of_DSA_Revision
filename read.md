# Collection of DSA Revision Notes :)

## Problem 22 : 

```
5 5 5 5 5 5 5 5 5 
5 4 4 4 4 4 4 4 5 
5 4 3 3 3 3 3 4 5 
5 4 3 2 2 2 3 4 5 
5 4 3 2 1 2 3 4 5 
5 4 3 2 2 2 3 4 5 
5 4 3 3 3 3 3 4 5 
5 4 4 4 4 4 4 4 5 
5 5 5 5 5 5 5 5 5
```
[QUESTION LINK :](https://takeuforward.org/plus/data-structures-and-algorithm/beginner-problems/patterns/pattern-22)

> CODE SOLUTION 

## Approach for `pattern22`

- Yeh function ek `2*n-1` size ka square pattern print karta hai.
- Har cell ke liye, `i` aur `j` ke basis par 4 distances calculate hote hain: top, bottom, left, aur right.
- Inn distances ka minimum leke, `n - min()` se jo value aati hai, woh us cell mein print hoti hai.
- Har row ke baad `endl` se new line print hoti hai.


```C++
void pattern22(int n) {
        for(int i=0;i<2*n-1;i++){
            for(int j=0;j<2*n-1;j++){
                int top=i,bottom=j;
                int left=(2*n-2)-i,right=(2*n-2)-j;
                cout<<n-(min(min(top,bottom),min(right,left)))<<" ";
            }
            cout<<endl;
        }
    }
```
-----------------------------------------------------------

## Problem 17 : 

```
Given an integer n. You need to recreate the pattern given below for any value of N. Let's say for N = 5, the pattern should look like as below:

    A
   ABA
  ABCBA
 ABCDCBA
ABCDEDCBA


Print the pattern in the function given to you.
```
[QUESTION LINK :](https://takeuforward.org/plus/data-structures-and-algorithm/beginner-problems/patterns/pattern-17)

> CODE SOLUTION 

## Approach for `pattern17`

- `pattern17` function ek pyramid shape ka pattern print karta hai.
- Pehle outer loop (`i`) se rows create karte hain, jahan `n` rows tak chalega.
- Har row ke liye, inner loop (`j`) spaces print karta hai, jisse pyramid shape ban sake.
- Character `ch` ko 'A' se initialize karte hain.
- `mid` variable se current row ka middle index calculate karte hain.
- Teesra loop (`k`) se characters print karte hain:
  - Agar `k` middle index se pehle ya uske barabar hai, toh character `ch` ko increment karte hain.
  - Agar `k` middle index ke baad hai, toh character `ch` ko decrement karte hain.
- Har row ke baad `endl` se new line print hota hai.



```C++
class Solution {
public:
    void pattern17(int n) {
        for(int i=0;i<=n-1;i++){
            for(int j=1;j<=n-i-1;j++){
                cout<<" ";
            }
            char ch='A';
            int mid= (2* i+1)/2;
            for(int k=1;k<=2*i+1;k++){
                cout<<ch;
                if (k<=mid) ch++;
                else ch--;
            }
            cout<<endl;
        }
    }
};
```
----------------
## secondMostFrequentElement : 
```
Given an array of n integers, find the second most frequent element in it. If there are multiple elements that appear a maximum number of times, find the smallest of them. If second most frequent element does not exist return -1
```
[QUESTION LINK :](https://takeuforward.org/plus/data-structures-and-algorithm/beginner-problems/basic-hashing/second-highest-occurring-element)

> CODE SOLUTION 
## Approach for `secondMostFrequentElement`

- Pehle `maxValue` find karte hain jo array `nums` ka maximum element hota hai.
- Ek `hash` array banate hain jo har element ka frequency store karta hai.
- `FirstHigestOcc` aur `SecHigestOcc` ko use karke first aur second most frequent element ki frequency track karte hain.
- Har element ke frequency ke hisaab se, agar woh element first se zyada frequent ho toh usse update karte hain aur pehle wala second highest ban jata hai.
- End mein second most frequent element return karte hain.

```C++
 int secondMostFrequentElement(vector<int>& nums) {
        int n=nums.size();
        int maxValue=nums[0];
        for(int i=0;i<n;i++){
            maxValue=max(maxValue,nums[i]);
        }
        vector<int> hash(maxValue+1,0);
        for(int i=0;i<n;i++){
            hash[nums[i]]++;
        }
        int FirstHigestOcc=0,FirstHighestValue=-1;
        int SecHigestOcc=0,SecHighestValue=-1;
        for(int i=0;i<=maxValue;i++){
            if(hash[i]>FirstHigestOcc){
                SecHigestOcc=FirstHigestOcc;
                SecHighestValue=FirstHighestValue;
                FirstHigestOcc=hash[i];
                FirstHighestValue=i;
            }
            else if(hash[i]==FirstHigestOcc){
                FirstHighestValue=min(FirstHighestValue,i);
            }
            else if (hash[i] > SecHigestOcc){
                SecHigestOcc=hash[i];
                SecHighestValue=i;
            }
            else if (hash[i] == SecHigestOcc){
                SecHighestValue=min(SecHighestValue,i);
            }
        }
        return SecHighestValue;
    }
```
---

## Largest odd number in a string : 
```
Given a string s, representing a large integer, the task is to return the largest-valued odd integer (as a string) that is a substring of the given string s.

The number returned should not have leading zero's. But the given input string may have leading zero.
```
[QUESTION LINK :](https://takeuforward.org/plus/data-structures-and-algorithm/beginner-problems/basic-strings/largest-odd-number-in-a-string)

> CODE SOLUTION 
## Approach for `largeOddNum`

- Pehle string `s` ka size `n` lete hain aur last odd digit ka index find karte hain.
- Last se shuru karke, har digit check karte hain jab tak koi odd digit nahi milti. Milte hi uska index `ind` store karte hain.
- Phir, string ke starting se 0s ko skip karte hain jab tak hum odd digit tak nahi pahunch jate.
- Finally, `s` ka substring return karte hain jo first non-zero se leke last odd digit tak hota hai.

```C++
string largeOddNum(string& s){
      int n=s.size();
      int ind=-1;
      for(int i=n;i>0;i--){
        if((s[i]-'0')%2!=0) {
            ind=i ;
            break;
        }
      }
      int i=0;
        while(i<=ind && s[i]=='0') i++;
        return s.substr(i,ind-i+1);
      
    }
```
---


## Longest common prefix : 
```
Given a string s, representing a large integer, the task is to return the largest-valued odd integer (as a string) that is a substring of the given string s.

The number returned should not have leading zero's. But the given input string may have leading zero.
```
[QUESTION LINK :](https://takeuforward.org/plus/data-structures-and-algorithm/beginner-problems/basic-strings/longest-common-prefix)

> CODE SOLUTION 

## Approach for `longestCommonPrefix`

- Pehle `str` array ko sort karte hain, jisse first aur last string lexicographically sabse alag ho jati hain.
- Phir, pehli aur aakhri string ke beech common prefix ko compare karte hain.
- Ek loop mein dono strings ke corresponding characters ko check karte hain jab tak common characters milte hain.
- Jaise hi koi character alag hota hai, loop ko break karke common prefix ko `ans` mein store karte hain aur return karte hain.


```C++
string longestCommonPrefix(vector<string>& str){
			int lengthOfStringsArray=str.size();
			sort(str.begin(),str.end());
			string firstStr1=str[0];
			string secondStr2=str[lengthOfStringsArray-1];
			string ans="";
			for(int i=0;i<min(firstStr1.size(),secondStr2.size());i++){
				if(firstStr1[i]!=secondStr2[i]) break;
				else ans+=firstStr1[i];
			}
			return ans;
		}
```
---


## Isomorphic string : 
```
Given two strings s and t, determine if they are isomorphic. Two strings s and t are isomorphic if the characters in s can be replaced to get t.



All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.


Example 1
Input : s = "egg" , t = "add"

Output : true

Explanation : The 'e' in string s can be replaced with 'a' of string t.

The 'g' in string s can be replaced with 'd' of t.

Hence all characters in s can be replaced to get t.
```
[QUESTION LINK :](https://takeuforward.org/plus/data-structures-and-algorithm/beginner-problems/basic-strings/isomorphic-string)

> CODE SOLUTION 

## Approach for `isomorphicString`

- Pehle check karte hain ki dono strings `s` aur `t` ka size same hai ya nahi. Agar alag hai, toh return `false`.
- `Smap` aur `Tmap` arrays ko use karke, har character ka mapping store karte hain.
- Loop ke through, har position par `s[i]` aur `t[i]` ko compare karte hain. Agar unka previous mapping same nahi hai, toh return `false`.
- Har character ke liye mapping index update karte hain, aur agar saare characters match ho jate hain, toh return `true`.



```C++
bool isomorphicString(string s, string t) {
    	if(s.size()!=t.size()) return false;
        int n=s.size();
         int Smap[256]={0};
         int Tmap[256]={0};
         for(int i=0;i<n;i++){
            if(Smap[s[i]]!=Tmap[t[i]]) return false;

            Smap[s[i]]=i+1;
            Tmap[t[i]]=i+1;
         }
        return true;
    }
```
---



## Rotate string : 
```
Given two strings s and goal, return true if and only if s can become goal after some number of shifts on s.

A shift on s consists of moving the leftmost character of s to the rightmost position.

For example, if s = "abcde", then it will be "bcdea" after one shift.


Example 1
Input : s = "abcde" , goal = "cdeab"

Output : true

Explanation : After performing 2 shifts we can achieve the goal string from string s.

After first shift the string s is => bcdea

After second shift the string s is => cdeab.
```
[QUESTION LINK :](https://takeuforward.org/plus/data-structures-and-algorithm/beginner-problems/basic-strings/rotate-string)

> CODE SOLUTION 

## Approach for `rotateString`

- Pehle check karte hain ki `s` aur `goal` strings ka size same hai ya nahi. Agar alag hai, toh return `false`.
- Har possible rotation ke liye, loop chalayenge jo `s` ko shift karta hai.
- `s` ka substring banate hain jisme current index se lekar last tak ka hissa `rotated` string mein add karte hain, aur phir uske pehle wale part ko jodte hain.
- Har rotation ke baad check karte hain ki kya `goal` string `rotated` ke barabar hai. Agar match ho jata hai, toh return `true`.
- Agar koi rotation match nahi karta, toh return `false`.




```C++
class Solution{	
	public:
		bool rotateString(string& s,string& goal){
			int sizeOfS=s.size();
			int sizeOfGoal=goal.size();
			if(sizeOfS!=sizeOfGoal) return false;
			string doubledS=s+s;
			return doubledS.find(goal)!=string::npos;
		}
};




class Solution{	
	public:
		bool rotateString(string& s,string& goal){
			int sizeOfS=s.size();
			int sizeOfGoal=goal.size();
			if(sizeOfS!=sizeOfGoal) return false;
			for(int i=0;i<sizeOfGoal;i++){
				string rotated=s.substr(i)+s.substr(0,i);
				if(goal==rotated) return true;
			}
			return false;
		}
};
```
---

## Sort characters by frequency : 
```
You are given a string s. Return the array of unique characters, sorted by highest to lowest occurring characters.

If two or more characters have same frequency then arrange them in alphabetic order.


Example 1
Input : s = "tree"

Output : ['e', 'r', 't' ]

Explanation : The occurrences of each character are as shown below :

e --> 2

r --> 1

t --> 1.

The r and t have same occurrences , so we arrange them by alphabetic order.
```
[QUESTION LINK :](https://takeuforward.org/plus/data-structures-and-algorithm/beginner-problems/basic-strings/sort-characters-by-frequency)

> CODE SOLUTION 

## Approach for `frequencySort`

- Pehle, `freq` naam ka array banate hain jo 26 characters (a se z) ka frequency track karega. Har character ka initial frequency 0 hota hai.
- Loop chalayenge `s` string par aur har character ka frequency update karte hain.
- Phir `freq` array ko sort karte hain using a custom comparator function:
  - Comparator function `comperator` pehle frequency check karta hai. Agar frequency same hai, toh characters ko ascending order mein sort karta hai.
- Finally, `ans` vector mein un characters ko add karte hain jinka frequency 0 se zyada hai.
- `ans` vector return karte hain jo sorted characters ki list hoti hai.


```C++
class Solution{	
        static bool comperator(pair<int,char>p1,pair<int,char>p2){
            if(p1.first>p2.first) return true;
            if(p1.first<p2.first) return false;;
            return p1.second < p2.second;
        }
public:
		vector<char> frequencySort(string& s){
			pair<int , char> freq[26];
            for(int i=0;i<26;i++){
                freq[i]={0,i+'a'};
            }
            for(char ch:s){
                freq[ch-'a'].first++;
            }
            sort(freq , freq+26 , comperator);
            vector<char> ans;
            for(int i=0;i<26;i++){
                if(freq[i].first>0) ans.push_back(freq[i].second);
            }
            return ans;
		}
};
```
---



## Sum of array elements : 
```
Given an array nums, find the sum of elements of array using recursion.


Example 1
Input : nums = [1, 2, 3]

Output : 6

Explanation : The sum of elements of array is 1 + 2 + 3 => 6.
```
[QUESTION LINK :](https://takeuforward.org/plus/data-structures-and-algorithm/beginner-problems/basic-recursion/sum-of-array-elements)

> CODE SOLUTION 

## Approach for `arraySum`

- `arraySum` function check karta hai ki `nums` vector khali hai ya nahi. Agar khali hai, toh return `0`.
- `sum` function ko call karte hain, jo recursion ka istemal karke vector ke elements ka sum calculate karta hai.
- `sum` function mein:
  - Pehle check karte hain ki `i` index vector ke size se zyada hai ya nahi. Agar zyada hai, toh `0` return karte hain.
  - Agar valid index hai, toh current element (`nums[i]`) ko sum karte hain aur next index (`i+1`) ke liye function ko recursively call karte hain.
- Ye process tab tak chalta hai jab tak sab elements ka sum nahi ho jata, aur final result return hota hai.

```C++
class Solution{	
	public:
		int sum(vector<int>&nums,int i){
			while(i>=nums.size()){
				return 0;
			}
			return nums[i]+sum(nums,i+1);
		}
		int arraySum(vector<int>& nums){
			if(nums.size()==0) return 0;
			int ans=sum(nums,0);
			return ans;
		}
};
```
---


## SORTING TECHNIQUES :)