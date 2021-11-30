# Find called classes with their paths

This code will extract all called classes in the page with their paths 
+ It will check too if they have __constructor method or not

```php 
foreach(get_declared_classes() as $class){
    $ref = new ReflectionClass($class);
    $hasConstruct = !empty($ref->hasMethod("__construct")) ? "<font color=green>Yes!!</font>" : "<font color=red>No</font>";
    $name = $ref->getFileName();
    if(!empty($name)){
        echo "$class | ($hasConstruct) | $name<br><br>";
    }
}
```


