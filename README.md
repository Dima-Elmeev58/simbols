# simbols
 static void Main(string[] args)
    {
        string inputFilePath = "C:\\Users\\Artem\\Desktop\\Текст.docx"; // Путь к проверяемому файлу
        string outputFilePath = "C:\\Users\\Artem\\Desktop\\Результаты.txt"; // Путь к файлу куда будут записаны результаты

        try
        {
            // Чтение содержимого файла
            string text = File.ReadAllText(inputFilePath);

            // Подсчет символов
            int Characters = text.Length;

            // Подсчет символов без пробелов
            int charactersWithoutSpaces = text.Count(c => !char.IsWhiteSpace(c));

            // Подсчет слов
            int wordCount = text.Split(new char[] { ' ', '\t', '\n', '\r' }, StringSplitOptions.RemoveEmptyEntries).Length;

            // Результаты
            string results = $"Количество символов: {Characters}\n" +
                             $"Количество символов без пробелов: {charactersWithoutSpaces}\n" +
                             $"Количество слов: {wordCount}";

            Console.WriteLine(results);

            // Запись результатов в файл
            File.WriteAllText(outputFilePath, results);
        }
        catch (FileNotFoundException ex) //Обработка ошибок - исключений
        {
            Console.WriteLine("Ошибка: файл не найден.");
            Console.WriteLine(ex.Message);
        }
        catch (IOException ex)
        {
            Console.WriteLine("Ошибка при чтении файла.");
            Console.WriteLine(ex.Message);
        }
        catch (Exception ex)
        {
            Console.WriteLine("Произошла ошибка.");
            Console.WriteLine(ex.Message);
        }
    }
}
