# jfiglet

Java implementation of FIGfonts to create ascii art banners.

## Usage
you can use it from command line or from java code

### Maven dependency

add the following maven dependency to your `pom.xml`

```
<dependency>
	<groupId>com.github.enxt</groupId>
	<artifactId>jfiglet</artifactId>
	<version>0.0.8</version>
</dependency>
```

## Usage - code

Then one could use number of `convertOneLine(...)` static methods to do the magic

```
import com.github.enxt.jfiglet.FigletFont;
import java.io.File;

public class App {
  public static void main(String[] args) {
    // using default font standard.flf, obtained from maven artifact
    String asciiArt1 = FigletFont.convertOneLine("hello");
    System.out.println(asciiArt1);
    
    // using font font2.flf, located somewhere in classpath under path /flf/font2.flf
    String asciiArt2 = FigletFont.convertOneLine(FigletFont.class.getResourceAsStream("/flf/font2.flf"), "hello");
    System.out.println(asciiArt2);
    
    asciiArt2 = FigletFont.convertOneLine("classpath:/flf/font2.flf", "hello");     
    System.out.println(asciiArt2);                
    
    // using font font3.flf, located in file system under path /opt/font3.flf
    String asciiArt3 = FigletFont.convertOneLine(new File("/opt/font3.flf"), "hello");     
    System.out.println(asciiArt3);

    asciiArt3 = FigletFont.convertOneLine("/opt/font3.flf", "hello");     
    System.out.println(asciiArt3);

    // using font font4.flf, from www 
    String asciiArt4 = FigletFont.convertOneLine("http://myhost.com/font4.flf", "hello");     
    System.out.println(asciiArt4);                
  }
}
```

## Usage - command line

You can use the jar from the central repo, or use the latest development version from sourcecode;
```
Usage: java -jar jfiglet.jar [-f FLF] MESSAGE
Prints MESSAGE to stdout as ASCII art using Figlet font
Example: java -jar jfiglet.jar -f "/opt/myfont.flf" "Hello World"


Figlet font:
  -f  FLF is font file location within file system, java classpath or www.
      When FLF starts with `http://'|`https://' file will be fetched from WWW,
      if FLF starts from `classpath:' then it will be looked for in JRE classpath,
      otherwise FLF if path to file in file system
```
