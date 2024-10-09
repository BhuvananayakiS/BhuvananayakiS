import java.util.*;
import java.io.*;

class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class LinkedList {
    Node head;

    void add(int data) {
        Node new_node = new Node(data);
        if (head == null) {
            head = new_node;
            return;
        }
        Node curr = head;
        while (curr.next != null)
            curr = curr.next;
        curr.next = new_node;
    }

    void printList() {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }
}

public class Main {
    public static Node reverseList(Node head) {
       if(head.next==null)
       {
           return head;
       }
       Node pre=null;
       Node cur= head;
       Node upc=cur.next;
       while(cur.next !=null)
       {
           cur.next =pre;
           pre=cur;
           cur=upc;
           upc=cur.next;
           
       }
       cur.next=pre;
       pre=cur;
       head=pre;
       return head;
    }

    public static void main(String args[]) {
        Scanner input = new Scanner(System.in);
        LinkedList list = new LinkedList();
        int n = input.nextInt();
        for (int i = 0; i < n; i++) {
            int x = input.nextInt();
            list.add(x);
        }

        list.head = reverseList(list.head);
        list.printList();
    }
}
