# Cookbook

<!-- 7.1 Create an Aras Innovator Object -->

## Create an Aras Innovator Object

```javascript
var myInnovator = new Innovator();
var myInnovator = this.getInnovator();
```

```csharp
Innovator myInnovator = this.getInnovator();
```

```vb
Dim myInnovator As Innovator = Me.getInnovator()
```

> Result: A new Innovator object

You need an Innovator Object to return a newResult() or newError() Item.

### Technique

There are basically two ways to create a new Innovator object; by getting the Innovator from the Item object or (only in JavaScript) calling the Class constructor.


<!-- 7.2 Create an Item Object -->

## Create an Item Object

```javascript
var myItem = new Item();
var myItem = this.newItem(myType,myAction);
var myInnovator = this.getInnovator();
var myItem = myInnovator.newItem(myType,myAction);
var myResult = myInnovator.newResult(resultText);
var myError = myInnovator.newError(errorMessage);
```

```csharp
Item myItem = this.newItem(myType,myAction);

Innovator myInnovator = this.getInnovator();
Item myItem = myInnovator.newItem(myType,myAction);
Item myResult = myInnovator.newResult(resultText);
Item myError = myInnovator.newError(errorMessage);
```

```vb
Dim myItem As Item = Me.NewItem(myType,myAction)
Dim myInnovator As Innovator = Me.getInnovator()
Dim myItem As Item = myInnovator.NewItem(myType,myAction)
Dim myResult As Item = myInnovator.NewResult(resultText)
Dim myError As Item = myInnovator.NewError(errorMessage)
```

> Result: A new Item object

You need an Item Object to submit a query or to add an Item.

### Technique

There are basically two ways to create a new Item Object; by calling the factory methods on the Item object or Innovator object or (only in JavaScript) calling the Class constructor.

<!-- 7.3 Query for an Item -->

## Query for an Item

```javascript
// Option 1
var qryItem = this.newItem(myType,"get");
qryItem.setID(myId);
var results = qryItem.apply();

// Option 2
var myInnovator = this.getInnovator();
var results = myInnovator.getItemById(myType, myId);
```

```csharp
// Option 1
Item qryItem = this.newItem(myType,"get");
qryItem.setID(myId);
Item results = qryItem.apply();

// Option 2
Innovator myInnovator = this.getInnovator();
Item results = myInnovator.getItemById(myType, myId);
```

```vb
' Option 1
Dim qryItem As Item = Me.NewItem(myType,"get")
qryItem.setID(myId)
Dim results As Item = qryItem.Apply()

' Option 2
Dim myInnovator As Innovator = Me.getInnovator()
Dim results As Item = myInnovator.GetItemById(myType, myId)
```

> Result: The queried Item object

You want to query for an Item that you know by id and type.

### Technique

There are a few ways to get an Item when you know its id and type, the simplest being the Innovator.getItemById() method. However, if you need to be granular about your request then building the query using the IOM is required. This provides the ability to include controls to limit the results and define the structure to be returned for the Items found.
