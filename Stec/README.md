<b>в данной программе было реализовано подобие стека<b/>

public class Stec

    public static void main(String[] args) {

        MyStec stec = new MyStec(3);

        stec.add(8);
        stec.add(18);
        stec.add(4);
        stec.add(9);
        stec.add(6);

        stec.print();
        System.out.println("");

        int x = stec.dost();
        System.out.println(x);
        System.out.println("");

        stec.print();
    }
    
    
public class MyStec

    public int[] mas;                           // создаем общий массив для стека

    public MyStec(){}
    public MyStec(int x){ add(x);}              // конструктор с первым элементом стека


    public void add(int num){                   // добавляем элемент в стек
        int[] mas2;                             // создаем доболнительный стек

        if (mas == null){                       // если стек пуст
            mas = new int[1];                   // добавляем в стек ячейку
            mas[0] = num;                       // помещаем в ячейку элемент num
        }else{                                  // если в стеке есть хотя-бы 1 элемент
            mas2 = new int[mas.length + 1];     // доболнительный стек на 1-у больше основного стека
            mas2[0] = num;                      // помещаем в 1-у ячейку стека элемент num
            for(int i=0; i<mas.length; i++){
                mas2[i+1] = mas[i];             // оставшееся место в доболнительном стеке заполняем элементами основного стека
            }
            mas = mas2;
        }
    }

    public int dost(){                          // достать элемент из стека 
        int mas3 = mas[0];                      // достаем первый элемент стека в классе MyStek
        int mas2[] = new int[mas.length-1];     // создаем класс на 1-у меньше стека
        for (int j = 0; j < mas2.length; j++){
            mas2[j] = mas[j+1];                 // переносим элементы стека
        }
        mas = mas2;                             // создаем стека на 1-у меньше 

        return mas3;                            // достаем первый элемент стека в основном слассе Main
    }

    public void print(){                        // вывести на экран содержимое стека
        if(mas != null){                        // если в стеке есть хотя-бы 1 элемент
            for(int i=0; i<mas.length; i++){
                System.out.println(mas[i]);     // выводим каждый элемент стека
            }
        }else{                                  // если стек пуст
            System.out.println("null");
        }
    }
