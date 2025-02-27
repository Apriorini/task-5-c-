Console.Write("Введите a: ");
string a1 = Console.ReadLine();
double a = Convert.ToDouble(a1);
Console.Write("Введите b: ");
string b1 = Console.ReadLine();
double b = Convert.ToDouble(b1);
Console.Write("Введите шаг h: ");
string h1 = Console.ReadLine();
double h = Convert.ToDouble(h1);
if (a >= b)
{
    Console.WriteLine("a должно быть меньше b.");
    return;
}
if (h <= 0)
{
    Console.WriteLine("h должен быть положительным.");
    return;
}
List<double> xValues = new List<double>();
for (double x = a; x <= b + 1e-9; x += h)
{
    xValues.Add(x);
}
List<double> yValues = new List<double>();
foreach (double x in xValues)
{
    double y = Math.Cos(x * x) + Math.Pow(Math.Sin(x), 2);
    yValues.Add(y);
}
double minY = 0;
double maxY = 0;
foreach (double y in yValues)
{
    if (y < minY) minY = y;
    if (y > maxY) maxY = y;
}
int crossCount = 0;
for (int i = 0; i < yValues.Count - 1; i++)
{
    if (yValues[i] * yValues[i + 1] < 0)
        crossCount++;
}
Console.WriteLine("\nТаблица значений:");
Console.WriteLine("{0,10} | {1,10}", "x", "y(x)");
Console.WriteLine(new string('-', 23));
for (int i = 0; i < xValues.Count; i++)
{
    Console.WriteLine("{0,10:F3} | {1,10:F5}",
                    xValues[i],
                    yValues[i]);
}
Console.WriteLine("\nКоличество точек в таблице: " + xValues.Count);
Console.WriteLine("Минимальное значение функции: {0:F5}", minY);
Console.WriteLine("Максимальное значение функции: {0:F5}", maxY);
Console.WriteLine("Количество пересечений оси X: " + crossCount);
