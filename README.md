# php-enum
Fork of myclabs/php-enum that changes the logic of __toString method so it shows by default the name of the constant that defined the enum. 
The only difference is that this fork of php-enum shows key (name of the const) in __toString method since from my point of view enums are used to abstract the actual value. The implementing class should overwrite __toString if it wishes to show the value or some other information. 


## Documentation

See documentation in [original php-enum](https://github.com/myclabs/php-enum/blob/master/README.md). (Or download it from there if you don't mind about __toString).
