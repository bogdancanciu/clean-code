# clean-code

This repository will show my perspective on Robert C. Martin's Clean Code book. I will present and compare a few mistakes I used to do before focusing on writing clean code and how I managed to clean the mess eventually. This repository will be mainly focused on highlighting some BrightScript/BrighterScript examples, but I will also present some messy code snippets from my old C#/Python projects for a better understanding.

## Chapter I. Clean code

The main idea behind the first chapter is to offer an overall perspective of what the book will be focusing on and why clean code is important. Long story short - there will always be code, so the cost of creating a mess will end up being extremely hard maintainable or not exactly maintainable anymore, so the mess will keep growing over time. Clean code should be understandable by developers other than the one who initially created it. In order to do so, it's mandatory to keep in mind some good practices the moment you write code. The code will most likely not be clean in its first implementation, that's why it has to be reviewed by the author and cleaned up considering the "best practices". Best practices are some heavy words here, some cases may need special attention to be made clean, while others could easily be cleaned up following some basic general accepted rules. The main idea behind this book is to offer more than one perspective on what clean code is, how to write clean code and how to maintain your code clean.

## Chapter II. Meaningful Names

### 1. Use suggestive, meaningful names
Always avoid using names that are meaningless, misleading, or confusing. Confusing names can result from multiple causes, some of them being: names containing keywords, noise words, abbreviations, deprecated or personal codifications.
```
    customerAgeInt = 21 - adding 'Int' keyword to make it clear the current variable is an integer
    theCustomer = createObject("RoSGNode","ContentNode") - adding 'the' noise word
    ca = 51 - abbreviation, or mental mapping for 'customer age'
    m_customerAge = 25 - adding deprecated 'm_' to the variable, to make it visible that it is a private member of a class
    hmCustomer = {} - adding 'hm' personal coddification to the variable, to signal that it is an HashMap
```
All examples presented above are bad practices and they should be avoided. In order to keep clean and meaningful names, I always check the variable and function names while self-reviewing my pull requests.

### 2. Avoid overloading/underloading name concepts
What I mean by over/underloading is you should not use the same naming concept for more than one specific funcitonality or use multiple concepts for the same functionality.

For example, if you write a method that adds two numbers:
```
    function add(firstNumber, secondNumber) as Dynamic
        return firstNumber + secondNumber
    end function
```
It would be bad practice to create another method named "add" for adding(appending) numbers to a list. This was an example of when a naming concept is overloaded in a messy way.

What I mean by underloading, is when working with a specific naming concept that describes functionality in some cases, and then, at some point in the future, defining another naming concept that is meant to do the same specific thing.

For example, if you write a function that fetches some data from the API:
```
    function fetchCustomers(serverUri as String) as Object
        request = createObject("roUrlTransfer")
        request.setUrl(serverUri)
        apiResponse = ParseJson(request.GetToString())
        
        return apiResponse
    end function
```
It would be bad practice to create another function in a separate class/module, that also fetches data from the API and name it "getProducts()" for instance. In this case, we use multiple concepts - fetch and get to express the same functionality.

### 3. Avoid giving too much context to a name
Giving too much or too little context to a name are a bad practice. What I mean by too much context is when developers tend to name variables in a way that makes you ask why was it necessary to go that far with namings.

Let's assume we have the following class: (Note: This example is going to be a BrighterScript example, that's why I'm involving classes.)
```
    class Customer
        private customerAge
        private customerAddress
        .
        .
        .
    end class
```
In this case, there is no point in naming the variable that stores the customer's age customerAge. Since we are inside the Customer class, it's pretty clear that all the concepts inside this class are customer related, so offering this type of context, in this case, is not clean.

## Chapter III. Functions

### 1. Functions should be small and on point