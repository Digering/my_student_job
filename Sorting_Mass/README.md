в данной программе было реализована сортировка массива путем пузырьковой сортировки и сортировки выбором


Главный(Main) файл

public class Main {

    public static void main(String[] args) {
        int[] mas1 = new int[]{14,7,1,4,2};
        int[] mas2 = new int[]{14,7,1,4,2};
        MySortingMass mas12 = new MySortingMass(mas1);
        MySortingMass mas22 = new MySortingMass(mas2);

        long start = System.nanoTime();

        System.out.println("");
        System.out.println("Сортировка выбором: ");
        mas12.Print();
        System.out.println("");
        mas12.Sort();
        mas12.Print();
        long finish1 = System.nanoTime();
        System.out.println("");
        System.out.println("Время выполнения: "+(finish1-start)/ 1000000);

        System.out.println("");
        System.out.println("Пузырьковая сортировка: ");
        mas22.Print();
        System.out.println("");
        mas22.Bubble_sorting();
        mas22.Print();
        long finish2 = System.nanoTime();
        System.out.println("");
        System.out.println("Время выполнения: "+(finish2-start)/ 1000000);
    }


файл с классом сортировок

public class MySortingMass {

    int[] items;

    public MySortingMass(int[] items){
        this.items = items;
    }

    private void Swap(int[] items, int left, int right){
        if (left != right){
            int temp = items[left];
            items[left] = items[right];
            items[right] = temp;
        }
    }
    public void Bubble_sorting(){

        boolean  swapped;
        do
        {
            swapped = false;
            for (int i = 1; i < items.length; i++) {
                if (items[i-1]>items[i])
                {
                    Swap(items, i - 1, i);
                    swapped = true;
                }
            }
        } while (swapped);

    }

    public void Sort()
    {
        int RangeEnd = 0;

        while (RangeEnd < items.length)
        {
            int nextIndex = Sorting_by_choice(items, RangeEnd);
            Swap(items, RangeEnd, nextIndex);

            RangeEnd++;
        }
    }

    private int Sorting_by_choice(int[] items, int RangeEnd)
    {
        int current = items[RangeEnd];
        int currentSmall = RangeEnd;

        for (int i = RangeEnd + 1; i < items.length; i++)
        {
            if (current > items[i])
            {
                current = items[i];
                currentSmall = i;
            }
        }

        return currentSmall;
    }

    public void Print(){
        for (int i=0; i<items.length;i++)
            System.out.print(items[i]+" ");
    }

