# clean-code

This repository will show my perspective on Robert C. Martin's Clean Code book. I will present and compare a few mistakes I used to do before focusing on writing clean code and how I managed to clean the mess eventually. This repository will be mainly focused on highlighting some brightscrip examples, but I will also present some messy code snippets from my old C#/Python projects for a better understanding.

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