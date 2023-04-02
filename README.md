//bitStuffing
import java.util.*;

import javax.lang.model.util.ElementScanner14;
class BitStuffing
{
    public static void main(String args[])
    {
        Scanner sc=new Scanner(System.in);
        int flag=0;
        int count=0;
        ArrayList<Integer> list=new ArrayList<Integer>();
        ArrayList<Integer> list1=new ArrayList<Integer>();
        String s=new String();
        System.out.println("Enter the binary data:");
        s=sc.nextLine();
        for(int i=0;i<s.length();i++)
        {
            list.add(Character.getNumericValue(s.charAt(i)));
        }
        for(int i=0;i<s.length();i++)
        {
            list1.add(Character.getNumericValue(s.charAt(i)));
        }
        System.out.println("-----BITSTUFFING-----");
        for(int i=8;i<list.size()-7;i++)
        {
            if(list.get(i)==1 && flag!=5)
            {
                flag+=1;
            }
            else if(flag==5)
            {
                list.add(i,0);
                i=i+1;
                flag=0;
            }
            else 
            {
                flag=0;
            }
        }
        for(int a:list)
        {
            System.out.print(a);
        }
        System.out.println();
        System.out.println("----BITUNSTUFFING----");
        for(int i=8;i<list.size()-7;i++)
        {
            if(list.get(i)!=list1.get(i))
            {
                list.remove(i);
            }
        }
        if(list1.size()==list.size())
        {
            for(int i=0;i<list1.size();i++)
            {
                if(list1.get(i)==list.get(i))
                {
                    count++;
                }
            }
        }
        if(count==list1.size())
        {
            System.out.println("data was sent successfully");
        }
        System.out.println("Data sent to receiver is");
        for(int i=0;i<list.size();i++)
        {
            System.out.print(list.get(i));
        } 
        System.out.println();
        System.out.println("------------------------------------------");
        for(int i=0;i<list1.size();i++)
        {
            System.out.print(list1.get(i));
        } 
    }
}
