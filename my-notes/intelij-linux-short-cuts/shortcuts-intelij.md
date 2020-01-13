#### Import and Export Intelij key map settings
*  File --> export settings --> chose key maps . It will create a zip file 
*  File --> import settings --> chose  the created zip file 


#### Navigation

*  Find class / file : CTRL + SHIFT + T
*  Find file / file : CTRL + SHIFT + R
*  Find a text content in path: CTRL H
*  Go to a line: CTRL + L 
*  Navigation open files: ALT + <--  or altl + --> 
*  Find uses: CTRL + G

#### Find
* find code references: F7 (with fn) + option 

#### Edit

* rename a class: ALT + SHIFT + R
* auto complte: CTRL + space
* reformat code : CTRL + SHIFT + F
* create constructors and other methods: ???
* imports : CTRL + SHIFT + O 
* delete a line of code : cursor at the begging of the line CTRL + D
* duplicate a line of code : ???

* lowercase and uppercase : CTRL + SHIFT + U
* colum selection mode : ALT + SHIFT + INSERT
* go to implementations: select the method/class + F3

####  Generate code
* surround with : select the code and cmd + option + t 


#### Windows
* Open settings:  ctrl + alt + s
* Open project settings:  ctrl + alt + shift + s
* Open Module settings: F12 :

####  Code analise intellij ultimate 

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
