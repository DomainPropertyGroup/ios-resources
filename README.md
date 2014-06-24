![](https://avatars3.githubusercontent.com/u/7484540?s=140)


Domain Objective-C styleguide
===============

Brace style
---------------------

>Egyptian braces are to be used

### Incorrect

 ```objective-c
-(void)myMethodName
{

  if (myCondition)
  {
    
  }
}
 ```

###Correct

 ```objective-c
-(void)myMethodName{

  if (myCondition){
    
  }
}
 ```

* * *

>Else and If Else statements follow on the same line as the previous statement's closing brace.

### Incorrect

 ```objective-c
if (myCondition) {

}
else if (myOtherCondition) {

}
else {

}
 ```

###Correct

 ```objective-c
if (myCondition) {

} else if (myOtherCondition) {

} else {

}
 ```

Assignment alignment
---------------------

>Align all assignment operators if possible.

###Incorrect

 ```objective-c
myObjectWithLongName = 16
myVarWithShortName = anotherObject
superShort = @"wicked"
 ```
 
###Correct

 ```objective-c
myObjectWithLongName   = 16
myVarWithShortName     = anotherObject
superShort             = @"wicked"
 ```
 
Tabs or spaces
---------------------

>Always use the Xcode default of 4 spaces.

Method naming
---------------------

>Avoid "and" or “with” for multiple method parameters.

###Incorrect

 ```objective-c
[self goDoSomethingWithThing:myThing andStuff:myStuff];
 ```
 
###Correct

 ```objective-c
[self goDoSomethingWithThing:myThing stuff:myStuff];
 ```

* * *

>Make the word before the argument describe the argument.

###Incorrect

 ```objective-c
[self withThingDoSomething:myThing andStuff:myStuff];
 ```
 
###Correct

 ```objective-c
[self goDoSomethingWithThing:myThing stuff:myStuff];
 ```
 
* * *

>Setters set, getters don’t get.

###Incorrect

 ```objective-c
-(void)size:(CGSize)size;
-(CGSize)getSize;
 ```
 
###Correct

 ```objective-c
-(void)setSize:(CGSize)size;
-(CGSize)size;
 ```
* * *

>Boolean naming should contain "can", "will", "should" or "is”.

###Incorrect

 ```objective-c
-(BOOL)doesDisplay;
  ```
 
###Correct

 ```objective-c
-(BOOL)canDisplay;
-(BOOL)willDisplay;
-(BOOL)shouldDisplay;
-(BOOL)isDisplaying;
 ```
 
* * *

>Acronyms are capitalized (not just methods). "Id" is not an acronym.

###Incorrect

 ```objective-c
-(void)makeRequestWithUrl;
  ```
 
###Correct

 ```objective-c
-(void)makeRequestWithURL;
 ```
 
iVars and properties
---------------------

>
<ul>
<li>Private iVars belong in a blank category in the implementation file NOT the header. 
<li>Protected iVars belong in the header with @protected keyword. (so it doesn’t look like private iVars placed incorectly)
<li>Use protected iVars for subclass use. NOT properties.
</ul>

* * *

>Use a leading underscore for all iVars

###Incorrect

 ```objective-c
UIView* myView;
  ```
 
###Correct

 ```objective-c
UIView* _myView;
 ```

* * *

>Access properties by iVar backer in implementation file. The dot accessor is for external use only.

###Incorrect

 ```objective-c
self.myView = [[UIView alloc] init];
  ```
 
###Correct

 ```objective-c
_myView = [[UIView alloc] init];
 ```

Enums
---------------------

>NS_ENUM should be used instead of enum.

###Incorrect

```objective-c
typedef enum {
    ExampleStyle_None,
    ExampleStyle_Short,
} ExampleStyle;
 ```
 
###Correct

```objective-c
typedef NS_ENUM(NSInteger, ExampleStyle) {
    ExampleStyle_None,
    ExampleStyle_Short,
};
 ```

* * *

>
<ul>
<li>Enums should be typed using typedef
<li>Each enum item name should be prefixed with the type name followed by an underscore
</ul>

###Incorrect

```objective-c
typedef NS_ENUM(NSInteger, CellHeight) {
    Default,
    Short,
    Tall,
};
 ```
 
###Correct

```objective-c
typedef NS_ENUM(NSInteger, CellHeight) {
    CellHeight_Default,
    CellHeight_Short,
    CellHeight_Tall,
};
 ```

Boolean comparisons
---------------------

>Don’t compare against YES or NO.

###Incorrect

 ```objective-c
if (myBOOL == YES)
if (myBOOL == NO)

  ```
 
###Correct

 ```objective-c
if (myBOOL)
if (!myBOOL)
 ```

Dot notation
---------------------

>Dot notation is to be used at all available opportunities unless explicitly frowned-upon by this styleguide.

Import/Include
---------------------

>
<li>Import Objective-C
<li>Include C/C++


Golden Trails
---------------------

>Fail early instead of forcing an obscure trail of logic.

###Incorrect

 ```objective-c
if (condition1){
        if (condition2){
            if (condition3){
                //only logic
            }
        }
    }
  ```
 
###Correct

 ```objective-c
if (!condition1) return;
 ```
 
 
NSError handling
---------------------

>Any method that takes an NSError by reference should also return a Boolean. Evaluate the error if the method returned false.

###Incorrect

 ```objective-c
NSError *error;
[self trySomethingWithError:&error];
if (error) {
    // Handle Error
}

  ```
 
###Correct

 ```objective-c
NSError *error;
if (![self trySomethingWithError:&error]) {
    // Handle Error
}

 ``` 

Blocks
---------------------

>Type your blocks whenever possible.

###Incorrect

 ```objective-c
- (void)someMethodThatTakesABlock:(returnType (^)(parameterTypes))myBlockParamName {...}
  ```
 
###Correct

 ```objective-c
typedef returnType (^myBlockTypeName)(parameterTypes);
- (void)someMethodThatTakesABlock:(myBlockTypeName)myBlockParamName;
 ``` 

Methods requiring a super call
---------------------

>Always mark the method with the required super attribute.

###Incorrect

 ```objective-c
- (void)someMethodThatBreaksIfSuperIsNotCalled;
  ```
 
###Correct

 ```objective-c
- (void)someMethodThatBreaksIfSuperIsNotCalled __attribute__((objc_requires_super));
 ``` 

Deprecating Methods
---------------------

>Always mark the method with the deprecated attribute or a deprecation method.

###Incorrect

 ```objective-c
- (void)someDeprecatedMethod;
  ```
 
###Correct

 ```objective-c
- (void)someDeprecatedMethod __attribute__((deprecated));
 ``` 

Custom constructor
---------------------

>Always use instancetype, not id, as the return type.

###Incorrect

 ```objective-c
- (id)init;
 ```
 
###Correct

 ```objective-c
- (instancetype)init;
 ``` 

Literals
---------------------

>Always use literals.

###Incorrect

 ```objective-c
[myArray objectAtIndex:4];
  ```
 
###Correct

 ```objective-c
myArray[4];
 ``` 
Array first and last object
---------------------

>Always use firstObject / lastObject to avoid out of bounds for an empty array.

###Incorrect

 ```objective-c
myArray[0]
  ```
 
###Correct

 ```objective-c
[myArray firstObject]
 ``` 
 
constants
---------------------

>Always use a leading 'k' in your constant variable name.

###Incorrect

 ```objective-c
static const NSInteger myAwesomeConstant = 17;
  ```
 
###Correct

 ```objective-c
static const NSInteger kMyAwesomeConstant = 17;
 ``` 
 
Ternary operators
---------------------

>Wrap the conditional in parentheses and leave a space on either side of all operators.

###Incorrect

 ```objective-c
label.text = isAwesome? @"awesome": @"lame";
  ```
 
###Correct

 ```objective-c
label.text = (isAwesome) ? @"awesome" : @"lame";
 ``` 

> Use the short ternary operator to provide fallback values.

 ```objective-c
 label.text = possiblyAvailableContentString ?: defaultString;
 ```

Scalars
---------------------

>Don't use platform or bit-size specific scalars unless explicitly needed.

###Incorrect

 ```objective-c
int myInt      = 16;
float myFloat  = 1.0f;
  ```
 
###Correct

 ```objective-c
NSInteger myInt  = 16;
CGFloat myFloat  = 1.0f;
 ``` 
 
###Correct

 ```objective-c
UInt8 mySmallInt = 4; // I really need an 8-bit integer here for the following reasons...
 ``` 
 
The 'new' constructor
---------------------

>Do not use the new constructor.

###Incorrect

 ```objective-c
NSObject* myObject = [NSObject new];
  ```
 
###Correct

 ```objective-c
NSObject* myObject = [[NSObject alloc] init];
 ``` 
Class names
---------------------

>
<ul>
<li/>Use the correct design pattern use name in the class name. Do not use the word 'manager'.
<li/>Include the correct Domain prefix. If working on any other project include the brand/project prefix in the class name.
</ul>


###Incorrect

 ```objective-c
UserBehaviourManager
  ```
 
###Correct

 ```objective-c
DMUserBehaviourController
 ``` 

###Correct

 ```objective-c
DMABCUserBehaviourModel
 ``` 

Commenting
---------------------

>Use double leading asterisks for block comments. Block comments should be used to clarify the intent of a method.

###Incorrect

 ```objective-c
-(void)myMethod{
/* this method does ... */

}
  ```
 
###Correct
 
 ```objective-c
 /** this method does ... */ 
-(void)myMethod{

}
 ``` 

* * * 

>Use inline comments for clarifying the use of obscure methods/functions or to explain why you've used a non-standard technique. Inline comments should fall above their subject on their own line.

###Incorrect
 ```objective-c

// this method does ...
-(void)myMethod{
  [self doSomethingElse]; //go and do something else

}
  ```
 
###Correct

 ```objective-c
 
-(void)myMethod{
//normally technique A should be used here but 
//because of [reason] technique B must be used. 

//getting the square root of PI
sqrtf(M_PI);
}
 ``` 
 
* * * 

>Use pipes to identify symbols within a comment.


###Incorrect
 ```objective-c

-(void)myMethod{
  //myInt is used to calculate the meaning of life.
  NSInteger myInt = 42;
}
  ```

###Correct

 ```objective-c
 
-(void)myMethod{
  //|myInt| is used to calculate the meaning of life.
  NSInteger myInt = 42;
}
 ``` 

Delegate methods
---------------------

>When creating a component that uses delegation include a reference to that component through it’s delegate methods. Try to use the component name, excluding the prefix, at the start of each delegate method whenever possible. The component will be called “DMPickerView” for this example.

###Incorrect
 ```objective-c
 
-(void)didPressItemAtIndex:(NSUInteger)itemIndex;
 ``` 

###Correct
 ```objective-c
 
-(void)pickerView:(DMPickerView *)pickerView  didPressItemAtIndex:(NSUInteger)itemIndex;
 ``` 

* * *

>Delegate method names should contain "did", "should" or "will”.

###Incorrect

 ```objective-c
-(void)pickerMayStartBehaviour:(DMPickerView *)pickerView;
 ```
 
###Correct

 ```objective-c
-(void)pickerDidStartBehaviour:(DMPickerView *)pickerView;
 ```

Localizable strings key format
---------------------

> Localizable strings keys should provide usage context without using the value. 

###Incorrect

 ```objective-c
"CONTACT_TABLE_DISMISS_CONFIRM_BUTTON_TOTALLY" = "Totally"
 ```

###Incorrect

 ```objective-c
"CONTACT_TABLE_DISMISS_CONFIRM_BUTTON" = "Totally"
 ```

###Correct

 ```objective-c
"contact-table.dismiss-confirm-button" = "Totally"
 ```

Component thread safety
---------------------

>When creating components that use blocks or protocols that use multi-threading, always return them on the main thread **unless otherwise specified**. This is to ensure that the user of the component will always know what thread the blocks or protocols will return on (main) and to ensure that the component itself is responsible for it’s own thread management.

###Incorrect

 ```objective-c
-(void)myMethod {

dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{
        
        id data = [self someLargeCalculations];
        [_delegate myProtocolMethod:data];
    });
}

-(void)anotherMethod:(MyBlockType)myBlock {

dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{
        
	id data = [self someLargeCalculations];        
	myBlock(data);
    });
}
 ```

###Correct

 ```objective-c
-(void)myMethod {

dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{
        
        id data = [self someLargeCalculations];

        dispatch_async(dispatch_get_main_queue(), ^{
            
            [_delegate myProtocolMethod:data];
        });
    });
}

-(void)anotherMethod:(MyBlockType)myBlock {

dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{
        
	id data = [self someLargeCalculations];  

	    dispatch_async(dispatch_get_main_queue(), ^{      

	       	    myBlock(data);
	    });
    });
}
 ```
