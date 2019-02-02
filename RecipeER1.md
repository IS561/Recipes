## All entities are understood to have titles and and descriptions expressed in text.

# Entity Classes

### Recipe
A step-wise procedure for producing a quantity of food from a group of
ingredients.

#### Recipe attributes
* Yield (Quantity).
* Number of servings (number)
* Serving size (quantity)
* Total time (temporal extent)
* Language

### Qualifying property 

A property required for a quantity of a food substance in order to
qualify for an ingredient Examples include "chopped," "sifted fine,"
and "sautéd to clear."  Since any ingredient may have more than one of
these, this can't be a simple attribute of an ingredient.

#### Attributes of a qualifying property
* Prerequisite (truth value). A prerequisite property is expected to
  obtain prior to the first step of the recipe through action by the
  cook (chopping, defrosting, etc.)
* Requirement (truth value). A requirement property distinguishes
  suitable from unsuitable food substances (fresh lemon juice as
  compared to bottled, kosher salt as compared to ordinary).

### Ingredient

A class of physical objects, each a like quantity of the same food
substance. Examples include "one bay leaf," "two teaspoons of
cornstarch," and ""three grams of salt." Instances of the class
"Ingredient" are themselves classes, since "one bay leadf" is not a
particular bay leaf, but whatever bay leaf is used during the
execution of a recipe.

#### Ingredient attributes
* Optional (truth value). This property obtains if the ingredient is
  optional.

### Quantity
A number with an optional unit of measurement, for example "2" or "2
teaspoons." Quantities are descriptions of magnitudes.  Units of
measurement are essential to the identity of what we'll call a
quantity, so that "1 teaspoon" is a different quantity than "4.92892
cc" even though they are the same magnitude.

#### Quantity attributes
* Type: discrete vs. continuous

### Food Substance 
A type of food or edible material that forms an ingredient or
completed recipe. Examples include "potato," "salt," "cornstarch," and
"chicken broth." Instances of this class are themselves classes.


### Step

A discrete ordered part of a repeatable process.  An example of a step
would be, "place chicken and next 11 ingredients in a 6-qt. slow
cooker. Cover and cook on LOW 6 hours or until chicken and vegetables
are tender and chicken separates from bone."

#### Attributes of a step

* First in sequence (truth value). This property obtains if the step
  is the first in a sequence of steps.
* Optional (truth value). This property obtains if the step is
  optional.

### Source
* A bibliographic description of an information resource.

#### Attributes of a source
* Content (text). The bibliographic description expressed as text.
* Notation (text). The notation in which the description is expressed.

### Tool
A physical object that participates in a step or causes a qualifying
property to obtain. Examples include "saucepan," "paring knife,"
"grater."

# Relationships

### Requires
* **Scope note:** participation of an ingredient in a recipe.
* Domain: Recipe
* Codomain: Ingredient
* Arity: 2 (binary relationship)
* Cardinality: many-to-many
* Remarks: Consider recording the nutritional content of an ingredient; it will be easier to keep consistent if each "ingredient" is characterized once. Assuming the nutritional details are consistent across recipes, many-to-many is the more appropriate cardinality.

### Includes
* **Scope note:** participation of a step in a recipe.
* Domain: Recipe
* Codomain: Step
* Arity: 2
* Cardinality: many-to-many
* Remarks: Some steps will recur in many recipes.

### Has Quantity
* **Scope note:** The amount of a substance constituting an ingredient.
* Domain: Ingredient
* Codomain: Quantity
* Arity: 2
* Cardinality: many-to-1

### Has Constituent
* **Scope note:** the food substance constituting the ingredient
* Domain: Ingredient
* Codomain: Food substance
* Arity: 2
* Cardinality: many-to-1

### Directly follows
* **Scope note:** a temporal relationship between a step and the step that immediately follows it
* Domain: Step
* Codomain: Step
* Arity: 2
* Cardinality: 1-to-1

### Has Substep
* **Scope note:** An ordered, functional feature of an activity. A piece of a larger step.
* Domain: Step
* Codomain: Step
* Arity: 2
* Cardinality 1-to-many
* Remarks: Some recipe steps are themselves sequences of smaller steps. In the meronymic classification of Winston, Chaffin, and Herrmann (1987) this is an "activity/feature" relationship.

### Equal magnitude
* **Scope note:** equivalence relationship obtaining between quantities of equal magnitude
* Domain: Quantity
* Codomain: Quantity
* Arity: 2
* Cardinality: many-to-many
* Remarks: For example, 1 US teaspoon equals 4.92892 ml.

### Equal or greater magnitude
* **Scope note:** relationship obtaining between commensurable quantities where one has a greater or equal magnitude. 
* Domain: Quantity
* Codomain: Quantity
* Arity: 2
* Cardinality: many-to-many
* Remarks: Domain and codomain are quantity, not amounts of a particular substance, so participants must be commensurable even if the measurement units are different. For example, "five cups is greater than or equal to one teaspoon." But not "2 pounds of salt is greater than or equal to 2 teaspoons of salt."

### Equal or greater amount
* **Scope note:** an asymmetric relationship between ingredients constituted of the same substance, without the requirement for commensurable quantities or magnitudes.
* Domain: Ingredient
* Codomain: Ingredient
* Arity: 2
* Cardinality: many-to-many
* Remarks: Domain and codomain are ingredient, not quantity. For example, "2 pounds of salt is an equal or greater amount than 2 teaspoons of salt," but not "Five cups is an equal or greater amount than 2 teaspoons."

### Has source
* **Scope note:** An attribution of the source of some recipe or other information.
* Domain: Recipe
* Codomain: Source
* Arity: 2
* Cardinality: many-to-many
* Remarks: More properly, the domain should be a superclass like "information resource," but we're not including upper level classes in this list.

### Uses tool
* **Scope note:** The relationship obtaining between a step in a recipe and a tool employed during that step.
* Domain: Step
* Codomain: Tool
* Arity: 2
* Cardinality: many-to-many

### Realizes property
* **Scope note:** An instrumental relationship obtaining between a tool and a qualifying property realized through the use of the tool.
* Domain: Tool
* Codomain: Qualifying property
* Arity: 2
* Cardinality: many-to-many
* Remarks: For example, a grater is used for grating, and can cause something to be grated.

