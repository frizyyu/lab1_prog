# lab1_prog
# Лабораторная работа №1 по программированию

## <p align="center">Федеральное государственное автономное образовательное учреждение высшего образования<br />«Национальный исследовательский университет ИТМО»<br />Факультет программной инженерии и компьютерной техники<br />Направление подготовки 09.03.04 «Программная инженерия» – Системное и прикладное программное обеспечение</p>
<br />
<br />

### <p align="center">Отчёт<br />По лабораторной работе №1<br />По дисциплине «Программирование»<br />Вар: 1313</p>
<br />
<br />
<p align="right">Выполнил:<br />
Студент 1 курса<br />
Васильев Артём Евгеньевич<br />
Группа: 3119<br />
Преподаватель:<br /></p>







Задание:
Написать программу на языке Java, выполняющую соответствующие варианту действия. Программа должна соответствовать следующим требованиям:
> 1.Она должна быть упакована в исполняемый jar-архив.
> 2.Выражение должно вычисляться в соответствии с правилами вычисления математических выражений (должен соблюдаться порядок выполнения действий и т.д.).
> 3.Программа должна использовать математические функции из стандартной библиотеки Java.
> 4.Результат вычисления выражения должен быть выведен в стандартный поток вывода в заданном формате.
Выполнение программы необходимо продемонстрировать на сервере helios.
Код программы:

      import java.util.Arrays;
      
      public class Main {
         public static void main(String[] args) {
      
             int[] c = new int[6]; //массив из 6 элементов, тк в диапазоне от 5 до 15 6 нечётных
             int counter = 0;
      
             double MIN = -3.0;
             double MAX = 15.0;
      
             double[] x = new double[17];
      
             String st = "[";
      
             for(int i=5; i<=15; i++){
                 if (i % 2 == 1)
                 {
                     c[counter] = i;
                     counter += 1;
                 }
             }
      
             for (int i=0; i <= x.length - 1; i++){
                 x[i] = (Math.random() * (MAX - MIN)) + MIN; //получаем рандомное от 0 до 1, затем преобразуем к нашему диапазону [-3.0, 15.0]
             }
             double[][] n = new double[6][17];
             for (int i=0; i < 6; i++){
                 for (int j=0; j < 17; j++){
                     if (c[i] == 7)
                         n[i][j] = Math.pow(Math.pow((2 * Math.pow(Math.E, x[j])), Math.asin((x[j] + 6) / 18)), (double) 1/3); //формула 1
                     else if (c[i] == 9 || c[i] == 11 || c[i] == 15) {
                         n[i][j] = Math.cos(Math.pow(((double)3 / 4) / (x[j] + 1 + (double) 1/2), 3)); //формула 2
                     }
                     else{
                         n[i][j] = Math.pow(Math.pow(Math.pow(Math.log(Math.abs(x[j])), ((Math.pow((x[j] / 0.5), 3) - (double) 3/4) / 2) / 3), (double) 1/3), 0.5 * (Math.pow((double) 2/3 + Math.pow((double)1/2 * (x[j] / (1 - Math.asin((x[j] + 6) / 18))), Math.asin((x[j] + 6) / 18)), 2) + (double) 1/4)); //формула 3
                     }
                 }
             }
      
             for (int i = 0; i < 6; i++){
                 st += "[";
                 for (int j = 0; j < 17; j++)
                     if (j != 16)
                         st += String.format("%.5f, ", n[i][j]);
                     else
                         st += String.format("%.5f", n[i][j]);
                 if (i == 5)
                     st += "]]";
                 else
                     st += "], \n";
      
             }
             System.out.println(st);
         }
      }

