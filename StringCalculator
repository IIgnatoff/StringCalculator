import java.util.Scanner;

class StringCalculator {

    public static void main(String[] args) {
        // Создаем объект Scanner для чтения ввода пользователя
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Это строковый калькулятор");
            System.out.println("Введите строки в формате \"a\" + \"b\", \"a\" - \"b\", \"a\" * b или \"a\" / b в одну строку:");
            String vvod = scanner.nextLine();
            /**
             * Пытаемся выполнить расчет введенного выражения.
             * Выводим результат на консоль. Завершаем цикл при успешном выполнении или сообщаем об ошибке
             */
            try {
                String resultat = calculate(vvod);
                System.out.println(resultat);
                break;
            } catch (IllegalArgumentException e) {
                System.out.println("Ошибка: " + e.getMessage());
            }
        }
    }


    public static String calculate(String vvod) {

        // Проверяем, соответствует ли выражение операции сложения строк: "a" + "b"
        if (vvod.matches("\"[^\"]{1,10}\" \\+ \"[^\"]{1,10}\"")) {
            String[] parts = vvod.split(" \\+ ");
            String str1 = parts[0].substring(1, parts[0].length() - 1);
            String str2 = parts[1].substring(1, parts[1].length() - 1);
            return formatOutput(str1 + str2);
        }

        // Проверяем, соответствует ли выражение операции вычитания строки из строки: "a" - "b"
        if (vvod.matches("\"[^\"]{1,10}\" - \"[^\"]{1,10}\"")) {
            String[] parts = vvod.split(" - ");
            String str1 = parts[0].substring(1, parts[0].length() - 1);
            String str2 = parts[1].substring(1, parts[1].length() - 1);
            return formatOutput(str1.replace(str2, ""));
        }

        // Проверяем, соответствует ли выражение операции умножения строки на число: "a" * b
        if (vvod.matches("\"[^\"]{1,10}\" \\* \\d+")) {
            String[] parts = vvod.split(" \\* ");
            String str = parts[0].substring(1, parts[0].length() - 1);
            int numberTen = Integer.parseInt(parts[1]);

            if (numberTen < 1 || numberTen > 10) {
                throw new IllegalArgumentException("Число должно быть от 1 до 10!!!");
            }

            return formatOutput(str.repeat(numberTen));
        }

        // Проверяем, соответствует ли выражение операции деления строки на число: "a" / b
        if (vvod.matches("\"[^\"]{1,10}\" / \\d+")) {
            String[] parts = vvod.split(" / ");
            String str = parts[0].substring(1, parts[0].length() - 1);
            int separator = Integer.parseInt(parts[1]);

            if (separator < 1 || separator > 10) {
                throw new IllegalArgumentException("Число должно быть от 1 до 10.");
            }

            if (separator > str.length()) {
                return "\"\"";
            }
            // Возвращаем результат деления строки на число
            return formatOutput(str.substring(0, str.length() / separator));
        }

        // Если выражение не соответствует ни одному из форматов, показываем исключение
        throw new IllegalArgumentException("Неподдерживаемое выражение.");
    }

    /**
     * Метод formatOutput форматирует строку, обрезая ее до 40 символов и добавляя "..." в конце, если это необходимо.
     */
    private static String formatOutput(String resultat) {
        // Если длина строки больше 40 символов, обрезаем ее и добавляем "..."
        if (resultat.length() > 40) {
            return "\"" + resultat.substring(0, 40) + "...\"";
        }
        return "\"" + resultat + "\"";
    }
}
