# Linked_List

## code
```
#include<iostream>
using namespace std;

//Create a Node structure
struct Node {
    int data;
    Node* next;
   
    Node(int value) {
        data = value;
        next = nullptr;
    }
};

// Linked List class
class LinkedList {
private:
    Node* head;
    Node* AV = nullptr;
public:
    LinkedList() {
        head = nullptr;
    }

    void Delete(Node* x, Node* y) {

        if (y == nullptr) head = x-> next;
        else y -> next = x-> next;
        delete x;
    }
    // Delete the value
    void deleteValue(int value) {

        Node* current = head;
        Node* previous = nullptr;

        while (current != nullptr) {

            if (current->data == value) {
                Delete(current, previous);
                return;
            }

            previous = current;
            current = current->next;
        }

        cout << "Value not found!" << endl;
    }

    // Insert node at the end
    void insert(int value) {
        Node* newNode = new Node(value);

        if (head == nullptr) {
            head = newNode;
            return;
        }

        Node* temp = head;

        while (temp->next != nullptr) {
            temp = temp->next;
        }

        temp->next = newNode;
    }

    

    // Display linked list
    void display() {
        Node* temp = head;

        while (temp != nullptr) {
            cout << temp->data << " -> ";
            temp = temp->next;
        }

        cout << "NULL" << endl;
    }
    void invert(Node*& s) {

        Node* r;
        Node* q;
        Node* p;

        r = nullptr;
        q = nullptr;
        p = s;

        while (p != nullptr) {

            r = q;
            q = p;
            p = p->next;

            q->next = r;
        }

        s = q;
    }

  // call insert
    void reverse() {
        invert(head);
    }

    
    
    void displayAV() {

        Node* temp = AV;

        cout << "AV List: ";

        while (temp != nullptr) {
            cout << temp->data << " -> ";
            temp = temp->next;
        }

        cout << "NULL\n";
    }

   
};

int main() {
    LinkedList list;
    cout << "Linked List: ";
    list.insert(10);
    list.insert(20);
    list.insert(30);
    list.display();

    int x;
    cin >> x;
    list.deleteValue(x);
    cout <<"After Delete " <<x<<"Linked List: "<<endl;
    list.display();

    list.reverse();

    cout << "\nReversed:\n";
    list.display();

    list.displayAV();

    list.insert(50);

    cout << "\nAfter Insert 50:\n";
    list.display();

    cout << "\nAV after reuse:\n";
    list.displayAV();
    return 0;
}



```

## Output 
Linked List: 10 -> 20 -> 30 -> NULL
10(input)
After Delete 10Linked List:
20 -> 30 -> NULL

Reversed:
30 -> 20 -> NULL
AV List: NULL

After Insert 50:
30 -> 20 -> 50 -> NULL

AV after reuse:
AV List: NULL
