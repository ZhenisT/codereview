# codereview
Задача: поиск уникальных IP адресов из файла с неограниченным размером.
Задача реализует класс com.yourcodereview.turebekov.IPFileReader предоставляющий метод read и возвращает количество уникальных записей.
public long read(String file, AVLTree tree) {
try (FileReader fileReader = new FileReader(file);
BufferedReader reader = new BufferedReader(fileReader)) {

    public long read(String file, AVLTree tree) {
        try (FileReader fileReader = new FileReader(file);
             BufferedReader reader = new BufferedReader(fileReader)) {

            String line;
            while ((line = reader.readLine()) != null) {
                if (!line.isEmpty()) {
                    tree.insert(line);
                }
            }
        } catch (IOException e) {
            throw new RuntimeException("File " + file + " is not found!");
        }

        return tree.size();
    }

Класс AVLTree - дерево бинарного поиска. Существующий элемент не может быть добавлен. Имеет переменную подсчета элементов в дереве.

## Запуск программы
Для запуска программы в качестве аргумента следует передать путь к файлу.

## Ограничения и проблемы
Файлы больших размеров - может вызвать ошибку outOfMemory: java heap
Решение - задать -Xms[size] для установки размера кучи большего размера.
