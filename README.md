# php-enum
Fork of myclabs/php-enum that changes the logic of __toString method so it hides by default the value of the enum.

## Documentation

See documentation in [original php-enum](https://github.com/myclabs/php-enum/blob/master/README.md).
The only difference is that this fork of php-enum shows key (name of the const) in __toString method since from my point of view enums are used to hide the actual value. The implementing class should overwrite __toString if it wishes to show the value or some other information. 
