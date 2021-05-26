영단어장 프로그램

```java

package com.day24.Quiz;

import java.util.Map;
import java.util.Map.Entry;
import java.util.TreeMap;

import javax.swing.JOptionPane;

public class Quiz01 {
   public static void main(String[] args) {
      String menu = "1. 등록 2. 모두 보기 3. 검색 4. 종료";
      String select;
      String word, meaning;
      StringBuilder sb = new StringBuilder();
      Map<String, String> map = new TreeMap<String, String>();
      loop:while(true) {
         select = JOptionPane.showInputDialog(menu);
         switch (select) {
         case "1":
            word = JOptionPane.showInputDialog("새 단어");
            meaning= JOptionPane.showInputDialog(word + "의 뜻");
            map.put(word, meaning);
            break;
         case "2":
            sb.append("==== 단어 목록 ====\n");
            for(Entry<String, String> e : map.entrySet()) {
               sb.append(e.getKey())
               .append(" : ")
               .append(e.getValue())
               .append("\n");
            }
            JOptionPane.showMessageDialog(null, sb);
            break;
         case "3":
            word = JOptionPane.showInputDialog("검색할 단어");
            if(map.containsKey(word)) {
               JOptionPane.showMessageDialog(null, map.get(word));
            }else {
               JOptionPane.showMessageDialog(null, "미등록 단어");
            }
            break;
         case "4":
            // {"apple", "home", "book"}
            Object[] arr = map.keySet().toArray();
            int rand = (int)(Math.random() * arr.length);
            String answer;
            
            word = (String)arr[rand];  // "home"
            meaning = map.get(word); // 집
            answer = JOptionPane.showInputDialog(meaning + "(은)는 영어로?");
            
            if(word.equalsIgnoreCase(answer)) {
               JOptionPane.showMessageDialog(null, "정답!");
            }
            else {
               JOptionPane.showMessageDialog(null, "땡!");
            }
            break;
         case "0":
            
            break loop;

         default:
            break;
         }
            
      }
   }
}
```
