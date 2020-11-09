# Think
나는 Scanner 객체를, 선생님은 JOptionPane을 이용했다. 따로 변수 선언 안 해도 되서 JOptionPane이 더 좋은 것 같다.

```java
package day09.homework;
import javax.swing.JOptionPane;
// teacher

public class Homework02 {
	public static void main(String[] args) {
		Pokemon[] pokemons = new Pokemon[5];
		int lastIdx = -1; // 가장 마지막 포켓몬의 인덱스. 다 채워지면 4
		String menu = "1. 포켓몬 등록\n2. 모든 포켓몬 보기\n3. 레벨업\n0. 종료";
		String select;

		while(true) {
			select = JOptionPane.showInputDialog(menu);

			switch (select) {

			case "1":{
				if(lastIdx == pokemons.length-1) {
					// 포켓몬이 모두 등록되었을때(lastIdx == 4일때)
					JOptionPane.showMessageDialog(null, "더이상 추가할 수 없습니다.");
					continue; // while문으로 돌아감.
				}
				Pokemon p = new Pokemon();
				p.name = JOptionPane.showInputDialog("이름");
				p.level = Integer.parseInt(JOptionPane.showInputDialog("레벨"));

				// 체력, 공격력
				p.hp = p.level*1000;
				p.power = p.level * ((Math.random()<0.2)? 3 : 2); // checkpoint

				pokemons[++lastIdx] = p; // checkpoint : lastIdx를 이용하여 인덱스값 변경
				break;
			}

			case "2":{ // 모든 포켓몬 보기
				String message = " * 포켓몬 정보 *";
				if(lastIdx == -1) {
					System.out.println("포켓몬이 존재하지 않습니다.");
					break;
				} // checkpoint : 만약에 객체를 3개정도 추가했으면 4번째부터 nullpointerException이 발생하게 된다. 해당 코드는 아예 포켓몬을 추가하지 않았을 경우에만 사용됨
				
				for(Pokemon p:pokemons) {
					if(p == null) {
						break; // NullPointerException 해결
					}
					message += "\nLv. " + p.level + "\nhp. " + p.hp + "\nap. " + p.power;
				}
				
				JOptionPane.showMessageDialog(null, message); // swtich
				break;
			}

			case "3":{ // 레벨업
				// 2. 포켓몬 이름 입력받아 해당 포켓몬만 레벨업(중복x)
				String name = JOptionPane.showInputDialog("포켓몬 이름을 입력하세요.");
				boolean found = false;
				for(Pokemon p:pokemons) {
					if(p.name.equals(name)) {
						++p.level;
						JOptionPane.showMessageDialog(null, "레벨업!");
						found = true;
						break; // 먼저 발견한 포켓몬만 레벨업하게 함.
					}
				}

				if(found == false) {
					JOptionPane.showMessageDialog(null, "레벨업 완료!"); 
					break;
				}
			}

			case "0":{
				JOptionPane.showInputDialog(null, "프로그램 종료");
				return;
			}

			default:{
				System.out.println("잘못된 입력입니다.");
				break;
			}
			}
		}



	}

}
```
