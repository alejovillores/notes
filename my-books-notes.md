# Clean Code

## Meaningful Names

The name of a variable, function, or class, should answer all the big questions. **It should tell you why it exists, what it does, and how it is used**. If a name requires a comment, then the name does not reveal its intent.

`int d; // elapsed time in days`

In this case, d not reveals nothing.

Example of code without meaningful names

```java
public List<int[]> getThem() {
   List<int[]> list1 = new ArrayList<int[]>();
   for (int[] x : theList)
      if (x[0] == 4)
         list1.add(x);

   return list1;
}
```

vs

Example of code with meaningful names

```java
public List<int[]> getFlaggedCells() {
   List<int[]> flaggedCells = new ArrayList<int[]>();
   for (int[] cell : gameBoard)
      if (cell[STATUS_VALUE] == FLAGGED)
         flaggedCells.add(cell);
   return flaggedCells;
}
```

### Avoid Disinformation

Avoid leaving false clues that obscure the meaning of code. Do not refer to a grouping of accounts as an accountList unless it’s actually a List.

```java
List<Account> accountList = new ArrayList(); // This is not good

List<Account> accounts = new ArrayList(); // This is good
```

_"Spelling similar concepts similarly is information. Using inconsistent spellings is dis-
information."_\

If names must be different, then they should also mean something different. So **pick one word per concept.**

```java
public int calculateCost(String location){

   int artistMoney = this.artist.calculatePrice();
   int locationCash = this.search(location).calculateCharge();

   return artistMoney + locationCash
}
```

In this case, cost, price, money, cash, charge means the same so they must have the same name so that it keeps the code simple and concise

```java
public int calculateCost(String location){

   int artistCost = this.artist.calculateCost();
   int locationCost = this.search(location).calculateCost();

   return artistCost + locationCost
}
```

### Use Pronounceable Names

If you can’t pronounce it, you can’t discuss it without sounding like an idiot.

How can be possible to guess that `genymdhms` means generation date, year, month, day, hour, minute, and second ? **Impossible**

So what would a better name be?

```java
class DtaRcrd102 {
   private Date genymdhms;
   private Date modymdhms;
   private final String pszqint = "102";
   /* ... */
};

to

class Customer {
   private Date generationTimestamp;
   private Date modificationTimestamp;;
   private final String recordId = "102";
   /* ... */
};

```

### Use Searchable Names

Single-letter names can ONLY be used as local vari-
ables inside short methods._"The length of a name should correspond to the size of its scope"_.

If a variable or constant might be seen or used in multiple places in a body of code,
it is imperative to give it a search-friendly name.

```java
for (int j=0; j<34; j++) {
   s += (t[j]*4)/5;
}

to

const int WORK_DAYS_PER_WEEK = 5;
int realDaysPerIdealDay = 4;
int sum = 0;

for (int j=0; j < NUMBER_OF_TASKS; j++) {
   int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
   int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
   sum += realTaskWeeks;
}
```

### Interfaces and Implementations

Don't use IInterface, just Interface

When you are using some known pattern, it is good to chose a name for the variables that represents the patter that is it used.

```java
// If we are using a Abstract Factory
class UserFactory

// If we are using a Singleton
class LoggeerSingleton
```

### Classes and objects

Classes and objects should have noun or noun phrase names like `Customer, WikiPage,
Account, and AddressParser`. Avoid words like `Manager, Processor, Data, or Info` in the name
of a class. A class name should not be a verb.

### Methods

Should have verb or verb phrase names like `postPayment, deletePage, or save`.

Accessors, mutators, and predicates should be named for their value and prefixed with `get`,
`set`, and `is`.
