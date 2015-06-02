# php-enum:

My version of php-enum, the Enum implementation inspired from SplEnum.

This is the same php-enum that you can get from: [MyCLabs/php-enum](https://github.com/myclabs/php-enum). I only changed the functionality of __toString() to return the key, since in my opinion the enum should no represent a value directly but just to be an abstraction that represents something specified by the key (inspired by Java enum). I you don't care about this, I recommend you to use the original one.

Now, the original description from [MyCLabs](https://github.com/myclabs):

## Why?

First, and mainly, `SplEnum` is not integrated to PHP, you have to install it separately.

Using an enum instead of class constants provides the following advantages:

- You can type-hint: `function setAction(Action $action) {`
- You can enrich the enum with methods (e.g. `format`, `parse`, …)
- You can extend the enum to add new values (make your enum `final` to prevent it)
- You can get a list of all the possible values (see below)

This Enum class is not intended to replace class constants, but only to be used when it makes sense.


## Declaration

```php
use MyCLabs\Enum\Enum;

/**
 * Action enum
 */
class Action extends Enum
{
    const VIEW = 'view';
    const EDIT = 'edit';
}
```


## Usage

```php
$action = new Action(Action::VIEW);

// or
$action = Action::VIEW();
```

As you can see, static methods are automatically implemented to provide quick access to an enum value.

One advantage over using class constants is to be able to type-hint enum values:

```php
function setAction(Action $action) {
    // ...
}
```

## Documentation

- `__construct()` The constructor checks that the value exist in the enum
- `__toString()` You can `echo $myValue`, it will display the the name of the constant
- `getValue()` Returns the current value of the enum
- `getKey()` Returns the key (name of the constant) of the current value on Enum

Static methods:

- `toArray()` method Returns all possible values as an array (constant name in key, constant value in value)
- `keys()` Returns the names (keys) of all constants in the Enum class
- `values()` Returns instances of the Enum class of all Enum constants (constant name in key, Enum instance in value)
- `isValid()` Check if tested value is valid on enum set
- `isValidKey()` Check if tested key is valid on enum set
- `search()` Return key for searched value

### Static methods

```php
class Action extends Enum
{
    const VIEW = 'view';
    const EDIT = 'edit';
}

// Static method:
$action = Action::VIEW();
$action = Action::EDIT();
```

Static method helpers are implemented using [`__callStatic()`](http://www.php.net/manual/en/language.oop5.overloading.php#object.callstatic).

If you care about IDE autocompletion, you can either implement the static methods yourself:

```php
class Action extends Enum
{
    const VIEW = 'view';

    /**
     * @return Action
     */
    public static function VIEW() {
        return new Action(self::VIEW);
    }
}
```

or you can use phpdoc (this is supported in PhpStorm for example):

```php
/**
 * @method static Action VIEW()
 * @method static Action EDIT()
 */
class Action extends Enum
{
    const VIEW = 'view';
    const EDIT = 'edit';
}
```
