import java.util.Scanner;
import java.io.FileWriter;
import java.io.IOException;

public class BubbleSort {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Ввод длины массива
        System.out.print("Введите длину массива: ");
        while (!scanner.hasNextInt()) {
            System.out.println("Ошибка! Введите число: ");
            scanner.next();
        }
        int length = scanner.nextInt();
        
        // Ввод элементов массива
        int[] arr = new int[length];
        System.out.println("Введите элементы массива:");
        for (int i = 0; i < length; i++) {
            while (!scanner.hasNextInt()) {
                System.out.println("Ошибка! Введите число: ");
                scanner.next();
            }
            arr[i] = scanner.nextInt();
        }

        scanner.close();

        // Проверка на количество элементов массива
        if (arr.length != length) {
            System.out.println("Ошибка! Количество чисел не совпадает с указанной длиной массива.");
            return;
        }

        // Сортировка пузырьком
        for (int i = 0; i < length - 1; i++) {
            for (int j = 0; j < length - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
        
        // Запись отсортированного массива в файл
        try {
            FileWriter writer = new FileWriter("sorted_array.txt", true);
            for (int i = 0; i < length; i++) {
                writer.write(arr[i] + " ");
            }
            writer.write("\n");
            writer.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
