# Clean Code

## Ch2 Meaningful Names

the idea is programmers read code more than they write it so naming variables , methods, classes

### Use Intention-Revealing Names

he name of a variable, function, or class, should answer all the big questions. It. should tell you why it exists, what it does, and how it is used. If a name requires a comment, then the name does not reveal its intent.

ex:

```java
int d; // elapsed time in days
// better name is
int elapsedTimeInDays;
```

### Avoid Disinformation

avoid leaving false clues that obscure the meaning of code

```java
Collection accountList;
// is it really a list
//better name is
Collection accounts;
```

### Make Meaningful Distinctions

It is not sufficient to add number series or noise words, even though the compiler is satisfied. If names must be different, then they should also mean something different.

```java
public static void copyChars(char a1[], char a2[]){}
// better name is
public static void copyChars(char a1[], char a2[]){}
// is it really diffrent 
getActiveAccount();
getActiveAccounts();
getActiveAccountInfo();
```

### Use Pronounceable Names

If you can’t pronounce it, you can’t discuss it without sounding like an idiot.

```java
class DtaRcrd102 {
private Date genymdhms;
private Date modymdhms;
private final String pszqint = "102";
};
// better name is
class Customer {
private Date generationTimestamp;
private Date modificationTimestamp;;
private final String recordId = "102";
};
```

### Use Searchable Names

Single-letter names and numeric constants have a particular problem in that they are not easy to locate across a body of text.

```java
for (int j=0; j<34; j++) {
    s += (t[j]*4)/5;
}
// better name is
int realDaysPerIdealDay = 4;
const int WORK_DAYS_PER_WEEK = 5;
int sum = 0;
for (int j=0; j < NUMBER_OF_TASKS; j++) {
    int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
    int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
    sum += realTaskWeeks;
}
```

### Avoid Encodings

### Member Prefixes

You also don’t need to prefix member variables with m_ anymore. Your classes and functions should be small enough that you don’t need them.

```java
public class Part {
    private String m_dsc; // The textual description
    void setName(String name) {
        m_dsc = name;
    }
}
public class Part {
    String description;
    void setDescription(String description) {
        this.description = description;
    }
}
```

### Class Names

Classes and objects should have noun or noun phrase names like `Customer`, `WikiPage `, `Account` , and `AddressParser` . Avoid words like `Manager` , `Processor` ,`Data`, in the name of a class. A class name should not be a verb.

### Method Names

Methods should have verb or verb phrase names like postPayment , deletePage , or save .

### Pick One Word per Concept

it’s confusing to have `fetch` , `retrieve`, and `get` as equivalent methods of different classes. just pick one

### Don’t Pun

Avoid using the same word for two purposes. Using the same term for two different ideas is essentially a pun.

ex using `add` for both addition and inserting into collection

### Use Solution Domain Names

using cs terms like collection names (`queue`, `stack`) or pattern names (`reducer`)

### Use Problem Domain Names

when there is not a cs name

### Add Meaningful Context

Imagine that you have variables named `firstName` ,`lastName` , `street` , `state` , and `zipcode` . 
You can add context by using prefixes: `addrFirstName` , `addrLastName` , `addrState`

## Ch3 Functions

### Small

The first rule of functions is that they should be small. The second rule of functions is that they should be smaller than that.

### Blocks and Indenting

if statements, else statements, while statements, and so on should be one line long. Probably that line should be a function call. 

the indent level of a function should not be greater than one or two

### Do One Thing

***FUNCTIONS SHOULD DO ONE THING . THEY SHOULD DO IT WELL .THEY SHOULD DO IT ONLY .***

Should be described by small paragraph

have one level of abstraction

have one section

```
RenderPageWithSetupsAndTeardowns, we check to see whether the page is a
test page and if so, we include the setups and teardowns. 
In either case we render the page in HTML.
```

## One Level of Abstraction

statements within our function are all at the same level of abstraction

#### The Stepdown Rule

We want every function to be followed by those at the next level of abstraction so that we can read the program, descending one level of abstraction at a time as we read down the list of functions.

```
To include the setups and teardowns, we include setups, then we include the test page con-
tent, and then we include the teardowns.
To include the setups, we include the suite setup if this is a suite, then we include the
regular setup.
To include the suite setup, we search the parent hierarchy for the “SuiteSetUp” page
and add an include statement with the path of that page.
To search the parent. . .
```

### Switch Statements

Avoid if possible replace it with inheritance or polymorphism

```java
public Money calculatePay(Employee e) throws InvalidEmployeeType {
   switch (e.type) {
      case COMMISSIONED:
         return calculateCommissionedPay(e);
      case HOURLY:
         return calculateHourlyPay(e);
      case SALARIED:
         return calculateSalariedPay(e);
      default:
         throw new InvalidEmployeeType(e.type);
   }
}
```

```java
public abstract class Employee {
   public abstract boolean isPayday();
   public abstract Money calculatePay();
   public abstract void deliverPay(Money pay);
}

public interface EmployeeFactory {
   public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType;
}

public class EmployeeFactoryImpl implements EmployeeFactory {
   public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType {
      switch (r.type) {
         case COMMISSIONED:
            return new CommissionedEmployee(r) ;
         case HOURLY:
            return new HourlyEmployee(r);
         case SALARIED:
            return new SalariedEmploye(r);
         default:
            throw new InvalidEmployeeType(r.type);
      }
   }
}
```

### Use Descriptive Names

- The smaller and more focused a function is, the easier it is to choose a descriptive name.

- Don’t be afraid to make a name long

- Choosing descriptive names will clarify the design of the module in your mind and help you to improve it

- Be consistent in your names. Use the same phrases, nouns, and verbs in the function names you choose for your modules

### Function Arguments

- The ideal number of arguments for a function is zero (niladic).

- Next comes one (monadic), followed closely by two (dyadic).

- Three arguments (triadic) should be avoided where possible.

- More than three (polyadic) requires very special justification

#### Minadic

- asking a question about that argument
  
  - ```java
    boolean fileExists(“MyFile”)
    ```

- transforming argument into something else and returning it
  
  - ```java
      InputStream fileOpen(“MyFile”)
    ```

- event handler methods with no output args
  
  - ```java
    void passwordAttemptFailedNtimes(int attempts)
    ```

- Try to avoid any monadic functions that don’t follow these forms

#### Flag Arguments

Flag arguments are ugly. It immediately complicates the signature of the method, loudly proclaiming that this function does more than one thing. 

#### Dyadic

- A function with two arguments is harder to understand than a monadic function

- the two arguments should be ordered components of a single value

- should have either a natural cohesion, or a natural ordering.
  
  - ```java
    Point p = new Point(0,0);
    ```

- should be converted to monadic if possible

#### Triads

- should be avoided

#### Argument Objects

When a function seems to need more than two or three arguments, it is likely that some of those arguments ought to be wrapped into a class of their own

```java
Circle makeCircle(double x, double y, double radius);
Circle makeCircle(Point center, double radius);
```

#### Argument Lists

- passing a variable number of arguments into a function.

- they are equivalent to a single argument

- all rules applies

```java
void monad(Integer... args);
void dyad(String name, Integer... args);
void triad(String name, int count, Integer... args);
```

### Have No Side Effects

- Side effects are lies. Your function promises to do one thing, but it also does other hidden things

- they are devious and damaging mistruths that often result in strange
  temporal couplings and order dependencies
  
  ```java
  public class UserValidator {
     private Cryptographer cryptographer;
     public boolean checkPassword(String userName, String password) {
        User user = UserGateway.findByName(userName);
        if (user != User.NULL) {
           String codedPhrase = user.getPhraseEncodedByPassword();
           String phrase = cryptographer.decrypt(codedPhrase, password);
           if ("Valid Password".equals(phrase)) {
              Session.initialize();
              return true;
           }
        }
        return false;
     }
  }
  ```

#### Output Arguments

Arguments are most naturally interpreted as inputs to a function not as output

```java
// Does this function append s as the footer to something? 
// does it append some footer to s ?
appendFooter(s);
```

If your function must change the state of something, have it change the state of its owning object

```java
report.appendFooter();
```

### Command Query Separation

- Functions should either do something or answer something, but not both

- change the state of an object

- return some information about the object

```java
// This function sets the value of a named attribute
// returns true if it is successful 
// false if no such attribute exists
public boolean set(String attribute, String value);
```

should be separated

```java
// check if attribute exits
public boolean attributeExits(Stirng attribute);
// only set the attribute
public void set(String attribute, String value);
```

### Prefer Exceptions to Returning Error Codes

- error code add unnecessary confusion

- add deeply structure statements

```java
if (deletePage(page) == E_OK) {
   if (registry.deleteReference(page.name) == E_OK) {
      if (configKeys.deleteKey(page.name.makeKey()) == E_OK){
         logger.log("page deleted");
      } else {
         logger.log("configKey not deleted");
      }
   } else {
      logger.log("deleteReference from registry failed");
   }
} else {
   logger.log("delete failed");
   return E_ERROR;
}
```

```java
try {
   deletePage(page);
   registry.deleteReference(page.name);
   configKeys.deleteKey(page.name.makeKey());
}
catch (Exception e) {
   logger.log(e.getMessage());
}
```

### Extract Try/Catch Blocks

- try catch blocks are complex

- function should only has a try catch block

```java
public void delete(Page page) {
   try {
      deletePageAndAllReferences(page);
   }
   catch (Exception e) {
      logError(e);
   }
}
private void deletePageAndAllReferences(Page page) throws Exception {
   deletePage(page);
   registry.deleteReference(page.name);
   configKeys.deleteKey(page.name.makeKey());
}
private void logError(Exception e) {
   logger.log(e.getMessage());
}
```

### DRY - Don’t Repeat Yourself

- the duplication is a problem because it bloats the code

- reduction of that duplication enhance readability

- Duplication may be the root of all evil in software.

- OOP , FP are invented to remove duplications

## CH4 - Comments

- comments aren't pure good

- should only express what can't be expressed with code

- rarely change so with time they don't express what the code actually do

- Don't make up for bad code

- better clean it not comment it

```java
// Check to see if the employee is eligible for full benefits
if ((employee.flags & HOURLY_FLAG) &&(employee.age > 65))
```

```java
if (employee.isEligibleForFullBenefits())
```

### Good Comments

### Legal comments

- code standard

- copyright and authorship

#### Informative Comments

- provide basic info with comment

```java
// format matched kk:mm:ss EEE, MMM dd, yyyy
Pattern timeMatcher = 
    Pattern.compile("\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");
```

#### Explanation of Intent

provides the intent behind a decision for the implementation

```java
public int compareTo(Object o)
{
    if(o instanceof WikiPagePath)
    {
        WikiPagePath p = (WikiPagePath) o;
        String compressedName = StringUtil.join(names, "");
        String compressedArgumentName = StringUtil.join(p.names, "");
        return compressedName.compareTo(compressedArgumentName);
    }
    return 1; // we are greater because we are the right type.
}
```

#### Clarification

- when the code is difficult to read

- can be risky to use because no one will look at the code

```java
assertTrue(a.compareTo(a) == 0); // a == a
assertTrue(a.compareTo(b) != 0); // a != b
```

#### Warning of Consequences

```java
// Don't run unless you
// have some time to kill.
public void _testWithReallyBigFile()
{
writeLinesToFile(10000000);
response.setBody(testFile);
response.readyToSend(this);
String responseString = output.toString();
assertSubString("Content-Length: 1000000000", responseString);
assertTrue(bytesSent > 1000000000);
}
```

#### TODO

- TODOs are jobs that should be done, but for some reason can’t do at the moment.

- scan through them regularly and eliminate the ones you can.

```java
//TODO-MdM these are not needed
// We expect this to go away when we do the checkout model
protected VersionInfo makeVersion() throws Exception
{
return null;
}
```

#### Javadocs in Public APIs

### Bad Comments

#### Mumbling

- you shouldn't comment because you feel need to

- if you do make it good

whats this comment really mean

```java
public void loadProperties()
{
try
    {
    String propertiesPath = propertiesLocation + "/" + PROPERTIES_FILE;
    FileInputStream propertiesStream = new FileInputStream(propertiesPath);
    loadedProperties.load(propertiesStream);
    }
    catch(IOException e)
    {
    // No properties files means all defaults are loaded
    }
}
```

#### Redundant Comments

- comment should be more informative than the code

- It does not justify the code

- provide intent or rationale. 

- It is easier to read than the code

- other than this its redundant

```java
/**
* The processor delay for this component.
*/
protected int backgroundProcessorDelay = -1;
/**
* The lifecycle event support for this component.
*/
protected LifecycleSupport lifecycle =
new LifecycleSupport(this);
/**
* The container event listeners for this Container.
*/
protected ArrayList listeners = new ArrayList();
```

#### Misleading Comments

what the function really does that it returns it closed is true if not it waits for timeout and then throw exception if the closed still false

```java
// Utility method that returns when this.closed is true. Throws an exception
// if the timeout is reached.
public synchronized void waitForClose(final long timeoutMillis) throws Exception
{
    if(!closed)
    {
    wait(timeoutMillis);
    if(!closed)
    throw new Exception("MockResponseSender could not be closed");
    }
}
```

#### Mandated Comments

you don't need to comment every thing

```java

/**
*
* @param title The title of the CD
* @param author The author of the CD
* @param tracks The number of tracks on the CD
* @param durationInMinutes The duration of the CD in minutes
*/
public void addCD(String title, String author,
int tracks, int durationInMinutes) {
    CD cd = new CD();
    cd.title = title;
    cd.author = author;
    cd.tracks = tracks;
    cd.duration = duration;
    cdList.add(cd);
}

```

#### Journal comments

it's like log of the file change not needed any more thanks to version control system

#### Noise comments

```java
/** The day of the month. */
private int dayOfMonth;
/**
* Default constructor.
*/
protected AnnualDateRule() {
}
```

#### Comment instead of function

Don’t Use a Comment When You Can Use a Function or a Variable

```java
// does the module from the global list <mod> depend on the
// subsystem we are part of?
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```

```java
ArrayList moduleDependees = smodule.getDependSubsystems();
String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```

### Closing Brace Comments

- don't use comments for deep nesting

- try refactor instead

### Commented-Out Code

should be removed

#### Nonlocal Information

port may change its unlikely that the comment will change

```java
/**
* Port on which fitnesse would run. Defaults to <b>8082</b>.
*
* @param fitnessePort
*/
public void setFitnessePort(int fitnessePort){
 this.fitnessePort = fitnessePort;
}
```

#### Too mush information

#### Inobvious Connection

The purpose of a comment is to explain code that does not explain itself. It is a pity when a comment needs its own explanation.

What is a filter byte? Does it relate to the +1? Or to the *3? Both? Is a pixel a byte? Why 200?

```java
/*
* start with an array that is big enough to hold all the pixels
* (plus filter bytes), and an extra 200 bytes for header info
*/
this.pngBytes = new byte[((this.width + 1) * this.height * 3) + 200];
```

### Example

```java
/**
 * This class Generates prime numbers up to a user specified
 * maximum. The algorithm used is the Sieve of Eratosthenes.
 * <p>
 * Eratosthenes of Cyrene, b. c. 276 BC, Cyrene, Libya --
 * d. c. 194, Alexandria. The first man to calculate the
 * circumference of the Earth. Also known for working on
 * calendars with leap years and ran the library at Alexandria.
 * <p>
 * The algorithm is quite simple. Given an array of integers
 * starting at 2. Cross out all multiples of 2. Find the next
 * uncrossed integer, and cross out all of its multiples.
 * Repeat untilyou have passed the square root of the maximum
 * value.
 *
 * @author Alphonse
 * @version 13 Feb 2002 atp
 */


class GeneratePrimes {
    /**
     * @param maxValue is the generation limit.
     */
    public static int[] generatePrimes(int maxValue) {
        if (maxValue >= 2) // the only valid case
        {
            // declarations
            int s = maxValue + 1; // size of array
            boolean[] f = new boolean[s];
            int i;
            // initialize array to true.
            for (i = 0; i < s; i++)
                f[i] = true;
            // get rid of known non-primes
            f[0] = f[1] = false;
            // sieve
            int j;
            for (i = 2; i < Math.sqrt(s) + 1; i++) {
                if (f[i]) // if i is uncrossed, cross its multiples.
                {
                    for (j = 2 * i; j < s; j += i)
                        f[j] = false; // multiple is not prime
                }
            }
            // how many primes are there?
            int count = 0;
            for (i = 0; i < s; i++) {
                if (f[i])
                    count++; // bump count.
            }
            int[] primes = new int[count];
            // move the primes into the result
            for (i = 0, j = 0; i < s; i++) {
                if (f[i])
                    // if prime
                    primes[j++] = i;
            }
            return primes; // return the primes
        } else // maxValue < 2
            return new int[0]; // return null array if bad input.
    }
}
```

#### Refactor

```java

```
