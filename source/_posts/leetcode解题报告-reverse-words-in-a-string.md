title: LeetCode解题报告-Reverse Words in a String
date: 2014-03-17 14:45:12
tags: 算法
---

Given an input string, reverse the string word by word.

For example,
Given s = "the sky is blue",
return "blue is sky the".



解题思路：
  首先将整个字符串整体反转，然后从前往后遍历反转后的字符串，单独将其中的每个单词反转。

Java代码：
{%codeblock lang:java %}
public class ReverseWords {

	public String reverseWords(String s){
		if(s == null || s.length() == 0){
			return s;
		}
		
		char[] chars = s.toCharArray();
		
		reverseWord(chars,0,chars.length);
		
		int start = 0;
		int end = 0;
		boolean inWord = false;
		for(int i = 0,j = chars.length; i < j; i++){
			char ch = chars[i];
			if(!inWord && ch != ' '){
				inWord = true;
				start = i;
			}
			
			if(inWord && (ch == ' ' || i == j -1)){
				inWord = false;
				end = i == j -1 ? j : i;
				reverseWord(chars,start,end);
			}
		}
		
		return trimCharArray(chars);
	}
	
	private void reverseWord(char[] chars,int start, int end){
		if(chars == null || chars.length == 0 || start >= end || chars.length < end){
			return;
		}
		
		for(int left = start, right = end - 1; left < right; left++,right--){
			char temp = chars[right];
			chars[right] = chars[left];
			chars[left] = temp;
		}
		
	}
	
	private String trimCharArray(char[] chs){
		StringBuilder sb =  new StringBuilder();
		boolean isPreSpace = false;
		for(int i = 0, j = chs.length; i < j; i++){
			char ch = chs[i];
			
			if(ch != ' '){
				if(isPreSpace && sb.length() != 0){
					sb.append(' ');
				}
				sb.append(ch);
			}
			isPreSpace =  ch == ' ';
		}
		return sb.toString();
	}
}
{%endcodeblock%}
