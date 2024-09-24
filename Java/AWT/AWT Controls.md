### The AWT supports the following types of controls:

# Labels: 

* Labels are passive controls that do not support any interaction with the user.
* Constructors:
```java
Label( ) throws HeadlessException`
Label(String str) throws HeadlessException`
Label(String str, int how) throws HeadlessException
```
* Alignment constants: `Label.LEFT, Label.RIGHT, or Label.CENTER`
* Set or change the text:`void setText(String str)`
* `String getText( )`
* Set alignment: `void setAlignment(int how)`
* `int getAlignment( )`
# Push buttons

* A push button is a component that contains a label and that generates an event when it is pressed.
* Constructors:
```java
Button( ) throws HeadlessException
Button(String str) throws HeadlessException
```
* `void setLabel(String str)`
* `String getLabel( )`

```java
public class className implements ActionListener {
	// create buttons ...
	buttonRef.addActionListener(this);
	buttonRef2.addActionListener((ae) -> {
		// action to be performed ...
	});
	public void actionPerformed(ActionEvent ae) {
		// action to be performed ...
	}
}
```

* `getActionCommand( ) `
* `setActionCommand( )
* `getSource( ) `

# Check boxes

* A check box is a control that is used to turn an option on or off.
* Constructors:
```java
Checkbox( ) throws HeadlessException
Checkbox(String str) throws HeadlessException
Checkbox(String str, boolean on) throws HeadlessException
Checkbox(String str, boolean on, CheckboxGroup cbGroup) throws HeadlessException
Checkbox(String str, CheckboxGroup cbGroup, boolean on) throws HeadlessException
```
* Methods:
```java
boolean getState( )
void setState(boolean on)
String getLabel( )
void setLabel(String str)
```

```java
public class CheckboxDemo implements ItemListener {
	...
	checkboxRef.addItemListener(this);
	
	public void itemStateChanged(ItemEvent ie) {
		// handle the state change ...
	}
}
```

## Checkbox Group

`CheckboxGroup cbg = new CheckboxGroup();`

Methods:
```java
Checkbox getSelectedCheckbox( )
void setSelectedCheckbox(Checkbox which)
```

# Choice Controls

* The Choice class is used to create a pop-up list of items from which the user may choose.

`Choice choice = new Choice();`

Methods:
```java
void add(String name)
String getSelectedItem( )
int getSelectedIndex( )
int getItemCount( )
void select(int index)
void select(String name)
String getItem(int index)
```

```
```java
public class ChoiceDemo implements ItemListener {
	Choice choice = new Choice();
	...
	choice.itemListener(this);
	public void itemStateChanged(ItemEvent ie) {
		// action for the state change ...
	}
} 
```

# Lists




•	 Scroll bars
•	 Text Editing