# Go 02

## Variable declaration

`var card string = "Ace of Spades"`

Because Go is a statically-typed language, its variable types should be explicitly declared.

JavaScript, which is a dynamically-typed language that can allow any type of value for a variable, will not care whether a variable changes from being a string to a number to a boolean etc.

Go, and other statically-typed languages, MUST always contain the type of value declared.

`card` must always be a string in this case.

### Shorter variable declaration

Go is clever enough to detect what the variable type should be from the initial declaration:
`card := "Ace of Spades"`

This is a quicker, alternate way of declaring this variable. Go figures out that a new variable should be made, base on the assigned data, using `:=`.

### Reassigning a variable

Simply use `=` to redeclare an existing variable, e.g.:
`card = "Queen of Hearts"`

## Some basic Go variable types

- bool: true or false;
- string: "Hi";
- int: "14", "-999";
- float64: "101.010101", "0.000000009", "-100.003".

## func output declaration

In Go, the type of output value should be declared when writing the function:

    func newCard() string {
    return "Eight of Diamonds"
    }

In this example, **string** is declared as the expected output function, as a **string** is being returned from the function.

## Slices and Loops

### Slices

In Go, arrays can actually be two types:

- Array: a fixed-length list of things, which **cannot** grow or shrink;
- Slice: an array that **can** grow or shrink, just like in JavaScript.

In an array or slice, every element **must** be of the same type, e.g. an array of integers, a slice of strings.

To declare a slice:
`cards := [] string {newCard(), "Ace of Hearts"}`
Square brackets are used to declare a slice, its element-type is declared after, followed by the initial elements in curly braces.

### Appending a slice

To add a new value to a slice:

`cards = append(cards, "Six of Spades")`

### Loops

    package main

    import  "fmt"

    func main() {
    	cards := []string{"Ace of Hearts", newCard()}
        cards = append(cards, "Six of Spades")

        for  i, card := range cards {
    	    fmt.Println(i, card)
        }
    }

    func  newCard() string {
        return  "Five of Diamonds"
    }

When `go run main.go` is run in the CLI:

    0 Ace of Hearts
    1 Five of Diamonds
    2 Six of Spades

A loop looks like the following:

    for i, card := range cards {
    	fmt.Println(card)
    }

**i**: index of this element in the array;
**card**: current card we're iterating over;
**range cards**: take the slice of 'cards' and loop over it;
**fmt.Println(card)**: run this one time for each card in the slice.
