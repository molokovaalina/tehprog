#include <iostream>

template <class T>
struct Node
{               // Структура узла списка
    T data;     // Значение, хранимое в узле
    Node *next; // Указатель на следующий узел

    Node(T value) : data(value), next(nullptr) {} // Конструктор узла, инициализирует значение и указатель на nullptr
};

template <class T>
class LinkedList
{
private:
    Node<T> *head; // Указатель на начало списка

public:
    LinkedList() : head(nullptr) {} // Конструктор списка, инициализирует указатель на nullptr

    // Метод добавления элемента в начало списка
    void addFirst(T value)
    {
        Node<T> *newNode = new Node<T>(value); // Создаем новый узел
        newNode->next = head;                  // Устанавливаем указатель нового узла на текущее начало списка
        head = newNode;                        // Обновляем указатель начала списка на новый узел
    }

    // Метод добавления элемента по индексу
    void addAtIndex(int index, T value)
    {
        if (index < 0)
        { // Проверка на некорректный индекс
            std::cerr << "Индекс не должен быть отрицательным" << std::endl;
            return;
        }

        if (index == 0)
        { // Если индекс 0, то добавляем в начало
            addFirst(value);
            return;
        }

        Node<T> *newNode = new Node<T>(value); // Создаем новый узел
        Node<T> *current = head;               // Указатель для перемещения по списку
        for (int i = 0; i < index - 1 && current != nullptr; i++)
        { // Переходим к узлу перед индексом
            current = current->next;
        }

        if (current == nullptr)
        { // Проверка на выход за границы списка
            std::cerr << "Индекс вышел за пределы списка" << std::endl;
            return;
        }

        newNode->next = current->next; // Обновляем указатели нового узла и соседних узлов
        current->next = newNode;
    }

    // Метод добавления элемента в конец списка
    void addLast(T value)
    {
        Node<T> *newNode = new Node<T>(value); // Создаем новый узел
        if (head == nullptr)
        { // Если список пуст, добавляем в начало
            head = newNode;
            return;
        }

        Node<T> *current = head; // Указатель для перемещения по списку
        while (current->next != nullptr)
        { // Переходим к последнему узлу
            current = current->next;
        }

        current->next = newNode; // Обновляем указатель последнего узла
    }

    // Метод удаления первого элемента списка
    void deleteFirst()
    {
        if (head == nullptr)
        { // Проверка на пустой список
            std::cerr << "Список пуст" << std::endl;
            return;
        }

        Node<T> *temp = head; // Временный указатель на удаляемый узел
        head = head->next;    // Обновляем указатель начала списка
        delete temp;          // Удаляем узел
    }

    // Метод удаления последнего элемента списка
    void deleteLast()
    {
        if (head == nullptr)
        {
            std::cerr << "Список пуст" << std::endl;
            return;
        }

        if (head->next == nullptr)
        {                   // Если в списке один элемент
            delete head;    // Удаляем его
            head = nullptr; // Обнуляем указатель на начало
            return;
        }

        Node<T> *current = head;
        while (current->next->next != nullptr)
        { // Доходим до предпоследнего узла
            current = current->next;
        }

        delete current->next;    // Удаляем последний узел
        current->next = nullptr; // Обновляем указатель предпоследнего узла
    }

    // Метод удаления элемента по индексу
    void deleteAtIndex(int index)
    {
        if (index < 0)
        { // Проверка на некорректный индекс
            std::cerr << "Индекс не должен быть отрицательным" << std::endl;
            return;
        }

        if (index == 0)
        { // Если индекс 0, то удаляем первый элемент
            deleteFirst();
            return;
        }

        Node<T> *current = head; // Указатель для перемещения по списку
        for (int i = 0; i < index - 1 && current != nullptr; i++)
        { // Доходим к узлу перед индексом
            current = current->next;
        }

        if (current == nullptr || current->next == nullptr)
        { // Проверка на выход за границы списка
            std::cerr << "Индекс вышел за пределы списка" << std::endl;
            return;
        }

        Node<T> *temp = current->next;       // Временный указатель на удаляемый узел
        current->next = current->next->next; // Обновляем указатель на следующий узел
        delete temp;                         // Удаляем узел
    }

    // Метод обновления элемента по индексу
    void updateAtIndex(int index, T value)
    {
        if (index < 0)
        {
            std::cerr << "Индекс не должен быть отрицательным";
            return;
        }

        Node<T> *current = head;
        for (int i = 0; i < index && current != nullptr; i++)
        { // Доходим к указанному индексу
            current = current->next;
        }

        if (current == nullptr)
        {
            std::cerr << "Индекс вышел за пределы списка" << std::endl;
            return;
        }

        current->data = value; // Обновляем значение узла
    }

    // Метод поиска элемента по индексу
    T findByIndex(int index)
    {
        if (index < 0)
        {
            std::cerr << "Индекс не должен быть отрицательным" << std::endl;
            return T();
        }

        Node<T> *current = head;
        for (int i = 0; i < index && current != nullptr; i++)
        { // Доходим к указанному индексу
            current = current->next;
        }

        if (current == nullptr)
        {
            std::cerr << "Индекс вышел за пределы списка" << std::endl;
            return T();
        }

        return current->data; // Возвращаем значение узла
    }
};

int main()
{
    LinkedList<int> list; // Создаем экземпляр списка с элементами типа int

    list.addFirst(1);      // Добавляем 1 в начало списка
    list.addLast(3);       // Добавляем 3 в конец списка
    list.addAtIndex(1, 2); // Добавляем 2 по индексу 1

    // Выводим элементы списка
    std::cout << "Список: ";
    for (int i = 0; i < 3; i++)
    {
        std::cout << list.findByIndex(i) << " ";
    }
    std::cout << std::endl;

    list.updateAtIndex(1, 4); // Обновляем элемент на индексе 1
    list.deleteLast();        // Удаляем последний элемент

    // Выводим элементы списка после обновления и удаления
    std::cout << "Обновленный список: ";
    for (int i = 0; i < 2; i++)
    {
        std::cout << list.findByIndex(i) << " ";
    }
    std::cout << std::endl;

    return 0;
}
