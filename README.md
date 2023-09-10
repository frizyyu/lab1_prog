## <p align="center">Федеральное государственное автономное образовательное учреждение высшего образования<br />«Национальный исследовательский университет ИТМО»<br /><br />Факультет программной инженерии и компьютерной техники<br /><br />Направление подготовки 09.03.04 «Программная инженерия» – Системное и прикладное программное обеспечение</p>
<br />
<br />

### <p align="center">Отчёт<br />По лабораторной работе №1<br />По дисциплине «Программирование»<br />Вар: 1313</p>
<br />
<br />

### <p align="right">Выполнил:<br />Студент 1 курса<br />Васильев Артём Евгеньевич<br />Группа: 3119<br />Преподаватель:<br /></p>
<br />
<br />

### Задание:<br />
Написать программу на языке Java, выполняющую соответствующие варианту действия. Программа должна соответствовать следующим требованиям:<br />
- Она должна быть упакована в исполняемый jar-архив.<br />
- Выражение должно вычисляться в соответствии с правилами вычисления математических выражений (должен соблюдаться порядок выполнения действий и т.д.).<br />
- Программа должна использовать математические функции из стандартной библиотеки Java.<br />
- Результат вычисления выражения должен быть выведен в стандартный поток вывода в заданном формате.<br />

Выполнение программы необходимо продемонстрировать на сервере helios.<br />
1. Создать одномерный массив c типа int. Заполнить его нечётными числами от 5 до 15 включительно в порядке возрастания.<br />
1. Создать одномерный массив x типа double. Заполнить его 17-ю случайными числами в диапазоне от -3.0 до 15.0.<br />
1. Создать двумерный массив c размером 6x17. Вычислить его элементы по следующей формуле (где x = x[j]):<br />
1. если c[i] = 7, то ![Снимок экрана 2023-09-10 211250 copy](https://github.com/frizyyu/lab1_prog/assets/84192047/5a4bc657-b02f-4741-bd45-79e5b8a2e8f8)<br />

1. если c[i] ∈ {9, 11, 15}, то ![Снимок экрана 2023-09-10 211250 copy1](https://github.com/frizyyu/lab1_prog/assets/84192047/3f1722ef-5871-4e1c-b5a5-3b4d7cf63165)<br />

1. для остальных значений ![Снимок экрана 2023-09-10 211250 copy2](https://github.com/frizyyu/lab1_prog/assets/84192047/41bee4bf-eff8-4ad5-918c-c64472e67db8)<br />

Напечатать полученный в результате массив в формате с пятью знаками после запятой.<br />

### Код программы: [файл тут](https://github.com/frizyyu/lab1_prog/blob/main/Main.java)<br />
```
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
```
<br />

### Результат работы программы: [файл тут](https://github.com/frizyyu/lab1_prog/blob/main/result.txt)<br />

```
[[60242939916272360000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000,00000, NaN, Infinity, NaN, 189389550347230960000000000000000000000000000000000000000000000000000000000000000,00000, NaN, NaN, NaN, 9622246775643326000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000,00000, 234,41946, Infinity, Infinity, Infinity, NaN, NaN, Infinity, 73324564421523710000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000,00000], 
[4,12256, NaN, 15,16474, NaN, 3,24212, 1,01202, 0,97895, 44,26242, 3,72761, 1,95355, 14,65809, 13,99678, 4,86302, 0,89445, 0,91724, 9,84034, 3,56139], 
[1,00000, 1,00000, 1,00000, 1,00000, 1,00000, 0,86037, -0,52031, 1,00000, 1,00000, 0,99999, 1,00000, 1,00000, 1,00000, 0,71575, -0,20229, 1,00000, 1,00000], 
[1,00000, 1,00000, 1,00000, 1,00000, 1,00000, 0,86037, -0,52031, 1,00000, 1,00000, 0,99999, 1,00000, 1,00000, 1,00000, 0,71575, -0,20229, 1,00000, 1,00000], 
[60242939916272360000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000,00000, NaN, Infinity, NaN, 189389550347230960000000000000000000000000000000000000000000000000000000000000000,00000, NaN, NaN, NaN, 9622246775643326000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000,00000, 234,41946, Infinity, Infinity, Infinity, NaN, NaN, Infinity, 73324564421523710000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000,00000], 
[1,00000, 1,00000, 1,00000, 1,00000, 1,00000, 0,86037, -0,52031, 1,00000, 1,00000, 0,99999, 1,00000, 1,00000, 1,00000, 0,71575, -0,20229, 1,00000, 1,00000]]
```
<br />

### Вывод:<br />
В ходе выполнения данной лабораторной работы я изучил синтаксис языка Java, узнал больше методов класса Math, научился компилировать .java файлы, а также создавать jar архивы и запускать их на сервере.
