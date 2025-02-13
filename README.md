# Что такое замыкание?
В JavaScript замыкания (closures) — это мощная концепция, которая позволяет функции "запомнить" своё лексическое окружение, даже если она выполняется вне этого окружения. Это означает, что функция, созданная внутри другой функции, может продолжать доступ к переменным, объявленным в родительской функции, даже после того как родительская функция завершила выполнение

# Пример замыкания

function outer() {
  let outerVariable = 'I am from outer function';

  function inner() {
    console.log(outerVariable); // inner функция имеет доступ к переменной outerVariable
  }

  return inner; // возвращаем ссылку на inner функцию
}

const closureFunction = outer(); // здесь outer функция выполняется, но возвращает inner
closureFunction(); // вызов замыкания, которое всё ещё имеет доступ к outerVariable

## Объяснение:
Когда мы вызываем функцию outer(), она создаёт переменную outerVariable и затем возвращает функцию inner().
Несмотря на то, что выполнение функции outer завершено, переменная outerVariable остаётся доступной внутри функции inner, так как она является частью замыкания.
# Пример с параметрами
Вот пример, который показывает, как замыкание может работать с параметрами:
function makeCounter() {
  let count = 0;

  return function() {
    count++;
    return count;
  };
}

const counter = makeCounter(); // возвращает функцию-счётчик
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3

# Объяснение:
Функция makeCounter() возвращает другую функцию, которая увеличивает и возвращает значение переменной count.
Несмотря на то, что makeCounter() уже завершила выполнение, возвращённая функция продолжает доступ к переменной count, потому что она является замыканием.

#Зачем нужны замыкания?
Инкапсуляция: Замыкания позволяют скрыть данные от глобальной области видимости, так что они не могут быть случайно изменены.
Фабрики функций: Они позволяют создавать функции с уникальными состояниями. Например, можно создать несколько независимых счётчиков, как показано в примере выше.
Асинхронные операции: Замыкания полезны в обработчиках событий или при работе с асинхронным кодом, где важно сохранять контекст.

# Заключение
Замыкания — это фундаментальный концепт JavaScript, который часто используется для создания функций с состоянием, инкапсуляции данных и обеспечения удобной работы с асинхронным кодом.

## Рекурсия 
— это метод решения задачи, при котором функция вызывает сама себя. Важной частью рекурсии является условие выхода, которое предотвращает бесконечные вызовы функции и завершает её выполнение.

# Основные принципы рекурсии
Базовое условие — это условие, при котором рекурсивные вызовы прекращаются. Без базового условия рекурсия может продолжаться бесконечно.
Рекурсивный вызов — это когда функция вызывает саму себя с новыми аргументами, которые приближаются к базовому условию.

# Пример простой рекурсии
Посмотрим на простой пример рекурсивной функции, которая вычисляет факториал числа:
function factorial(n) {
  if (n === 0) {  // базовое условие
    return 1;      // факториал 0 равен 1
  }
  return n * factorial(n - 1);  // рекурсивный вызов
}

console.log(factorial(5));  // 120
## Объяснение:
Функция factorial вызывает сама себя, но с уменьшенным значением n (то есть n - 1).
Базовое условие — это когда n === 0. В этот момент рекурсия прекращается и возвращает 1 (факториал 0).
Для вычисления факториала 5, например, рекурсивные вызовы будут выглядеть так:
factorial(5) вызывает factorial(4), и так далее, пока не дойдёт до factorial(0), который вернёт 1.
Затем все промежуточные результаты перемножаются и возвращают конечный результат — 120.

# Почему и когда использовать рекурсию
Рекурсия полезна в ситуациях, когда:
Проблема имеет рекурсивную структуру, например, задачи, связанные с деревьями, графами или разбиением задачи на подзадачи (например, сортировка).
Усложнение логики с итерациями — рекурсия позволяет проще и элегантнее выразить решение задачи.
Решение с ограничением по памяти — рекурсивные функции могут быть эффективнее при ограничении на использование памяти, так как они работают "на месте" (на стеке вызовов).

# Важное замечание
Рекурсия может быть неэффективной с точки зрения памяти, если глубина рекурсии слишком велика. В таких случаях стоит задуматься об использовании итеративных решений или оптимизации рекурсии, например, с помощью хвостовой рекурсии (tail recursion), которая оптимизируется в некоторых языках программирования.

### Рекурсия — это мощный инструмент, и понимание её принципов помогает решать множество задач в программировании.
