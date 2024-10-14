### 1. Exception Handling (5 marks)

Exception handling in Java is a mechanism to deal with runtime errors or exceptional situations that may occur during program execution. It allows you to separate error-handling code from the main logic of your program. The main components of exception handling are:

1. **try**: Contains the code that might throw an exception
2. **catch**: Handles the exception if it occurs
3. **finally**: Executes regardless of whether an exception occurs or not
4. **throw**: Manually throws an exception
5. **throws**: Declares that a method might throw certain exceptions

Example:

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
} finally {
    System.out.println("This always executes");
}
```

### 2. I/O Exception (5 marks)

`IOException` is a **checked** exception in Java that occurs during Input/Output operations. It's thrown when an I/O operation fails or is interrupted. Common scenarios include:

- File not found
- Unable to read from or write to a file
- Network connection issues

Example:

```java
import java.io.*;

public class FileReadExample {
    public static void main(String[] args) {
        try {
            FileReader file = new FileReader("nonexistent.txt");
            BufferedReader reader = new BufferedReader(file);
            String line = reader.readLine();
            reader.close();
        } catch (IOException e) {
            System.out.println("An I/O error occurred: " + e.getMessage());
        }
    }
}
```
* `FileNotFoundException`
* `SecurityException`
### 3. Labels and Their Examples (5 marks)

In Java AWT, Labels are used to display a single line of read-only text. They are non-interactive components often used to provide descriptions or instructions.

Example:

```java
import java.awt.*;

public class LabelExample {
    public static void main(String[] args) {
        Frame frame = new Frame("Label Example");
        Label label1 = new Label("This is a label");
        Label label2 = new Label("Aligned Center", Label.CENTER);
        Label label3 = new Label("Right Aligned", Label.RIGHT);

        frame.setLayout(new FlowLayout());
        frame.add(label1);
        frame.add(label2);
        frame.add(label3);

        frame.setSize(300, 100);
        frame.setVisible(true);
    }
}
```

### 4. Buttons and Their Examples (5 marks)

Buttons in Java AWT are interactive components that trigger an action when clicked. They are commonly used for user interactions like submitting forms or initiating processes.

Example:

```java
import java.awt.*;
import java.awt.event.*;

public class ButtonExample {
    public static void main(String[] args) {
        Frame frame = new Frame("Button Example");
        Button button = new Button("Click Me");

        button.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                System.out.println("Button clicked!");
            }
        });

        frame.add(button);
        frame.setSize(200, 100);
        frame.setLayout(new FlowLayout());
        frame.setVisible(true);
    }
}
```

### 5. Working with Frame Window (5 marks)

A Frame in Java AWT is a top-level window with a title and a border. It's the main container for other AWT components. Key aspects of working with frames include:

1. Creating a frame
2. Setting size and position
3. Adding components
4. Handling window events
5. Setting visibility

Example:

```java
import java.awt.*;
import java.awt.event.*;

public class FrameExample extends Frame {
    public FrameExample() {
        setTitle("Frame Example");
        setSize(300, 200);
        setLayout(new FlowLayout());

        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent we) {
                System.exit(0);
            }
        });

        Button button = new Button("Click Me");
        add(button);
    }

    public static void main(String[] args) {
        FrameExample frame = new FrameExample();
        frame.setVisible(true);
    }
}
```

### 6. List and Their Examples (5 marks)

The List component in Java AWT allows users to select one or more items from a scrollable list of text items. It's useful for presenting multiple options to users.

Example:

```java
import java.awt.*;
import java.awt.event.*;

public class ListExample {
    public static void main(String[] args) {
        Frame frame = new Frame("List Example");
        List list = new List(4, true);  // 4 visible rows, multiple selection allowed

        list.add("Item 1");
        list.add("Item 2");
        list.add("Item 3");
        list.add("Item 4");
        list.add("Item 5");

        list.addItemListener(new ItemListener() {
            public void itemStateChanged(ItemEvent ie) {
                String[] selected = list.getSelectedItems();
                System.out.println("Selected items: " + String.join(", ", selected));
            }
        });

        frame.add(list);
        frame.setSize(200, 150);
        frame.setLayout(new FlowLayout());
        frame.setVisible(true);
    }
}
```

### 7. Scrollbars and Their Examples (5 marks)

Scrollbars in Java AWT are used to select from a range of values. They can be vertical or horizontal and are often used for navigation or adjusting values.

Example:

```java
import java.awt.*;
import java.awt.event.*;

public class ScrollbarExample {
    public static void main(String[] args) {
        Frame frame = new Frame("Scrollbar Example");
        Scrollbar vertical = new Scrollbar(Scrollbar.VERTICAL, 0, 10, 0, 100);
        Scrollbar horizontal = new Scrollbar(Scrollbar.HORIZONTAL, 0, 10, 0, 100);

        AdjustmentListener listener = new AdjustmentListener() {
            public void adjustmentValueChanged(AdjustmentEvent e) {
                System.out.println("Current value: " + e.getValue());
            }
        };

        vertical.addAdjustmentListener(listener);
        horizontal.addAdjustmentListener(listener);

        frame.add(vertical, BorderLayout.EAST);
        frame.add(horizontal, BorderLayout.SOUTH);
        frame.setSize(300, 200);
        frame.setVisible(true);
    }
}
```

### 8. Event Handling Methods (5 marks)

Event handling in Java AWT involves responding to user actions or system events. The main steps in event handling are:

1. Implement an appropriate listener interface
2. Register the listener with the component
3. Implement the methods of the listener interface

Common event handling methods include:

- `actionPerformed`() for ActionListener
- `itemStateChanged`() for `ItemListener`
- `windowClosing`() for `WindowListener`
- `mouseClicked`() for `MouseListener`

Example:

```java
import java.awt.*;
import java.awt.event.*;

public class EventHandlingExample {
    public static void main(String[] args) {
        Frame frame = new Frame("Event Handling Example");
        Button button = new Button("Click Me");

        button.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                System.out.println("Button clicked!");
            }
        });

        frame.addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent we) {
                System.exit(0);
            }
        });

        frame.add(button);
        frame.setSize(200, 100);
        frame.setLayout(new FlowLayout());
        frame.setVisible(true);
    }
}
```

### 9. Text Area and Their Examples (5 marks)

`TextArea` in Java AWT is a multi-line text input component that allows users to enter or edit text. It's useful for collecting larger amounts of text input.

Example:

```java
import java.awt.*;
import java.awt.event.*;

public class TextAreaExample {
    public static void main(String[] args) {
        Frame frame = new Frame("TextArea Example");
        TextArea textArea = new TextArea("Enter text here", 5, 30);

        Button button = new Button("Get Text");
        button.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                System.out.println("Text in TextArea: " + textArea.getText());
            }
        });

        frame.setLayout(new FlowLayout());
        frame.add(textArea);
        frame.add(button);
        frame.setSize(300, 200);
        frame.setVisible(true);
    }
}
```

### 10. Flow Layout and Their Examples (5 marks)

FlowLayout is a layout manager that arranges components in a directional flow, much like lines of text in a paragraph. Components are arranged in a top-to-bottom, left-to-right flow.

Example:

```java
import java.awt.*;

public class FlowLayoutExample {
    public static void main(String[] args) {
        Frame frame = new Frame("FlowLayout Example");
        frame.setLayout(new FlowLayout(FlowLayout.LEFT, 10, 10));

        for (int i = 1; i <= 5; i++) {
            frame.add(new Button("Button " + i));
        }

        frame.setSize(300, 150);
        frame.setVisible(true);
    }
}
```

### 11. I/O Stream and Their Examples (10 marks)

I/O Streams in Java are used to read from and write to various sources and destinations. They are categorized into two main types:

1. Byte Streams: For handling binary data (e.g., FileInputStream, FileOutputStream)
2. Character Streams: For handling text data (e.g., FileReader, FileWriter)

Examples:

1. `FileInputStream` and `FileOutputStream` (Byte Streams):

```java
import java.io.*;

public class ByteStreamExample {
    public static void main(String[] args) {
        try {
            FileInputStream in = new FileInputStream("input.txt");
            FileOutputStream out = new FileOutputStream("output.txt");
            int c;
            while ((c = in.read()) != -1) {
                out.write(c);
            }
            in.close();
            out.close();
        } catch (IOException e) {
            System.out.println("I/O Error: " + e.getMessage());
        }
    }
}
```

2. FileReader and FileWriter (Character Streams):

```java
import java.io.*;

public class CharacterStreamExample {
    public static void main(String[] args) {
        try {
            FileReader reader = new FileReader("input.txt");
            FileWriter writer = new FileWriter("output.txt");
            int c;
            while ((c = reader.read()) != -1) {
                writer.write(c);
            }
            reader.close();
            writer.close();
        } catch (IOException e) {
            System.out.println("I/O Error: " + e.getMessage());
        }
    }
}
```

3. `BufferedReader` and `BufferedWriter` (Buffered Character Streams):

```java
import java.io.*;

public class BufferedStreamExample {
    public static void main(String[] args) {
        try {
            BufferedReader reader = new BufferedReader(new FileReader("input.txt"));
            BufferedWriter writer = new BufferedWriter(new FileWriter("output.txt"));
            String line;
            while ((line = reader.readLine()) != null) {
                writer.write(line);
                writer.newLine();
            }
            reader.close();
            writer.close();
        } catch (IOException e) {
            System.out.println("I/O Error: " + e.getMessage());
        }
    }
}
```

### 12. Checkbox and Checkbox Group and Their Examples (10 marks)

Checkboxes in Java AWT are used to create options that can be selected or deselected. Checkbox groups allow for creating mutually exclusive options (radio buttons).

1. Checkbox Example:

```java
import java.awt.*;
import java.awt.event.*;

public class CheckboxExample {
    public static void main(String[] args) {
        Frame frame = new Frame("Checkbox Example");
        Checkbox cb1 = new Checkbox("Option 1");
        Checkbox cb2 = new Checkbox("Option 2", true);  // Initially selected

        cb1.addItemListener(new ItemListener() {
            public void itemStateChanged(ItemEvent e) {
                System.out.println("Option 1: " + (e.getStateChange() == ItemEvent.SELECTED ? "Selected" : "Deselected"));
            }
        });

        frame.setLayout(new FlowLayout());
        frame.add(cb1);
        frame.add(cb2);
        frame.setSize(200, 100);
        frame.setVisible(true);
    }
}
```

2. Checkbox Group Example (Radio Buttons):


```java
import java.awt.*;
import java.awt.event.*;

public class CheckboxGroupExample {
    public static void main(String[] args) {
        Frame frame = new Frame("Checkbox Group Example");
        CheckboxGroup group = new CheckboxGroup();
        Checkbox cb1 = new Checkbox("Option 1", group, false);
        Checkbox cb2 = new Checkbox("Option 2", group, true);
        Checkbox cb3 = new Checkbox("Option 3", group, false);

        ItemListener listener = new ItemListener() {
            public void itemStateChanged(ItemEvent e) {
                if (e.getStateChange() == ItemEvent.SELECTED) {
                    System.out.println("Selected: " + ((Checkbox)e.getSource()).getLabel());
                }
            }
        };

        cb1.addItemListener(listener);
        cb2.addItemListener(listener);
        cb3.addItemListener(listener);

        frame.setLayout(new FlowLayout());
        frame.add(cb1);
        frame.add(cb2);
        frame.add(cb3);
        frame.setSize(250, 100);
        frame.setVisible(true);
    }
}
```

### 13. Java AWT Package (10 marks)

The Java Abstract Window Toolkit (AWT) is a set of APIs used to create graphical user interfaces (GUIs) for Java applications. It provides a basic set of tools for creating windows, buttons, menus, and other interface elements.

Key features of Java AWT:

1. Platform-dependent: AWT components are implemented using native peer components.
2. Heavyweight components: AWT components are rendered by the underlying operating system.
3. Basic set of GUI components: Includes Frame, Button, TextField, Label, Checkbox, etc.
4. Layout managers: For organizing components within containers.
5. Event handling: To respond to user actions and system events.

Main components of AWT:

1. Container classes: Frame, Panel, Dialog
2. Component classes: Button, Label, Checkbox, `TextField`, `TextArea`, List, Choice
3. Layout managers: `FlowLayout`, `BorderLayout`, `GridLayout`, `CardLayout`
4. Event handling classes: ActionListener, `ItemListener`, `WindowListener`, etc.

Example demonstrating various AWT components:

```java
import java.awt.*;
import java.awt.event.*;

public class AWTExample {
    public static void main(String[] args) {
        Frame frame = new Frame("AWT Example");
        frame.setLayout(new FlowLayout());

        // Adding various components
        Label label = new Label("Enter your name:");
        TextField textField = new TextField(20);
        Button button = new Button("Submit");
        Checkbox checkbox = new Checkbox("I agree");
        Choice choice = new Choice();
        choice.add("Option 1");
        choice.add("Option 2");
        choice.add("Option 3");

        // Adding components to the frame
        frame.add(label);
        frame.add(textField);
        frame.add(button);
        frame.add(checkbox);
        frame.add(choice);

        // Event handling
        button.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                System.out.println("Name entered: " + textField.getText());
            }
        });

        // Window closing event
        frame.addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent we) {
                System.exit(0);
            }
        });

        frame.setSize(300, 200);
        frame.setVisible(true);
    }
}
```

This example demonstrates the use of various AWT components including Frame, Label, `TextField`, Button, Checkbox, and Choice, along with event handling for button clicks and window closing.

### 14. Layout Managers (10 marks)

Layout Managers in Java AWT are responsible for arranging components within a container. They determine the size and position of components in a GUI. The main layout managers in AWT are:

1. `FlowLayout`
2. `BorderLayout`
3. `GridLayout`
4. `CardLayout`
5. `GridBagLayout`

Let's explore each with examples:

1. `FlowLayout`:
    - Arranges components in a left-to-right, top-to-bottom flow.
```java
import java.awt.*;

public class FlowLayoutExample {
    public static void main(String[] args) {
        Frame frame = new Frame("FlowLayout Example");
        frame.setLayout(new FlowLayout(FlowLayout.LEFT, 10, 10));

        for (int i = 1; i <= 5; i++) {
            frame.add(new Button("Button " + i));
        }

        frame.setSize(300, 100);
        frame.setVisible(true);
    }
}
```

2. `BorderLayout`:
    - Arranges components in five regions: NORTH, SOUTH, EAST, WEST, and CENTER.

```java
import java.awt.*;

public class BorderLayoutExample {
    public static void main(String[] args) {
        Frame frame = new Frame("BorderLayout Example");
        frame.setLayout(new BorderLayout(5, 5));

        frame.add(new Button("North"), BorderLayout.NORTH);
        frame.add(new Button("South"), BorderLayout.SOUTH);
        frame.add(new Button("East"), BorderLayout.EAST);
        frame.add(new Button("West"), BorderLayout.WEST);
        frame.add(new Button("Center"), BorderLayout.CENTER);

        frame.setSize(300, 200);
        frame.setVisible(true);
    }
}
```

3. `GridLayout`:
    - Arranges components in a grid of rows and columns.

```java
import java.awt.*;

public class GridLayoutExample {
    public static void main(String[] args) {
        Frame frame = new Frame("GridLayout Example");
        frame.setLayout(new GridLayout(3, 2, 5, 5));

        for (int i = 1; i <= 6; i++) {
            frame.add(new Button("Button " + i));
        }

        frame.setSize(300, 200);
        frame.setVisible(true);
    }
}
```

4. CardLayout:
    - Shows one component at a time from a set of components.

```java
import java.awt.*;
import java.awt.event.*;

public class CardLayoutExample {
    public static void main(String[] args) {
        Frame frame = new Frame("CardLayout Example");
        CardLayout cardLayout = new CardLayout();
        frame.setLayout(cardLayout);

        Panel card1 = new Panel();
        card1.add(new Label("Card 1"));
        Panel card2 = new Panel();
        card2.add(new Label("Card 2"));

        frame.add(card1, "First");
        frame.add(card2, "Second");

        Button nextButton = new Button("Next");
        nextButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                cardLayout.next(frame);
            }
        });

        frame.add(nextButton, "South");
        frame.setSize(200, 100);
        frame.setVisible(true);
    }
}
```

5. GridBagLayout:
    - The most flexible layout manager, allowing precise component positioning and sizing.

```java
import java.awt.*;

public class GridBagLayoutExample {
    public static void main(String[] args) {
        Frame frame = new Frame("GridBagLayout Example");
        GridBagLayout layout = new GridBagLayout();
        frame.setLayout(layout);
        GridBagConstraints gbc = new GridBagConstraints();

        gbc.fill = GridBagConstraints.HORIZONTAL;
        gbc.gridx = 0;
        gbc.gridy = 0;
        frame.add(new Button("Button 1"), gbc);

        gbc.gridx = 1;
        gbc.gridy = 0;
        frame.add(new Button("Button 2"), gbc);

        gbc.gridx = 0;
        gbc.gridy = 1;
        gbc.gridwidth = 2;
        frame.add(new Button("Button 3"), gbc);

        frame.setSize(300, 200);
        frame.setVisible(true);
    }
}
```

These examples demonstrate how different layout managers arrange components within a container. Each layout manager has its own strengths and is suitable for different types of user interfaces. The choice of layout manager depends on the specific requirements of your application's GUI.