package test;

import java.util.Arrays;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class test {

	// return integer if it doesn't match previous one in array
	public static int lonelyInteger(int[] arr) {
		int i=0;
		while (i<(arr.length-1))
		{
			if (arr[i] != arr[i+1])
				return arr[i+1];
			i++;
		}
			
		return arr[i];
	}

	// extract values for user/pass and return
	public static String extractCredentials(String[] arr) {
		int i=0;
		String user = "none";
		String pass = "none";
		while (i<(arr.length))
		{
			int lastIndex = -1;
			lastIndex = arr[i].lastIndexOf("user=");
			if (lastIndex >= 0)
			{
				user=arr[i].substring(lastIndex+"user=".length());
			}
			lastIndex = arr[i].lastIndexOf("pass=");
			if (lastIndex >= 0)
			{
				pass=arr[i].substring(lastIndex+"pass=".length());
			}
			i++;
		}
			
		return user + ":" + pass;
	}

	// parse array and return elements that contain an IP address
	public static String parseLog(String[] arr) {

		Pattern p = Pattern.compile("[0-9]+\\.[0-9]+\\.[0-9]+\\.[0-9]+");
		int i=0;
		String ret = "";
		String sep = "";
		while (i<(arr.length))
		{
			Matcher m = p.matcher(arr[i]);
			if (m.find()) {
				ret = ret + sep + arr[i];
				sep=" ";
			}
			i++;
		}
		return ret;
	}
	
	// sort numbers in array and return pairs of numbers
	public static String parseNums(String[] arr) {
		Arrays.sort(arr);
		int i=0;
		String ret="";
		String sep="";
		while (i<(arr.length-1))
		{
			ret = ret + sep + arr[i]+" "+arr[i+1];
			sep = " ";
			i++;
		}
		return ret;
	}
	
	// stub to test above method
	public static void lonelyStub() {
		int[] anArray;
		anArray = new int[3];
		anArray[0] = 1;
		anArray[1] = 1;
		anArray[2] = 2;
		int ret= lonelyInteger(anArray);
		System.out.println("ret = "+ret);		
	}

	// stub to test above method
	public static void extractCredentialsStub() {
		String[] anArray;
		anArray = new String[3];
		anArray[0] = "a=b";
		anArray[1] = "user=joe";
		anArray[2] = "pass=secret";
		String ret= extractCredentials(anArray);
		System.out.println("ret = "+ret);		
	}

	// stub to test above method
	public static void parseLogStub() {
		String[] anArray;
		anArray = new String[3];
		anArray[0] = "line 1";
		anArray[1] = "ip address is 10.0.2.15";
		anArray[2] = "mac addr = 08:00:27:12:96:98";
		String ret= parseLog(anArray);
		System.out.println("ret = "+ret);		
	}

	// stub to test above method
	public static void parseNumsStub() {
		String[] anArray;
		anArray = new String[4];
		anArray[0] = "4";
		anArray[1] = "2";
		anArray[2] = "1";
		anArray[3] = "3";
		String ret= parseNums(anArray);
		System.out.println("ret = "+ret);		
	}
	
	public static void main(String[] args) {
		lonelyStub();
		extractCredentialsStub();
		parseLogStub();
		parseNumsStub();
	}

}
