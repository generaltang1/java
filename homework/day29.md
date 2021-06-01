구구단 2단.txt ~ 9단.txt 을 모두 저장해보자
 	
 		2단.txt
 		2 x 1 = 2
 		2 x 2 = 4
 		..
 		2 x 9 = 18
 		-------------------
 		위에서 만든 파일 사용하여
 		사용자에게 '단' 을 입력 받고 해당 파일을 출력 
    
    
   ```java
import java.io.*;
import java.util.Scanner;

public class Homework01 {

	public static void main(String[] args) {
		for(int i = 2; i < 10; ++i) {
		try {
			FileWriter fw = new FileWriter(i+"단.txt");
			for(int j = 1; j < 10; ++j) {
				fw.write(i + " X " + j + " = " +i*j +"\n");
			}
			fw.close();
		} catch (IOException e) {
						e.printStackTrace();
		}
		
		} // for
		
		String dan;
		Scanner sc = new Scanner(System.in);
		System.out.println("출력할 구구단은?");
		dan = sc.next() + ".txt";
		try {
			FileInputStream fIn = new FileInputStream(dan);
			Scanner sc2 = new Scanner(fIn);
			
			while(sc2.hasNext()) {
			String s;
			s = sc2.nextLine();
			System.out.println(s);
			}
			sc2.close();
			fIn.close();
			
			
		} catch (IOException e) {
			e.printStackTrace();
		}
		
	} // main

}

    ```
