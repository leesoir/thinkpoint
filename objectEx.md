```java
package com.javalec.quiz;
import java.util.Scanner;

/*
 * 1. Student 클래스 
 *  - 멤버변수(=필드) 선언
 *   이름, 국, 영, 수, 평균, 합격여부(boolean)
 * 
 * 2. Quiz01 메인클래스 
 *  - Student 인스턴스를 3개 생성하여 
 *  - Scanner를 사용해서 학생 3명의 이름, 국, 영, 수를 입력 받는다
 *  - 모든 인스턴스의 평균과 합격 여부(평균 60점 이상이면 합격)이 계산되어 저장
 *  - 3명의 이름, 평균, 합격 여부를 출력 
 *   
 */
public class Quiz01 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		Student[] students = new Student[3]; // 길이가 3인 Student 배열
		
		for(int i=0; i<students.length; i++) {
			System.out.println("이름과 국어, 영어, 수학 점수를 입력하세요 > ");
			students[i] = new Student(); 
			students[i].name = sc.next();
			students[i].language = sc.nextInt();
			students[i].english = sc.nextInt();
			students[i].math = sc.nextInt();
			students[i].average = (students[i].language + students[i].english + students[i].math) / 3;
		
			// *** think point
//			if(students[i].average >= 60) {
//				students[i].pass = true;
//			} else students[i].pass = false;
			students[i].pass = students[i].average >= 60; 
        // 논리문 자체가 boolean을 리턴하므로 코드 길이를 줄일 수 있다.
		}
		
		for(Student s:students) {
			System.out.println("이름 : " + s.name + "\n국어 점수 : " + s.language + "\n영어 점수 : " + s.english + "\n수학 점수 : " + s.math + "\n평균 : " + s.average + "\n합격 여부 : " + s.pass + "\n");
		}
		
		sc.close();
		
	}
}
```
