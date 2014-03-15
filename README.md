Nutrition Facts
=================

Static factories and constructors share a limitation: they do not scale well to large numbers of optional parameters. Consider the case of a class representing the Nutrition Facts label that appears on packaged foods. These labels have a few required fields—serving size, servings per container, and calories per serving— and over twenty optional fields—total fat, saturated fat, trans fat, cholesterol, sodium, and so on. Most products have nonzero values for only a few of these optional fields.
What sort of constructors or static factories should you write for such a class?

1. **Telescoping constructor pattern**: provide a constructor with only the required parameters, another with a single optional parameter, a third with two optional parameters, and so on, culmi- nating in a constructor with all the optional parameters;
2. **JavaBeans pattern**: provide a parameterless constructor to create the object and then call setter methods to set each required parameter and each optional parameter of interest;
3. **Builder pattern [Gamma95, p. 97]**: provide a constructor (or static factory) with all of the required parameters that returns a builder object. Then the client calls setter-like methods on the builder object to set each optional parameter of interest. Finally, the client calls a parame- terless build method to generate the object, which is immutable.


## Problems with each one?

1. **the telescoping constructor pattern works**, but it is **hard to write** client code when there are many parameters, and **harder still to read it**. The reader is **left wondering what all those values mean** and must carefully count parameters to find out. Long sequences of identically typed parameters can cause subtle bugs.



