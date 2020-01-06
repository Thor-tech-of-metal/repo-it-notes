#### Navigation

*  Find class / file : cmd + shift + O
*  Find everything: double-click the big shift on the right
*  Find a text content in path: cmd + shift + F
*  Go to a line: cmd + L 
*  Navigation open files: cmd + [  or cmd + ]
*  Navigation in the code: highlight the method or attribute + cmd + click
*  Find uses: option + Fn + F7
*  Bring project tree: cmd + 1
*  Bring class structure : cmd + 7
*  Go to class implementation not interface: option + cmd + B

#### Find
* find code references: F7 (with fn) + option 

#### Edit
* replace in file : cmd + R
* rename a class: Fn + shift + f6
* auto complte: option + enter
* reformat code : option + cmd + L
* create constructors and other methods: cmd + n
* imports : control + option + O 
* duplicate a line of code : cmd + d
* lowercase and uppercase : cmd + shift u
* colum selection mode : cmd + shift + 8

####  Generate code
* surround with : select the code and cmd + option + t

#### Windows
* Open project settings: cmd + ,
* Open Module settings: cmd + :

####  Code analise

* Setup your analise level. Settings--> Editor--> inspection, in the search add "Duplication",
  Then go to the section that you wish to update  for instance java  and click the duplication level you wish to add.

* **General analyze ** Go to Analyze--> Inspect Code.

* **Method body duplication**: highlight the method, right click, Refactor, find and Replace Code Duplication. 
It will find something like this:
```java
    public void method() {
        int a = 1;
        int b = 2;
        int c = a+b;
        int d = b+c;
    }
    private int add(int a, int b) {
        return a+b;
    }
```

* **Find duplicated code in a class**: Go to Analyze--> Locate Duplicates.
It will find something like this:
```java
public String createString(final String value){
        if (value ==  null){
            throw new NullPointerException("value must NOT be null.");
        }
        final StringBuffer sb = new StringBuffer();
        sb.append("A");
        sb.append("B");
        sb.append("C");
        addSomeSpecialThings(value, sb);
        sb.append("Z");
        return sb.toString();
    }


    public String createString1(final String value){
        if (value ==  null){
            throw new NullPointerException("value must NOT be null.");
        }
        final StringBuffer sb = new StringBuffer();
        sb.append("A");
        sb.append("B");
        return sb.toString();
    }
``` 
* **Find repeated code** in a old fashion way. Highlight 2 or 3 lines of code and .. Control/ Command F