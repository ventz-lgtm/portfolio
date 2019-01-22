[Back](https://dhog10.github.io/portfolio/)

## Java
Java was my first programming language. I learned Java mainly during my two year Computing course for college. My experience in Java hugely improved my understanding of OOP concepts, which has massively assisted me in learning new languages such as Lua, C++ and C#. I worked on various projects during my computing course, mainly related to games.

I also continue to program regularly in Java for my University Algorithms Processes & Data (AP&D) module, this involves implementing various algorithms and data structures in Java, such as linked lists, binary trees, searching algorithms and sorting algorithms.

### VEngine
[Source](https://github.com/dhog10/VEngine)

VEngine is a Java project I worked on during my time studying Computing in college. I developed this to improve my ability to program in Java aswel as improving my understanding of basic object management principals for game engines. VEngine is a basic game engine for Java which includes rendering for sprites and gifs, 2D physics rigidbody simulation and collisons between circles and axis aligned rectangles. I gained a better understanding of rigidbody collision response techniques in particular whilst programming this.

This project greatly improved my knowledge in Java, making use of various techniques such as multi threading, lambda and user input. This not only improved my ability with Java, but also improved my general understanding of such concepts, and OOP in general.

I also developed a better understanding of certain game related systems, such as object management, threading, render and tick loops, delta time and rigidbody behaviour.
<video width="480" height="320" controls="controls">
  <source src="images/vengine.mp4" type="video/mp4">
</video>
Demonstration of rigidbody simulation and collision detection between axis aligned rectangles and circles.

### Single Linked List
My implementation of single linked lists for my AP&D Module.

```java
package linkedList.list;

import linkedList.node.SingleLinkNode;

/**
 * Implementation of the List interface, extending the BasicList class
 * A single linked list class, with each node storing a reference to the next node in the list
 *
 * @author Daniel Lush
 * @version November 2018
 * @param <T> type of value to be stored in the list
 */
public class SingleLinkedList <T> extends BasicList<SingleLinkNode<T>,T> implements List<T> {
    /**
     * Return the SingleLinkNode object at a given index
     *
     * @param index index to search for node
     * @return the node at the given index
     * @throws ListAccessError
     */
    private SingleLinkNode<T> getNode(int index) throws ListAccessError{
        if(isEmpty()){throw new ListAccessError("Attempt to index empty list"); }
        if(index < 0){ throw new ListAccessError("Index less than 0"); }

        SingleLinkNode<T> currentNode = getRoot();

        for(int i = 0; i < index; i++){
            currentNode = (SingleLinkNode)currentNode.getNext();
            if(currentNode == null){ throw new ListAccessError("Index out of bounds"); }
        }

        return currentNode;
    }

    /**
     * Inserts a given object to the list at a given position
     *
     * @param index the index at which the new entry should be added.
     * @param value the value to be added.
     * @throws ListAccessError
     */
    @Override
    public void add(int index, T value) throws ListAccessError {
        if(index == 0){
            SingleLinkNode<T> newNode = new SingleLinkNode<T>(value);
            newNode.setNext(getRoot());
            setRoot(newNode);

            return;
        }

        SingleLinkNode<T> currentNode = getNode(index - 1);

        SingleLinkNode<T> newNode = new SingleLinkNode<T>(value);

        SingleLinkNode<T> nextNode = (SingleLinkNode)currentNode.getNext();

        currentNode.setNext(newNode);
        newNode.setNext(nextNode);
    }

    /**
     * Removes an object at the given index from the list
     *
     * @param index the index of the entry to be removed.
     * @return The object which was removed from the list
     * @throws ListAccessError
     */
    @Override
    public T remove(int index) throws ListAccessError {
        if(index == 0){
            SingleLinkNode<T> root = getRoot();
            setRoot((SingleLinkNode)getRoot().getNext());

            return root.getValue();
        }

        SingleLinkNode<T> currentNode = getNode(index - 1);

        SingleLinkNode<T> nextNode = (SingleLinkNode)currentNode.getNext();
        if(nextNode == null){ throw new ListAccessError("Index out of bounds"); }

        currentNode.setNext((SingleLinkNode)nextNode.getNext());
        nextNode.setNext(null);

        return nextNode.getValue();
    }

    /**
     * Gets an object at a given index in the list
     *
     * @param index the index of the entry to be accessed.
     * @return the object at the given index
     * @throws ListAccessError
     */
    @Override
    public T get(int index) throws ListAccessError {
        SingleLinkNode<T> currentNode = getNode(index);
        return currentNode.getValue();
    }
}
```
