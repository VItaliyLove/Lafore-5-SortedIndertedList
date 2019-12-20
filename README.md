s# Lafore-5-SortedInsertedList

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.nio.Buffer;

class Algorithm {

    static class Link {

        public int data;
        public Link next;

        public Link(int newData){
            data = newData;
            next = null;
        }
    }

    static class SortedList{

        private double data;
        private Link first;


        public SortedList()
        {
            first = null;
        }

        public SortedList(Link[] arr)
        {
            first = null;
            for (int i = 0; i < arr.length; i++)
                insert(arr[i]);
        }

        public boolean isEmpty() {
            return (first == null);
        }

        public void insert(Link k) {
            Link current = first;
            Link previous = null;

            while(current != null && k.data < current.data) {
                previous = current;
                current = current.next;
            }
             if (previous == null)
                 first = k;
             else
                 previous.next = k;
             k.next = current;
        }

        public Link remove() {
            Link temp = first;
            first = first.next;
            return temp;
        }


        public void displayList() {
            Link current = first;
            while (current != null) {
                System.out.print(current.data + " ");
                current = current.next;
            }
            System.out.println();
        }

    }

    public static void main(String[] arg) throws IOException {

        Link[] linkArr = new Link[5];
        for (int i = 0; i < 5; i++) {
            Link link = new Link(i);
            linkArr[i] = link;
        }

        for (int i = 0 ; i < 5; i++)
            System.out.print(linkArr[i].data);
        System.out.println();

        SortedList sortedList = new SortedList(linkArr);

        for (int i = 0; i < 5; i++)
            linkArr[i] = sortedList.remove();

        for (int i = 0 ; i < 5; i++)
            System.out.print(linkArr[i].data);
        System.out.println();
    }
}
