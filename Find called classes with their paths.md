# Find called classes with their paths

This code will extract all called classes in the page with their paths 
+ It will check too if they have __constructor method or not

```php 
// Start div tag with some style
echo("<div style='background-color: white; color: black;'><h1 style='margin-bottom: 7px;'>Called classes with constructs</h1>");
// Get all declared classes and and do foreach loop 
foreach(get_declared_classes() as $class){
    // Call the reflection class to get more information
    $ref = new ReflectionClass($class);
    // Does the class has constructor ?
    $hasConstruct = !empty($ref->hasMethod("__construct")) ? "<font color=green>Yes</font>" : "<font color=red>No</font>";
    // Get the path of the class
    $path = $ref->getFileName();
    // If the path is not empty
    if(!empty($path)){
        // Print the class name + does has consturctor? + path
        echo "$class - $hasConstruct - $path<br><br>";
    }
}
// Close the tag
echo("</div>");
```


