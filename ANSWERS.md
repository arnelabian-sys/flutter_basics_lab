GitHub repository link

Last three build() called lines (Activity 2):
build() called: 4 glasses build() called: 5 glasses build() called: 6 glasses

Observations
Activity 2: setState Experiment
I removed setState() from _addGlass(), leaving only if (_glasses < _goal) _glasses++;, and tapped the + button several times. The number on the screen stayed the same, and the progress bar did not move. This happened because _glasses changed in memory, but without setState(), Flutter was not notified to update the UI. When I added setState() back, the number and progress bar updated normally after every tap.

Activity 3: Expanded Experiment
When I removed Expanded from the Wind StatBox, its width became based on its content, while the other boxes still shared the remaining space. As a result, the boxes were no longer equal in width. Expanded allows a widget to fill its share of the available space in a Row or Column.

Activity 4: crossAxisCount Experiment
I changed crossAxisCount from 2 to 3. The grid displayed three cards per row, and each card became narrower. I changed it back to 2 afterward. This happens because crossAxisCount determines the number of columns in the grid.

Activity 5: buildTheme Experiment
I changed the ElevatedButton corner radius in buildTheme() from 8 to 20. The buttons became more rounded. Since the style is defined in the theme, the change applies to the ElevatedButtons that use the theme's default style.

Review Questions Answers
1.What is the difference between a StatelessWidget and a StatefulWidget? Give one example of each from this lab.
A StatelessWidget does not manage changing state, while a StatefulWidget can manage data that changes while the app is running. An example of a StatelessWidget is the ProfileCard in Activity 1. An example of a StatefulWidget is the WaterTrackerPage in Activity 2 because it updates the number of glasses.

2.Why is a StatefulWidget written as two classes? What does each class do?
A StatefulWidget uses two classes to separate the widget configuration from its changing state. The first class creates the State object, while the second class stores changing data, handles updates using setState(), and builds the UI.

3.In Activity 2, what happened when you changed _glasses outside setState()? Why?
The number on the screen did not update even though _glasses changed in memory. This happened because Flutter was not notified to rebuild the UI. When I used setState(), the screen updated normally.

4.Looking at the Debug Console in Activity 2, when is build() called?
The build() method is called when the screen is first displayed and whenever setState() triggers a rebuild. Each time I press the + or − button, the UI updates if the value changes. Pressing Reset also triggers a rebuild.

5.Explain the main axis and the cross axis of a Row and of a Column.
In a Row, the main axis goes horizontally from left to right, while the cross axis goes vertically. In a Column, the main axis goes vertically, while the cross axis goes horizontally.

6.In Activity 3, what happened when you removed Expanded from a StatBox? What does Expanded do?
When I removed Expanded from the Wind StatBox, its width became based on its content, so the boxes were no longer equal in width. Expanded allows a widget to occupy its share of the available space in a Row or Column.

7.Why do we use GridView.builder for the menu instead of a Column with many children?
We use GridView.builder because it displays items in a grid and supports scrolling. It can build items as they are needed, which is useful for large lists. A Column displays children vertically and does not scroll by itself.

8.How do Stack and Positioned create the Best seller badge in Activity 4?
Stack allows widgets to overlap each other. Positioned controls where the Best seller badge appears inside the menu card, such as near the top-left corner.

9.What is the difference between customizing with ThemeData and with a style on one widget? Give one example of each from Activity 5.
ThemeData sets the general appearance of the app, while a style on one widget changes only that specific widget. In Activity 5, buildTheme() changes the default ElevatedButton corner radius to 20. A TextStyle applied to one Text widget can change only that text's font size or weight.

10.When you flip the dark-mode switch in Activity 5, which widget holds the state, and how does the change reach MaterialApp?
The _ThemeDemoAppState class holds the _isDark variable. When I flip the switch, the callback calls setState(). This rebuilds ThemeDemoApp and updates MaterialApp's themeMode, changing the app between light and dark mode.