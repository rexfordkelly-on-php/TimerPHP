Introduction
===

Simple class for logging time and memory usage of methods and such.

The `Timer::__toString()` method will create a simple plain text overview,
but you can of course also create your own output by using the properties 
of the Timer objects directly.

Example usage
---

Here is some sample output from the `sample/add.php` script in this repo.

    /TimerPHP/sample/add.php(3, 9)
     │ 
     │ 7.001 s
     │ 4.02 KiB, 732.41 KiB
     │ 
     ├ SlowMath::slowAdd(3, 9)
     │  │ 
     │  │ 4.001 s
     │  │ 432.00 B, 732.41 KiB
     │ ─┘ 
     │ 
     ├ test(null, true, false)
     │  │ 
     │  │ 2.000 s
     │  │ 176.00 B, 732.41 KiB
     │ ─┘ 

If you want to see some actual usage of this class, you can check out my project,
Svish/MyHymnal.


License
===

This work is licensed under the Creative Commons Attribution 3.0 Unported License. To view a copy of this license, visit [Creative Commons Attribution 3.0 Unported License](http://creativecommons.org/licenses/by/3.0/).

![Creative Commons License](http://i.creativecommons.org/l/by/3.0/88x31.png)
